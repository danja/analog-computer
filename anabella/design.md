# Analog Computer

The goal here is to build a machine comparable to the basic [analog computers](https://en.wikipedia.org/wiki/Analog_computer) used (occasionally) in education, which in turn are modeled on those developed historically for solving equations.

There's a certain irony that these machines are generally considered obsolete, if not entirely forgotten, yet virtually all of the electronic devices we use every day contain analog computing elements.

The big difference is that the circuits used in eg. a mobile phone to interface with sensors like microphones and cameras are purpose-specific. Traditional analog computers are more general-purpose.

An analog circuit developer will very likely at some point in a project prototype on a breadboard using loose components that correspond directly with those of analog computers : resistors, capacitors and most notably operational amplifiers (which come straight from the world of analog computers, for carrying out mathematical operations). But the level of granularity and user interface are somewhat different.  

The modules of an analog computer relate more directly to mathematical operations such as addition, multiplication and integration. While it is possible to simulate these numerically in a digital computer, there is a qualitative difference. I suspect there may be insights offered by the analog paradigm that are obscured by looking at things through a digital lens.
It's worth remembering that the physical world, at human scales, is essentially an analog system - well, the word 'analog' has been retroactively applied to mean something that is continuous rather than discrete. Originally it refers to one system that behaves in a similar, analogous manner to another.  

### Requirements

I'd like enough functionality to be able to model some 'standard' systems:

* [Damped Mass on Spring](https://en.wikipedia.org/wiki/Mass-spring-damper_model)
* [Bouncing Ball](https://en.wikipedia.org/wiki/Bouncing_ball) (in a box..?)
* [Lorenz System](https://en.wikipedia.org/wiki/Lorenz_system)
* 3-cell [Cellular Neural Network](https://en.wikipedia.org/wiki/Cellular_neural_network)
* [Lotka-Volterra Predator-Prey](https://en.wikipedia.org/wiki/Lotka%E2%80%93Volterra_equations)

Metering with be done externally. (maybe a later unit containing meter + speaker + Arduino-based 'scope). It should be worthwhile allowing for some level of external control (ie. for resetting the integrators) to allow an Arduino or whatever to interface, making a hybrid computer.

My plan is to use an A4 plate as the front panel, which gives a nice physical limit on what is possible. This form-factor I believe should also work as a good alternative to finer-grained modular setups such as those based on Euroracks. Connectors will be 2mm banana plugs/sockets.

Standard analog chips will be used inside (probably mostly TL072 op amps), powered at +/- 15v, using +/- 10v as the value range.

I'm not aiming for high precision, but may have a bit of trimming for things like offset on the pots. etc. Using typical inexpensive components such as 1% metal film resistors, that 1% seems a reasonable target (capacitor tolerance will be the weakest link, though hopefully hand-selecting individual components will minimise error here).

## Proposed Functionality

### Control Unit

* Power switch & LED
* Overload indicator
* Mode switch : Initial Conditions/Run/Halt

*TBD: external control of the mode would be desirable*

### Modules

| Component    | Quantity | Control  | Inputs | Outputs | Tot. I+O |
| ------------ | -------- | -------- | ------ | ------- | -------- |
| Voltage Ref. | 4        | -        | -      | 4       | 4        |
| Coefficients | 6        | pot      | 1      | 1       | 12       |
| Free pots    | 2        | pot      | 3      | -       | 6        |
| Summers      | 4        | -        | 4      | 2       | 24       |
| Inverters    | 4        | -        | 1      | 2       | 12       |
| Integrators  | 4        | Switch   | 3      | 2       | 24       |
| Multipliers  | 2        | -        | 3      | 2       | 10       |
| Log          | 1        | -        | 1      | 1       | 2        |
| Exp          | 1        | -        | 1      | 1       | 2        |

(96 connectors there...maybe 12x8 = 96 available)

## Voltage Reference

2 x 10v
2 x 1v

## Coefficients

6 x potentiometers with one terminal grounded, feeding unity gain buffers

## Free pots

2 x pots, all terminals exposed

## Summers

4 x op amps in **inverting** configuration

* 3 x1 inputs
* 1 x10 input
* 2 outputs

### Design Considerations & Implementation

The first question here was whether to use inverting or non-inverting configurations. There are two problems with the non-inverting setup, first is that the gain calculation is a little more complicated (not really an issue), second there is interaction between different inputs. The usual inverting setup has the input resistors connected to the (-) op amp input, which is forced by the feedback to stick at virtual ground, thus removing interaction. The drawbacks of using the usual inverting setup are that the input impedance will be much lower, and that - well, they are inverting. But the input impedance will typically be much greater than the output impedance from which the units are fed, so this shouldn't be an problem in practice. The overhead of providing a -1 inverter per summer is low and alleviates the other problem

Many historic analog computers expose pretty much the whole of the op amp. In particular, those using an inverting configuration allow access to the virtual ground point allowing arbitrary feedback components. Here, to keep things simple, this won't be the case. Instead, the straightforward summer model will be used.

Checking the TL07x datasheet and breadboarding, the simple inverting configuration appears to be perfectly adequate given the overall accuracy goal of around 1%. A feedback resistor of 100k, input resistors of 3 x 100k & 1 x 10k seems fine.

## Inverters

4 x unity gain op amp inverters (ie. -1), 1 input, 1 output

Like the summers, a 100k input & 100k feedback resistor should be ok.

## Integrators

4 x op amps in **inverting** configuration, with switched capacitor for time constant.

**TBD**

To allow simultaneous response and the potential for external control, electronic switching of the integrators is desirable.

Common (inexpensive) analog switch ICs won't support the +/- 15v range. The plan here is to experiment with discrete FET-based switches.  

A fallback here is to use electromechanical relays or possibly pair the indegrators, each pair having a DPDT, ON-OFF-ON switch for Initial Conditions - Hold - Run. Because of timing issues, this is a last resort.

## Multipliers

**TBD**

The easiest solution here is to use dedicated multiplier chips - maybe 2 x AD633. These are quite expensive.
Less expensive, but potentially just as good are circuits based around the LM13700 (dual) transconductance op-amp.
Breadboard experimentation needed here.

## Log/Exp

Log & antilog circuits can be quite straightforward, but there is a particular practical issue to consider - log(x) where x<0 is undefined (complex logs are beyond scope here).

# Analog Computer : Annabella

The basic goal is to build a machine comparable to the basic analog computers used (occasionally) in education, with enough functionality to be able to model some 'standard' systems:

* damped mass on spring
* bouncing ball in a box
* Lorenz Attractor

Metering with be done externally. (maybe a later unit containing meter + speaker + Arduino-based 'scope).

My plan is to use an A4 plate as the front panel, which gives a nice physical limit on what is possible. This form-factor I believe should also work as a good alternative to finer-grained modular setups such as those based on Euroracks. Connectors will be 2mm banana plugs/sockets. 

Standard analog chips will be used inside, powered at +/- 15v, using +/- 10v as the value range.

## Proposed Functionality

### Control Unit

* Power switch & LED
* Set initial conditions
* Run
* ...

### Modules

| Component    | Quantity | Controls | Inputs | Outputs |
| ------------ | -------- | -------- | ------ | ------- |
| Voltage Ref. | 8        | -        | -      | 8       |
| Coefficients | 6        | 6 x pots | 6      | 6       |
| Free pots    | 2        | 2 x pots | 6      | -       |
| Summers      | 4        | -        | 16     | 8       |
| Inverters    | 4        | -        | 4      | 8       |
| Integrators  | 4        | 4 x SW   | 12     | 8       |
| Multipliers  | 2        | -        | 3      | 4       |

(89 connectors there...maybe 12x8 = 96 available)

#### TBD

* log
* exp
* comparator(s)
* rectifiers(s)
* function generators(s) (transfer function)
* function generator (sig. gen.)
* clock

## Voltage Reference

4 x 10v
4 x 1v

## Coefficients

6 x potentiometers with one terminal grounded, feeding unity gain buffers

## Free pots 

2 x pots, all terminals exposed

## Summers

4 x op amps in **inverting** configuration

* 3 x1 inputs
* 1 x10 input
* 2 outputs

*TBD Should the virtual ground point be exposed?*

## Inverters 

4 x unity gain op amp inverters, 1 input, 1 output

## Integrators

4 x op amps in **inverting** configuration, with switched capacitor for time constant, with analog switches handling initial conditions/run

## Multipliers 

2 x AD633 











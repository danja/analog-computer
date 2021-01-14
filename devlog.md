# Development Log

**2021-01-14** My birthday!

Blog post: https://dannyayers.wordpress.com/2021/01/14/synchronearlicity/

**2021-01-09**

I'm typing this in the dark, power outage.
After posting a fairly random blog post [link later] I mailed Bernd [details to follow].
He gave me some great pointers regarding analogue computer hardware. I'd just copied them out of emails when power went off:
[[
I would suggest to use electronic analog switches
such as the ADG441 etc. for your integrator control. These are not too
expensive and work well with a +/-15 V power supply. We use these, too, in
our Model-1 analog computer.

 Regarding multipliers: For most applications an AD663 is sufficient and
costs about 10 EUR/piece. If you need implicit functions such as square root
or division, I would suggest using an AD734 which is pretty expensive but has
great stability and is explicitly well suited for implicit function
generation.

Regarding capacitors: Precision is not the problem, just find some good
matching capacitors. The problem is dielectric absorption. You want
capacitors with polypropylene or Teflon dielectric, nothing else, in your
integrators! The smaller the dielectric absorption of a dielectric is, the
better suited is that capacitor for an integrator. I suggest buying some WIMA
PP capacitors, such as 4.7 uF, or 470 nF or the like - get about 10 or 20 of
each value and then find good matching capacitors. The absolute value of the
integrator time scale factor is not as important as the requirement that all
integrators have the same time scale factor when set to 1, 10 etc.
]]

**2020-12-31** New Year's Eve (just another day at Mozzanella Polytechnic)

The other day an astronomer on YouTube I follow was talking about chaos in the the motion of the planets. I did a blog post - [A Quick Way to Visit the Stars](https://dannyayers.wordpress.com/2020/12/29/a-quick-way-to-visit-the-stars/). But this also prompted me to look at a bit more chaos theory.

One of the simplest systems for generating chaotic activity is Chua's Circuit. I found an excellent (if rather confusingly organised) site about this : http://www.chuacircuits.com/ It features an nice straightforward op amp-based implementation.
But how do you frame this in terms of an analog computer? Soon found a great little paper : [Simplest ODE Equivalents of Chua’s Equations](https://people.eecs.berkeley.edu/~chua/papers/Pospisil00.pdf) (PDF). It can be done using 3 summers, 3 integrators and one nonlinear component, the 'Chua Diode'. This is an odd little thing, it's a function with a couple of kinks. Very simple to make with op amps.
But from what I can gather, the shape isn't particularly important, just as long as it is nonlinear - so I reckon it's probably doable using something like the log function I have planned for this machine.
I found it reminiscent of the [ReLU](https://machinelearningmastery.com/rectified-linear-activation-function-for-deep-learning-neural-networks/) activation function for neural nets. So naturally I next had a sniff around [The CNN Paradigm](http://nonlinear.eecs.berkeley.edu/raptor/CNNs/TheCNNParadigm.pdf) (PDF) by some guy called Chua. That's Cellular Neural Networks.




**2020-12-15** First post here.

To date I've been putting notes directly inside the [design doc](https://github.com/danja/analog-computer/blob/master/anabella/design.md). From now on, I'll put fine-grained notes here, making the design doc effectively a snapshot.

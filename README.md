# Analog Computer

I want to build an analog computer. [Design in progress](anabella/design.md).

This repo is in need of organization!

### Status

_More detailed notes can be found on the [DevLog](https://github.com/danja/analog-computer/blob/master/devlog.md)_

**2021-12-22** Double-Wow! Another year's gone by without me making any _visible_ progress on this thing. Most recent related development has been getting together test gear. That should make the breadboarding etc. go much faster - long term efficiency, innit. Should be able to get back to this in the next few weeks. (Similar goes for my [ELFQuake](https://elfquake.wordpress.com/) project).

Elsewhere, have got https://hyperdata.it live again with blog, bit-by-bit getting other projects live again there.

Prompted to visit here today because Derek of Veritasium has just produced a video on analog computers, [The Most Powerful Computers You've Never Heard Of](https://www.youtube.com/watch?v=IgF3OX8nT0w). Good stuff, historical background. (I would quibble on some of the things he says about analog vs. digital, but the general gist is fine). Another episode is promised talking about the relationship between analog computers and machine learning. As it happens, one of my motivations for starting this project was to play with designs for artificial neurons etc, so I'm looking forward to Derek's Pt.2.

As it happens, I've also been gearing myself up for putting out some videos on YouTube. I've played there many times already, but I need to tidy up my act... One of the first 'clean' vids I have planned is on electronic analog computer design. Here's an [old video](https://www.youtube.com/watch?v=OfPHS5UEFvQ) if you care to bookmark channel.

**2020-12-09**

Made some tweaks to design/front panel, decided it'd be a good idea to include a Summing Junction input on the summers.

Started a [links page](links.md).

**2020-12-08**
Wow, rather a long time since I last updated things here. Moderately good reason: about a year ago I realised I had too many projects on the go at the same time, so tried to focus on just one - [Chatterbox](https://github.com/danja/chatterbox).

But that isn't to say I've totally neglected this thing. Most visibly, I _may_ have accumulated all the components I'll need.

![Bits](https://github.com/danja/analog-computer/blob/master/images/bits.jpg?raw=true)

The front panel - which effectively determines the overall design under the hood - is getting towards the point where I can start that side of construction. The top half here is the patchbay, bottom half controls. I have 2mm sockets of 5 colours, trying to make the choices make some kind of sense.

![Front Panel](https://github.com/danja/analog-computer/blob/master/anabella/images/front-panel-blocks_2020-12-09.png?raw=true)

I've also done quite a lot of research into potential circuits. (See [references](anabella/reference)) My most immediate task there is to organise notes/docs around that. Then, I anticipate rather a lot of time on the breadboard.

**2018-09-25** overall [design](anabella/design.pdf) more or less worked out, started roughing out front panel. Now working through individual modules, breadboarding. Soon will order case and some connectors, make sure everything will fit.

2018-09-18 set up github repo, started typing up plans

### Motivation

- simulating seismic-like systems and play with signal conditioning to (hopefully) inform [ELFQuake](https://elfquake.wordpress.com/)
- for use in music synthesis (also I want to try out a particular semi-modular construction idea, something to use later on analog synth components)
- brush up my calculus
- general curiosity - in particular experimentation with hybridization, using an Arduino to interface with PC, put everything on the Web
- [chaos](http://www.analogmuseum.org/english/examples/lorenz_attractor/) is fun!

_This also looks like it might have potential for fun : [Mathematical modelling of infectious disease](https://en.wikipedia.org/wiki/Mathematical_modelling_of_infectious_disease). The SIR model uses 3 differential equations, should test my calculus at least._

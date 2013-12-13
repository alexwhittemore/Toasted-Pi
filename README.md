Thermostat
==========

Thermostat is a web interface for a Raspberry Pi based home thermostat.

Hardware
--------

Thermostat hardware consists of a Raspberry Pi, a DS18B20 OneWire temperature sensor, and a mains-rated 20A 5V relay, driven by a simple NPN transistor + base resistor (common emitter configuration) relay driver.

In reality, something designed for heating applications like an [Aube RC840](http://www.aubetech.com/products/list.php?noLangue=2&noFamille=3&app=20) would be best, but because I didn't measure twice (or, really, even once), I have an RC840T, rated for 240V. Turns out my heaters are 120. Whoops.

The connections are trivial: the relay (well, transistor base) is driven by GPIO0 on the RPi (pin 2 on my model B, adjust to taste), and the thermometer is read by GPIO4 using the now-included w1-gpio and w1-therm kernel modules. There's an LED in there somewhere too, I forget the pin. It's only for heating indication, anyway.

I should make a Fritzing schematic, shouldn't I? Consider it on the to-do list.

Software
--------
The temperature handling daemon and server are both written in Javascript/Node, for a couple of reasons: 1) I can, 2) I don't really know how to use node and want to learn, and 3) I already know python. You'd have thought 3 would be a strike against Node, but you'd be wrong.

I mean seriously, if I weren't doing this *specifically* to be hard on myself, I'd have just gotten a Nest.

Of course, saying that these components are written in JS/Node is sort of misleading, considering that at time of writing, they aren't written at all.

Burning your house down and/or zapping yourself into the next life
------------------------------------------------------------------

You're taking lots of risk playing with mains, much less 240v mains, much less high-current 240v mains. Lots of risk for which I have no intention of being held responsible. If you're not comfortable with this, go buy a Nest. Really, it's way better anyway.

Of course, if you don't have a stupid HV electric heating system like I do and you only need to play with 24VAC, that's much nicer.

Still, if you burn your house down, don't yell at me. Use appropriate gauge wires, wire nuts, etc. There are lots more ways to mess this up than you can think of, and I'm completely aware I've done a couple of them in my own implementation (I plan on using this system literally 4 days a year, this is Los Angeles. If I lived in Maine, I'd buy a Nest).

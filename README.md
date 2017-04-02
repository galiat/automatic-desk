# automatic-desk

## Overview
After wondering where all the Automatic desks, at Autodesk were, I slightly automated my existing desk. 
https://twitter.com/galiat/status/847876743109255168

## Materials Used
* the same kind of desk as in the Autodeks Boston office. 
  * (I have no idea the brand. I'll update this when I'm back in the office.)
* particle photon with headers ($20) https://store.particle.io/
* digital metal-gear micro servo (~$8)
* servo horn (should come w/ servo)
* small amount of 3/8th plywood (or something similar)
* 3 male to female wires (only need this if the servo wires aren’t broken out)
* scotch tape
* 4 [command strips](http://www.command.com/3M/en_US/command/products/~/Command-Mini-Refill-Strips?N=5924736+3294529207+3294737303&rt=rud)

## Set up the particle photon
1) Follow the excellent documentation on on particle.io to get your photon set up. Only go thru _Step 2: Connect with your smartphone_
https://docs.particle.io/guide/getting-started/intro/photon/

2) Plug you servo into the photon
Servo wires always have 3 color-coded wires

|  type  | color  | port |
| ------ | ------ | ---- |
| Signal | orange |  WKP |
| Power  | red    |  VIN |
| Ground | black  |  GND |

3) Load code to the photon - follow the documention https://docs.particle.io/guide/getting-started/build/photon/ up thru _Flashing Your First App_

4) Create a new app & copy this code in. You might want to adjust the `delay` depending on your height.
```js
Servo deskServo;

void setup()
{
  Particle.function("stand", stand);
  Particle.function("sit", sit);
  deskServo.attach(A7);  
  deskServo.write(90);
}

int sit(String _command)
{
  deskServo.write(40);
  delay(11000);
  deskServo.write(90);
  
  return 0;
}

int stand(String _command)
{
  deskServo.write(140);
  delay(11000);
  deskServo.write(90);

  return 0;
}

void loop(){}
```

5) Test it out. Hit sit & stand on the app. The servo should react.

## Mount it to your desk
1) I'll type this up later. But basiclly, I taped the servo horn to the paddle on the desk and then mounted whole thing to the side of the desk using commandstrips and plywood.

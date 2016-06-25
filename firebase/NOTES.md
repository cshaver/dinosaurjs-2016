# Firebase - Makes IoT Prototyping  Fun, *Jen Tong  - Google Cloud Platform Developer Advocate*

## @

### The Plan
- EE for Web Devs
- Recipe for IoT
- Live build & code
- Silly demos

### Bits & Volts

#### 0 Bit:
5v |  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|  
0v |============

#### 1 Bit:
5v |============  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|  
0v |  

#### Analog:
|~~~~~~~~~~~~~~~


#### PWM
Like a stair ladder
V^V^V^V^V^

**Raspberry Pi** has nodejs, memory systems, etc  
**Arduino Uno** for writing code right on the metal. not really an OS. has pins that interact with the outside world. exact timing

**Wires** are how we copy state from one place to another.  
**Breadboards** hold wires with a metal clip, attached in rows. Two long rails on the side used as reference 0 and reference 1 (voltage and ground). Great for putting things together on your desk.  
**Perfboard/protoboard** to solder stuff onto. Some look just like breadboards which make it very easy to transfer.  
**Buttons**
**Light-emitting diodes (LED)** - pins are slightly different lengths. Logic 1 on long pin and 0 on short pin it will light up, but not in any other config. (Only allows current in one direction)
**Resistors** are terrible, terrible wires. They do the same things that wires do, but badly. Read the stripe code to know how bad a wire they are.

### Components
- Kind of like Legos but sometimes they dance

## The Recipe:
For building *one* of something, focused on rapid development vs cost per unit

- Components
- Arduino Uno, formatta, and protocol for talking to higherlevel computer such as...
- Raspberry Pi which will run node
- johnny-Five, a nodebot library
- Firebase to give our thing Internet

### johnny-Five
- Documentation is great! each component has a picture has a picture of exactly what you want your breadboard/arduino to look like to get it working, and a program to start working with the component

### Firebase
- Goodies to make app dev easier:
  - realtime data (this is what we'll be using)
  - authentication
  - hosting

#### Realtime Database
- Realtime is where your bus *is* - not where it was an hour or a month ago. [wherebus.firebaseapp.com](https://wherebus.firebaseapp.com)
- Realtime is collaborative drawing [firesketch.firebaseapp.com](https://firesketch.firebaseapp.com)

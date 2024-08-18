> Bridge is a structural design pattern that lets you split a large class or a set of closely related classes into two separate hierarchies - abstraction and implementation - which can be developed independently of each other.

The pattern attempts to solve the problem of extending a class in multiple dimensions. For example, a Shape to a Form and a Colour. 
## Structure
![[Pasted image 20240818173433.png]]
1. The Abstraction provides high-level control logic. It relies on the implementation object to do the actual low-level work.
2. The Implementation declares the interface that's common for all concrete implementations. An abstraction can only communicate with an implementation object via methods that are declared here.
3. Concrete implementations contain platform-specific code.
4. Refined Abstractions provide variants of control logic. Like their parent, they work with different implementations via the general implementation interface.
5. Usually, the Client is only interested in working with the abstraction. However, it's the client's job to link the abstraction object with one of the implementation objects.
## Pseudocode
![[Pasted image 20240818173634.png]]
```java
// The "abstraction" defines the interface for the "control"
// part of the two class hierarchies. It maintains a reference
// to an object of the "implementation" hierarchy and delegates
// all of the real work to this object.
class RemoteControl is
    protected field device: Device
    constructor RemoteControl(device: Device) is
        this.device = device
    method togglePower() is
        if (device.isEnabled()) then
            device.disable()
        else
            device.enable()
    method volumeDown() is
        device.setVolume(device.getVolume() - 10)
    method volumeUp() is
        device.setVolume(device.getVolume() + 10)
    method channelDown() is
        device.setChannel(device.getChannel() - 1)
    method channelUp() is
        device.setChannel(device.getChannel() + 1)

// You can extend classes from the abstraction hierarchy
// independently from device classes.
class AdvancedRemoteControl extends RemoteControl is
    method mute() is
        device.setVolume(0)

// The "implementation" interface declares methods common to all
// concrete implementation classes. It doesn't have to match the
// abstraction's interface. In fact, the two interfaces can be
// entirely different. Typically the implementation interface
// provides only primitive operations, while the abstraction
// defines higher-level operations based on those primitives.
interface Device is
    method isEnabled()
    method enable()
    method disable()
    method getVolume()
    method setVolume(percent)
    method getChannel()
    method setChannel(channel)

// All devices follow the same interface.
class Tv implements Device is
    // ...

class Radio implements Device is
    // ...

// Somewhere in client code.
tv = new Tv()
remote = new RemoteControl(tv)
remote.togglePower()

radio = new Radio()
remote = new AdvancedRemoteControl(radio)
```

# USB to Serial to HID

A tool which emulates a HID device (keyboard/mouse) to control one PC from another.

This can be used as the Keyboard and Mouse in a KVM - either an IP KVM (like PiKVM) or a laptop KVM.

## Images

![Top](/images/top.png)
![Bottom](/images/bottom.png)

## Usage

### PiKVM

The [PiKVM](https://github.com/pikvm/pikvm) project makes use of a Raspberry Pi to provide KVM over IP. Simply add an HDMI capture device and some way to do keyboard/mouse control. The PiKVM team provides a couple of ways of doing this, but this project is an alternative to it.

#### Set up

You need to be able to set the override.yaml in a PiKVM install. This typically means:

- Connect via SSH or the web terminal (`su -` to switch to root user)
- Enable read/write - `rw`
- Add the below config section - `nano /etc/kvmd/override.yaml`
    - [More information about the config files](https://docs.pikvm.org/first_steps/#structure-of-configuration-files)
- Make readonly - `ro`

```yaml
kvmd:
    hid:
        type: ch9329
```

#### Laptop KVM

There exists a project which uses a piece of custom hardware to turn a laptop into a KVM - [Openterface](https://openterface.com/) - which means you can use your laptop as a PC crash cart. This project can be used as a cheaper alternative.

With a USB HDMI capture device (like [this](https://www.amazon.co.uk/UGREEN-Thunderbolt-Compatible-Camera-iPad-Laptop-Phone/dp/B0CFQ2BMPZ)), this hardware and a [fork of the Openterface software](https://github.com/Jallerton00/Openterface_QT), you can mimic most of what the Openterface project can achieve.

This is not feature complete - the original project provides more options for host software; a USB port swhich which can be switched between host and target & integrated HDMI capture - but may be a decent alternative for some.

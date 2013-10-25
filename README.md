# python-cec - libcec bindings for Python

`python-cec` allows you to control your TV, reciever and other CEC-compliant HDMI devices from a python script on a computer. Most computer graphics cards don't support CEC; you'll need a [Pulse-Eight USB-CEC adapter](http://www.pulse-eight.com/store/products/104-usb-hdmi-cec-adapter.aspx) or a Raspberry Pi (Untested).

## Installing:

### Install dependencies
To build python-cec, you need the libcec development libraries:

On Gentoo:
```
sudo emerge libcec
```

On Ubuntu:
```
sudo apt-get install libcec-dev
```

On OS X:
```
brew install libcec
```

### Checkout, build and install

```
git clone https://github.com/trainman419/python-cec.git
cd python-cec
python setup.py install
```

## Getting Started

A simple example to turn your TV on:

```python
import cec

cec.init()

tv = cec.Device(0)
tv.power_on()
```

## API


```python
import cec

adapters = cec.list_adapters() # may be called before init()

cec.init(adapter=cec.DEFAULT)

cec.close()  # not implemented yet

cec.add_callback(event, handler)  # not implemented yet

cec.remove_callback(event, handler)  # not implemented yet

devices = cec.list_devices()

class Device:
   is_on()
   power_on()
   standby()
   address
   physical_address
   vendor
   osd_string
   cec_version
   language
   is_active() # not implemented yet

cec.is_active_source() # not implemented yet
cec.set_active_source()  # not implemented yet
cec.set_inactive_source()  # not implemented yet

cec.volume_up()
cec.volume_down()
# TODO: mute/unmute
# TODO: audio status

cec.set_physical_address(addr) # not implemented yet

cec.set_stream_path(addr) # not implemented yet
```

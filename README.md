※ Fixes
makefile modify

LIBS = -lwiringPi -lpthread
=>
LIBS = -lwiringPi -lpthread -lm -lrt -lcrypt



gpio_keyd
========

gpio_keyd is a maaping program between GPIO and key inputs by uinput.
gpio_keyd needs wiringPi library in order to control GPIO.

### Installation

```
$ git clone https://github.com/hardkernel/wiringPi.git
$ cd wiringPi
$ sudo ./build
$ cd
$ git clone https://github.com/bkrepo/gpio_keyd.git
$ cd gpio_keyd
$ make
$ sudo make install
```

### Usage
```
Usage: gpio_keyd [option]
Options:
  -c <config file>           set the configuration file (default: "/etc/gpio_keyd.conf")
  -i <polling interval>      set polling interval time (default: 10000 us)
  -d                         run as deamon
  -h                         help
```

### Configuration
gpio_keyd uses the configuration file which is including the GPIO-key mapping information.
GPIO pin means the wiringPi GPIO pin number. Digital GPIO can configure 'active high' or 'active low' by 'Active value'

gpio_keyd also support analog GPIO input. Analog GPIO only works with 'active low'.

* (Example: /etc/gpio_keyd.conf)
```
# Digital input
# <Key code>	<GPIO type>	<GPIO pin>	<Active value>
KEY_LEFT	digital		1		0
KEY_RIGHT	digital		4		0
KEY_UP		digital		16		0
KEY_DOWN	digital		15		0
KEY_1		digital		23		0
KEY_5		digital		22		0
KEY_X		digital		31		0
KEY_Z		digital		11		0
KEY_S		digital		10		0
KEY_A		digital		6		0
KEY_Q		digital		26		0
KEY_W		digital		27		0

# Analog input
# <Key code>	<GPIO type>	<ADC port>	<ADC active value>
KEY_I		analog		0		0
KEY_K		analog		0		2045
KEY_J		analog		1		0
KEY_L		analog		1		2045
```

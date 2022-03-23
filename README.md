# AW9523 Micropython LED Driver

A simplified micropython driver for Adafruit's AW9523 LED driver.
Note: the GPIO expander mode is currently unavailable with this driver.

## Example

```python
from machine import Pin, I2C
i2c = I2C(1, scl=Pin(27), sda=Pin(26))
from aw9523 import AW9523
aw = AW9523(i2c)

# Work with a single LED. Values between 0 and 255
aw[0] = 0
aw[0] = 10
aw[0] = 255
aw.reset()
aw[0] = 1000
# Traceback (most recent call last):
#   File "<stdin>", line 1, in <module>
#   File "aw9523.py", line 55, in __setitem__
# ValueError: Value must be 0 to 255

# Work with multiple LEDs at the same time:
aw[:16] = 0
aw[2:5] = [10, 50, 10]
```

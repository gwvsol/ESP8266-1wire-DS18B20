## ESP8266-1wire-DS18B20

[![micropython](https://user-images.githubusercontent.com/13176091/53680744-4dfcc080-3ce8-11e9-94e1-c7985181d6a5.png)](https://micropython.org/)

Библиотека для работы ESP8266 с DS18B20

***
### Схема включения DS18B20

![esp8266-ds18b20](https://user-images.githubusercontent.com/13176091/53965098-3747d680-40f9-11e9-83d7-e3fb61a46e9d.png)

Код который используется в стандартной библиотеке [ds18x20.py](https://github.com/micropython/micropython/blob/master/drivers/onewire/ds18x20.py) часто завершается ошибкой, что приводит к прекращению работы всего приложения.
```python
if self.ow.crc8(self.buf):          # здесь возникает частая ошибка, что приводит 
    raise Exception('CRC error')    # к прекращению работы всего приложения
```

В данной библиотеке это фрагмент кода убран.

Библиотека используется так же как и стандартная [ds18x20.py](https://github.com/micropython/micropython/blob/master/drivers/onewire/ds18x20.py)

### Пример использования
```python
from machine import Pin
from onewire import OneWire
from time import sleep_ms
from ds18b20 import DS18X20
ds = DS18X20(OneWire(Pin(12)))
roms = ds.scan()
ds.convert_temp()
time.sleep_ms(750)
for rom in roms:
    print(ds.read_temp(rom))
```












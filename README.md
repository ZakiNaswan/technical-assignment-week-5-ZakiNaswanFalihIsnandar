# Script Code
import time import board import adafruit_dht import psutil

for proc in psutil.process_iter(): if proc.name() == 'libgpiod_pulsein' or proc.name() == 'libgpiod_pulsei': proc.kill() sensor = adafruit_dht.DHT11(board.D23) while True: try: temp = sensor.temperature humidity = sensor.humidity print("Temperature: {}*C Humidity: {}% ".format(temp, humidity)) except RuntimeError as error: print(error.args[0]) time.sleep(2.0) continue except Exception as error: sensor.exit() raise error time.sleep(2.0)

# Wiring Diagram
![WhatsApp Image 2022-07-21 at 16 48 18](https://user-images.githubusercontent.com/107292901/180247647-dd6e3fde-b1ef-45bf-8b94-b86779f623f7.jpeg)

# Data Dari Sensor
![2022-07-15-134600_1366x768_scrot](https://user-images.githubusercontent.com/107292901/180248075-994bfbce-c8d1-48d3-b1a6-6f377523ebec.png)
![2022-07-15-134846_1366x768_scrot](https://user-images.githubusercontent.com/107292901/180248130-b270a110-cd64-40fe-abeb-57c7a400096b.png)

# Grafik
![2022-07-15-135933_1366x768_scrot](https://user-images.githubusercontent.com/107292901/180248614-9e5144b2-243b-45bc-a96b-09267f851461.png)

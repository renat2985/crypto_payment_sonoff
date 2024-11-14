[🇷🇺 Русская версия документации здесь](https://github.com/renat2985/crypto_payment_sonoff/blob/main/README_RU.md)

# Payment for Your Services via Solana or Toncoin

A convenient and fast way to implement paid services using the Solana or TonCoin cryptocurrency. The process is simple: You open any crypto wallet, scan the QR code (for example, it can be printed on a sheet with the required amount), transfer the specified amount, and as soon as the payment is received, the relay will activate and turn on your device for the time you set. This could be any device, from a kettle, coffee machine, or light bulb to powering electricity in a room or another location.

You can assemble the device yourself or ask to build it for you. To order a ready-made device, contact me via [Telegram](https://t.me/ESPiotDevice), [Skype](https://skype:renat2985?chat), [Discord](https://discord.com/invite/zaGaDuGe).
We have a similar project with a screen, [check it out](https://github.com/renat2985/crypto_payment_touchScreen).


[![IMAGE ALT TEXT HERE](https://github.com/renat2985/crypto_payment_sonoff/blob/main/doc/intro4.png)](https://www.youtube.com/watch?v=zKdVJmzJNLM&list=PL6NJTNxbvy-LpsI6D_1RM6v5YWDvsm5j4)

### Key Features:

1. **Device Connection:**
   - When first powered on, if the device can’t find the router or if you press the button on the ESP itself, it will create an access point named “Crypto payments.”
     
     <img src="https://github.com/renat2985/crypto_payment_sonoff/blob/main/doc/WiFi.png" width="200px">
   - Connect to this access point (no password needed) and open a browser, then enter http://192.168.4.1. Usually, after connecting to Wi-Fi, the Captive portal will automatically open and redirect you to the desired page.
     
     <img src="https://github.com/renat2985/crypto_payment_sonoff/blob/main/doc/AP1.png" width="300px">
   - Click "Configure WiFi" to proceed with the setup.

2. **Device Configuration:**
   - **Router and Password:** Enter your Wi-Fi connection details.
   - **Crypto Name:** The cryptocurrency associated with the device, for example, "Solana" or "Toncoin". You can optionally include GPIO pins in this field. Example: `Solana:12,11,22`, where "Solana" is the cryptocurrency, and `12, 11, 22` are the corresponding pin numbers for the relay, reset button, and LED (`RELAY_PIN`, `BUTTON_PIN`, `LED_PIN`).
   - **Your Wallet:** Enter your wallet address to receive payments.
   - **CoinMarketCap API:** Used to retrieve the current Solana exchange rate in fiat currency.
   - **Tatum API:** Used to obtain the balance of your wallet.
   For testing purposes, you can use the built-in APIs; however, for long-term use, it is strongly recommended to register on the respective websites ([coinmarketcap.com](https://coinmarketcap.com/api/) and [tatum.io](https://tatum.io/)) and obtain your own API keys. The free plans allow up to 10,000 requests per month, which is sufficient for 10 devices. However, as the number of devices increases, there may be delays in retrieving up-to-date information, potentially causing issues with payment processing.
   - **Currency:** Select the currency in which you want to receive payments (EUR, USD, RUB, BYN, BGN, GBP, etc.). This is necessary for automatic conversion to solana based on the current exchange rate, updated hourly through coinmarketcap.com.
   - **Service Currency Price:** Specify the price in your selected currency that the customer should pay.
   - **Payment Tolerance:** In this field, specify the acceptable price deviation. Since the Ton price constantly fluctuates, you need to indicate a deviation range (as a single number) that you are willing to accept for payment.
   - **Relay Work Time:** Specify how long the relay should be activated in seconds. This can range from one second (for simulating a button press) to several minutes or hours.

   _Please note, if the blue LED starts flashing, it is a signal that something went wrong. You might have entered your Solana or Toncoin wallet incorrectly. It could also indicate an incorrect CoinMarketCap or Tatum API. If you are using the standard API (without changes), it may have exceeded the limit, and you might need to create your own CoinMarketCap API. The WiFi signal has disappeared. Another reason could be that the trial period of the software has expired._
     
     <img src="https://github.com/renat2985/crypto_payment_sonoff/blob/main/doc/APFull2.png" width="500px">


### Instructions for Self-Assembly:

For self-assembly you will need any of these devices: SONOFF OLD, [SONOFF RF R2, SONOFF BASICR2](https://github.com/renat2985/crypto_payment_sonoff/blob/main/doc/flash_gpio_r2.png), [SONOFF Mini R1, SONOFF Mini R2](https://github.com/renat2985/crypto_payment_sonoff/blob/main/doc/flash_gpio_mini_r2.png), [SONOFF S26, SONOFF S26R2](https://github.com/renat2985/crypto_payment_sonoff/blob/main/doc/flash_gpio_s26.jpg).

- A programmer, such as USB to TTL / PL230
- A soldering iron and wires

  <img src="https://github.com/renat2985/crypto_payment_sonoff/blob/main/doc/flash_gpio4.png" width="500px">


We have added support for SONOFF devices based on the ESP32 (Dual R3, Mini R4, Basic R4, POW, THR316), but most of them have not yet undergone full testing. If you encounter any issues, please contact us, and we will do our best to assist you.
On devices with ESP8266 (Mini R1, Mini R2, S26, S26R2), all GPIO (pins) remained unchanged, and no configuration is required. However, with ESP32, many GPIO pins have changed depending on the device model. We decided not to release separate firmware for each model as it would make maintenance more complicated. Therefore, you will need to manually configure the GPIO for your device.
To do this, after the device name, add a colon (:) followed by the GPIO for the relay, then the GPIO for the reset button, and finally the GPIO for the LED.
Below, you will find a list of devices and their corresponding GPIO settings. Simply copy the necessary configurations, and the device should work.

```Solana:27,0,13``` ```Toncoin:27,0,13```  Dual R3

```Solana:26,0,19``` ```Toncoin:26,0,19``` Mini R4

```Solana:4,9,19``` ```Toncoin:4,9,19``` Mini R4M

```Solana:4,9,6``` ```Toncoin:4,9,6``` Basic R4

```Solana:13,0,18``` ```Toncoin:13,0,18``` POW 16a

```Solana:4,0,18``` ```Toncoin:4,0,18``` POW 20a

```Solana:21,0,13``` ```Toncoin:21,0,13``` POW Ring

```Solana:21,0,15``` ```Toncoin:21,0,15``` THR316

Good luck! If you have any questions, don't hesitate to reach out.


# Web installer (recommended)
## [https://renat2985.github.io/crypto_payment_sonoff/](https://renat2985.github.io/crypto_payment_sonoff/)


### For Advanced Users: Firmware Instructions via Programmer
### Specification [ESP8266 crypto_payment_sonoff.ino.bin](https://github.com/renat2985/crypto_payment_sonoff/raw/main/build/esp8266.esp8266.generic/crypto_payment_sonoff.ino.bin) file
```
  -  Module: Generic ESP8266 Module
  -  Flash Size: 1M
  -  CPU Frequency: 80Mhz
  -  Flash Mode: DOUT
  -  Flash Frequency: 40Mhz

  { "path": "./build/esp8266.esp8266.generic/crypto_payment_sonoff.ino.bin", "offset": 0 }
```

### Specification [ESP32 crypto_payment_sonoff.ino.bin](https://github.com/renat2985/crypto_payment_sonoff/raw/main/build/esp32.esp32.esp32/crypto_payment_sonoff.ino.bin), [ESP32C3 crypto_payment_sonoff.ino.bin](https://github.com/renat2985/crypto_payment_sonoff/raw/main/build/esp32.esp32.esp32c3/crypto_payment_sonoff.ino.bin), [ESP32S3 crypto_payment_sonoff.ino.bin](https://github.com/renat2985/crypto_payment_sonoff/raw/main/build/esp32.esp32.esp32s3/crypto_payment_sonoff.ino.bin) file
```
  { "path": "./build/esp32.esp32.esp32*/crypto_payment_sonoff.ino.bootloader.bin", "offset": 4096 },
  { "path": "./build/esp32.esp32.esp32*/crypto_payment_sonoff.ino.partitions.bin", "offset": 32768 },
  { "path": "./build/esp32.esp32.esp32*/boot_app0.bin", "offset": 57344 },
  { "path": "./build/esp32.esp32.esp32*/crypto_payment_sonoff.ino.bin", "offset": 65536 }
```

### ESP8266 NodeMCU Flasher
https://github.com/nodemcu/nodemcu-flasher
Download Release: [Win32](https://github.com/nodemcu/nodemcu-flasher/blob/master/Win32/Release/ESP8266Flasher.exe) or [Win64](https://github.com/nodemcu/nodemcu-flasher/blob/master/Win64/Release/ESP8266Flasher.exe).

## :battery: Donation

If you like this project, you can buy me a cup of coffee :coffee:

<img src="https://github.com/renat2985/renat2985/raw/main/donate/donate.png" width="100%">

- PayPal [https://www.paypal.me/RKevrels](https://www.paypal.me/RKevrels/5)
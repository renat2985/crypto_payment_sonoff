
# Оплата ваших услуг через Solana, Cosmos, Algorand или Toncoin

 Удобный и быстрый способ внедрения платных услуг с использованием криптовалюты Solana, Cosmos, Algorand или Toncoin. Процесс простой: Вы открываете любой крипто кошелек, сканируете QR-код (Его можно например распечатать на листике с необходимой суммой), переводите эту указанную сумму, и как только платеж будет получен, реле активируется и включит ваш прибор на заданное вами время. Это может быть любой прибор, от чайника, кофемашины и лампочки до включения электричества в помещение или любом другом месте.

Вы можете собрать устройство самостоятельно или попросить это сделать для вас. Для заказа готового устройства свяжитесь через [Telegram](https://t.me/ESPiotDevice), [Skype](https://skype:renat2985?chat), [Discord](https://discord.com/invite/zaGaDuGe).

У нас есть похожий проект с экраном, [посмотри](https://github.com/renat2985/crypto_payment_touchScreen).


[![IMAGE ALT TEXT HERE](https://github.com/renat2985/crypto_payment_sonoff/blob/main/doc/intro4.png)](https://www.youtube.com/watch?v=zKdVJmzJNLM&list=PL6NJTNxbvy-LpsI6D_1RM6v5YWDvsm5j4)

### Основные функции:

1. **Подключение устройства:**
   - При первом включении, если устройство не находит роутер, или если вы нажмёте кнопку на самом Sonoff, оно создаст точку доступа с именем ”Crypto payments”.
     
     <img src="https://github.com/renat2985/crypto_payment_sonoff/blob/main/doc/WiFi.png" width="200px">
   - Подключитесь к этой точке (пароль не требуется) и откройте браузер, где введите http://192.168.4.1. Обычно после подключения к Wi-Fi автоматически откроется Activ portal, который перенаправит вас на нужную страницу.
     
     <img src="https://github.com/renat2985/crypto_payment_sonoff/blob/main/doc/AP1.png" width="300px">
   - Нажмите "Configure WiFi" для настройки.

2. **Настройка устройства:**
   - **Роутер и пароль:** Введите данные для подключения к вашему Wi-Fi.
   - **Crypto Name:** Криптовалюта устройства, например, "Solana", "Cosmos", "Algorand" или "Toncoin". Вы можете опционально добавить в это поле GPIO пины. Пример: `Solana:12,11,22`, где Solana — это криптовалюта устройсва, а `12,11,22` — это соответствующие номера пинов для реле, кнопка сброса и светодиода (`RELAY_PIN,BUTTON_PIN,LED_PIN`).
   - **Your Wallet:** Введите адрес вашего кошелька для приема платежей.
   - **CoinMarketCap API:** Используется для получения текущего курса Solana в фиатной валюте.
   - **Tatum API:** Служит для получения информации о балансе вашего кошелька.
   Для тестирования можно использовать встроенные API, однако для долгосрочного использования настоятельно рекомендуется зарегистрироваться на соответствующих сайтах ([coinmarketcap.com](https://coinmarketcap.com/api/) и [tatum.io](https://tatum.io/)) и получить собственные ключи API. Бесплатные тарифы позволяют выполнять до 10 000 запросов в месяц, чего достаточно для 10 устройств. Однако при увеличении количества устройств возможны перебои с получением актуальной информации, что может привести к сбоям в процессе оплаты.
   - **Сurrency:** Выберите валюту, в которой хотите получать оплату (EUR, USD, RUB, BYN, BGN, GBP и др.). Это необходимо для автоматической конвертации суммы в Solana на основе текущего курса, который обновляется каждый час через coinmarketcap.com.
   - **Service Currency Price:** Укажите цену в выбранной валюте, которую клиент должен оплатить.
   - **Payment Tolerance:** В этой ячейке указывается допустимая погрешность в цене. Поскольку стоимость криптовалюты постоянно колеблется, здесь нужно указать диапазон отклонений (одной цифрой), который вы готовы принять при оплате.
   - **Relay Work Time:** Укажите, на сколько секунд должно включиться реле. Это может быть от одной секунды (например, для имитации нажатия кнопки) до нескольких минут или часов.
     
      <img src="https://github.com/renat2985/crypto_payment_sonoff/blob/main/doc/APFull2.png" width="500px">

3. **Сброс настроек:**

      Чтобы вернуть устройство к заводским настройкам, выполните следующие действия:
      1.	Нажмите кнопку на устройстве Sonoff.
      2.	Устройство перезагрузится.
      3.	После перезагрузки появится точка доступа с именем Crypto Sonoff.

      Теперь устройство готово к повторной настройке.

_Обратите внимание, если начал мигать синий светодиод — это сигнал, что что-то пошло не так. Возможно, вы неправильно написали свой Solana, Cosmos, Algorand или Toncoin кошелек. Также это может указывать на неправильный API от CoinMarketCap или Tatum. Если вы используете стандартный API (не меняли его), возможно, он превысил лимит, и вам нужно сделать собственный [CoinMarketCap API](https://coinmarketcap.com/api/), [Tatum API](https://tatum.io/). Плохой сигнал WiFi. Еще одна причина может быть в том, что закончился пробный период программного обеспечения._

### Инструкции для самостоятельной сборки:

Для самостоятельной сборки вам потребуется любое из этих устройств: SONOFF OLD, [SONOFF RF R2, SONOFF BASICR2](https://github.com/renat2985/crypto_payment_sonoff/blob/main/doc/flash_gpio_r2.png), [SONOFF Mini R1, SONOFF Mini R2](https://github.com/renat2985/crypto_payment_sonoff/blob/main/doc/flash_gpio_mini_r2.png), [SONOFF S26, SONOFF S26R2](https://github.com/renat2985/crypto_payment_sonoff/blob/main/doc/flash_gpio_s26.jpg).

Дополнительно вам понадобятся:
- Программатор, например USB to TTL / PL230
- Паяльник и провода

  <img src="https://github.com/renat2985/crypto_payment_sonoff/blob/main/doc/flash_gpio4.png" width="500px">


Мы добавили поддержку устройств SONOFF на базе ESP32 (Dual R3, Mini R4, Basic R4, POW, THR316), но большинство из них не прошло полное тестирование. Если у вас возникнут проблемы, пожалуйста, свяжитесь с нами, и мы постараемся помочь. На устройствах с ESP8266 (Mini R1, Mini R2, S26, S26R2) все GPIO (пины) оставались неизменными. Вам не нужно ничего настраивать. Однако на ESP32 многие пины изменились в зависимости от модели устройства. Мы решили не выпускать отдельные прошивки для каждой модели, так как это усложнило бы их поддержку. Поэтому вам нужно будет вручную настроить GPIO для вашего устройства. Для этого в после Crypto Name после имени крипто валюты, добавьте : далее сначала GPIO реле, затем для GPIO кнопки сброса, и в конце GPIO для светодиода (LED). 
Ниже вы найдете список устройств и соответствующих им GPIO. Просто скопируйте нужные настройки, и устройство должно заработать.

Dual R3 ```Solana:27,0,13``` ```Cosmos:27,0,13``` ```Algorand:27,0,13``` ```Toncoin:27,0,13```

Mini R4 ```Solana:26,0,19``` ```Cosmos:26,0,19``` ```Algorand:26,0,19``` ```Toncoin:26,0,19```

Mini R4M ```Solana:4,9,19``` ```Cosmos:4,9,19``` ```Algorand:4,9,19``` ```Toncoin:4,9,19```

Basic R4 ```Solana:4,9,6``` ```Cosmos:4,9,6``` ```Algorand:4,9,6``` ```Toncoin:4,9,6```

POW 16a ```Solana:13,0,18``` ```Cosmos:13,0,18``` ```Algorand:13,0,18``` ```Toncoin:13,0,18```

POW 20a ```Solana:4,0,18``` ```Cosmos:4,0,18``` ```Algorand:4,0,18``` ```Toncoin:4,0,18```

POW Ring ```Solana:21,0,13``` ```Cosmos:21,0,13``` ```Algorand:21,0,13``` ```Toncoin:21,0,13```

THR316 ```Solana:21,0,15``` ```Cosmos:21,0,15``` ```Algorand:21,0,15``` ```Toncoin:21,0,15```

Удачи! 

# Web installer (recommended)
## [https://renat2985.github.io/crypto_payment_sonoff/](https://renat2985.github.io/crypto_payment_sonoff/)


### Для совсем профи инструкция для прошивки через программатор
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

If you like this project, you can give me a cup of coffee :coffee:

<img src="https://github.com/renat2985/renat2985/raw/main/donate/donate.png" width="100%">

- PayPal [https://www.paypal.me/RKevrels](https://www.paypal.me/RKevrels/5)
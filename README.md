# Sosial Media
Telegram : https://t.me/minsanztuy/   
Website  : https://autotradevip.com/

# binollaapi
Binolla API  
Website    : https://autotradevip.com/en/  
Olmyptrade : https://youtu.be/zTZT7zDlmtU  
Binomo     : https://youtu.be/ww9rVMX5TK4  
IQ Option  : https://youtu.be/4i3YUEDRGWY  
Quotex     : https://www.youtube.com/channel/UCCqnm8XHUoc0Ude78RJwmoA  
Binolla     : https://www.youtube.com/channel/UCCqnm8XHUoc0Ude78RJwmoA  
Expert Option     : https://www.youtube.com/channel/UCCqnm8XHUoc0Ude78RJwmoA   
Alpari     : https://www.youtube.com/channel/UCCqnm8XHUoc0Ude78RJwmoA  
Exness     : https://www.youtube.com/channel/UCCqnm8XHUoc0Ude78RJwmoA  


### Import
```python
from binollapi import Binolla
```
### Login by ssid
if connect sucess return True,None  

if connect fail return False,None  
```python
from binollapi import Binolla
ssid = "your ssid"
weboscket_cookie = "websocket cookie"
account=Binolla(set_ssid=ssid,weboscket_cookie=weboscket_cookie)
check_connect,message=account.connect()
print(check_connect,message)
```

### Get Balance
```python
from binollapi import Binolla
ssid = "your ssid"
weboscket_cookie = "websocket cookie"
account=Binolla(set_ssid=ssid,weboscket_cookie=weboscket_cookie)
check_connect,message=account.connect()
account.change_balance("PRACTICE")
balance=account.get_balance()
print(balance)
```

### Buy 
```python
from binollapi import Binolla
ssid = "your ssid"
weboscket_cookie = "websocket cookie"
asset="GBPCAD_otc"
amount=14000
dir="call"#"call"/"put"
duration=1#sec
account=Binolla(set_ssid=ssid,weboscket_cookie=weboscket_cookie)
check_connect,message=account.connect()
API.change_balance("PRACTICE")
if check_connect:
    print("Balance: ",API.get_balance())
    c, buy_info = API.buy(asset,amount,dir,duration)
    if c == True:
        print(c, buy_info)
    else:
        print(c, buy_info)
```

### Buy Check Win
```python
from binollapi import Binolla
ssid = "your ssid"
weboscket_cookie = "websocket cookie"
asset="GBPCAD_otc"
amount=14000
dir="call"#"call"/"put"
duration=1#sec
account=Binolla(set_ssid=ssid,weboscket_cookie=weboscket_cookie)
check_connect,message=account.connect()
API.change_balance("PRACTICE")
if check_connect:
    print("Balance: ",API.get_balance())
    c, buy_info = API.buy(asset,amount,dir,duration)
    if c == True:
        print("----Trade----")
        print("Get: ",API.check_win(buy_info['deal']['uuid']))
        print("----Trade----")
        print("Balance: ",API.get_balance())
    else:
        print("BUY Fail")
```

### Get Candle
```python
from binollapi import Binolla
import time, datetime
ssid = "your ssid"
weboscket_cookie = "websocket cookie"
asset="GBPCAD_otc"
amount=14000
dir="call"#"call"/"put"
duration=1#sec
account=Binolla(set_ssid=ssid,weboscket_cookie=weboscket_cookie)
check_connect,message=account.connect()
if check_connect:
    asset="EURAUD_otc"
    _time=int(time.time())#the candle end of time
    offset=3600#how much sec want to get     _time-offset --->your candle <---_time
    period=60#candle size in sec
    print("---Sedang Mencari History candlestick---\n")
    candles=API.get_candles(asset,_time,offset,period)
    for candle in candles['history']:
        # print(candle)
        timestamp = datetime.datetime.fromtimestamp(candle[0]).strftime("%Y-%m-%d %H:%M")
        open_price = candle[1]
        high_price = candle[2]
        low_price = candle[3]
        close_price = candle[4]
        volume = candle[5]
        print(f"{timestamp},{open_price},{high_price},{low_price},{close_price},{volume}")

    API.close()
```

### History Detail
```python
from binollapi import Binolla
import datetime
ssid = "your ssid"
weboscket_cookie = "websocket cookie"
API =Binolla(host="binolla.com",set_ssid=ssid,weboscket_cookie=weboscket_cookie)
check_connect, message=API.connect()
if check_connect:
    # Mendapatkan detail history candlestick
    asset = "EURAUD_otc"  # Aset yang ingin Anda periksa
    end_time = datetime.datetime.now()  # Waktu akhir untuk data candlestick
    period = 60  # Periode candlestick dalam detik (opsional, default adalah 60)
    offset = 61 * 60  # Jeda waktu dalam detik antara waktu yang diminta dan data yang diterima (opsional, default adalah 61 menit)

    history_detail = API.get_history_detail_binolla(asset, end_time, period, offset)

    # Sekarang Anda dapat menggunakan DataFrame `history_detail` untuk menganalisis data candlestick
    print(history_detail)

API.close()
```

### Get Gistory Binolla
```python
from binollapi import Binolla
import datetime
ssid = "your ssid"
weboscket_cookie = "websocket cookie"
API =Binolla(host="binolla.com",set_ssid=ssid,weboscket_cookie=weboscket_cookie)
check_connect, message=API.connect()
if check_connect:
    # Mendapatkan detail history candlestick
    asset = "EURAUD_otc"  # Aset yang ingin Anda periksa
    start_time = "2024-03-31 00:00:00"  # Waktu mulai data historis
    end_time = datetime.datetime.now().strftime('%Y-%m-%d %H:%M:%S')  # Waktu akhir saat ini
    # end_time = "2024-04-01 00:00:00"  # Waktu akhir data historis
    candle = "M1"  # Model candle (Misalnya: "M1" untuk 1 menit)
    csv_path = "historical_data.csv"  # Path untuk menyimpan data historis dalam format CSV
    # Mendapatkan data historis menggunakan metode get_history_binolla
    historical_data = API.get_history_binolla(asset, start_time, end_time, candle, csv_path)
    # Melakukan analisis atau pengolahan data historis
    # Contoh: Menampilkan seluruh data historis
    print(historical_data)

API.close()
```

### GET realtime candle
```python
from binollapi import Binolla
ssid = "your ssid"
weboscket_cookie = "websocket cookie"
API =Binolla(host="binolla.com",set_ssid=ssid,weboscket_cookie=weboscket_cookie)
check_connect,message=API.connect()
if check_connect:
    asset="NZDUSD_otc"
    list_size=10#this is setting how much Binolla you want to save
    API.start_candles_stream("NZDUSD_otc",list_size)
    while True:
        if len(API.get_realtime_candles("NZDUSD_otc"))==list_size:
            break
    print(API.get_realtime_candles("NZDUSD_otc"))
    API.close()
```

### Get Payment
```python
from binollapi import Binolla
ssid = "your ssid"
weboscket_cookie = "websocket cookie"
API =Binolla(host="binolla.com",set_ssid=ssid,weboscket_cookie=weboscket_cookie)
check_connect, message=API.connect()
if check_connect:
    all_data=account.get_payment()
    for asset_name in all_data:
        asset_data=all_data[asset_name]
        print(asset_name,asset_data["payment"],asset_data["open"])
API.close()
```

### Get all asset name
```python
from binollapi import Binolla
ssid = "your ssid"
weboscket_cookie = "websocket cookie"
API =Binolla(host="binolla.com",set_ssid=ssid,weboscket_cookie=weboscket_cookie)
check_connect, message=API.connect()
if check_connect:
    raw_asset = API.get_all_asset_name()
    print(raw_asset)
API.close()
```

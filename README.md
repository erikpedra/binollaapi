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

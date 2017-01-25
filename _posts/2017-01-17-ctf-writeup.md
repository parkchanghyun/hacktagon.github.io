---
layout: post
title: About some ctf writeups
categories:
- ctf
- pwnable
---

한글테스트

# first
aaa

## second
bbb

{% highlight python %}
from socket import *
import telnetlib
import struct
import time

# socat tcp-listen:31337,reuseaddr,fork,bind=0.0.0.0 exec:./auction &

p = lambda x: struct.pack("<Q", x)
up = lambda x: struct.unpack("<Q", x)[0]

host = "192.168.76.131"
port = 31337

def main():

    def rw(s, f):
        r = ''
        while f not in r:
            c = s.recv(1)
            if not c:
                break
            r += c
        return r

    s = socket(AF_INET, SOCK_STREAM)
    s.connect((host,port))

    print rw(s, 'on sale!')
    s.send('reg cykor\n')
    time.sleep(1)
    print s.recv(4096)
    s.send('bid 1234\n')
    time.sleep(1)
    print s.recv(4096)
    s.close()

if __name__ == '__main__':
    main()
{% endhighlight %}

### End
done
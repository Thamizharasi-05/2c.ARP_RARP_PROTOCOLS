# 2c.SIMULATING ARP /RARP PROTOCOLS
## NAME-SRILAKSHMI.B.H
## REG.NO-212224100057
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
client.py
```import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
   ip=c.recv(1024).decode()
   try:
      c.send(address[ip].encode())
   except KeyError:
      c.send("Not Found".encode())
```

server.py
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
   ip=input("Enter logical Address : ")
   s.send(ip.encode())
   print("MAC Address",s.recv(1024).decode())
```

## OUPUT - ARP
client.py

<img width="716" height="143" alt="image" src="https://github.com/user-attachments/assets/db9dc4a2-51ad-48fd-9ed6-6b3ca5ce0eb4" />

server.py

<img width="768" height="301" alt="image" src="https://github.com/user-attachments/assets/d5b4fed8-f439-4841-a6d8-aefc76ea29e0" />

## PROGRAM - RARP

client.py
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
   ip=c.recv(1024).decode()
   try:
      c.send(address[ip].encode())
   except KeyError:
      c.send("Not Found".encode())
```

server.py
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
   ip=input("Enter MAC Address : ")
   s.send(ip.encode())
   print(“Logical Address”, s.recv(1024).decode())
```
## OUPUT -RARP
client.py

<img width="718" height="165" alt="image" src="https://github.com/user-attachments/assets/4bc9f942-eb19-4162-a729-2fbdf36ebc2b" />

server.py

<img width="784" height="247" alt="image" src="https://github.com/user-attachments/assets/ae38fce8-fda6-412e-bfed-4cb5d986e163" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.

# 2c.SIMULATING ARP /RARP PROTOCOLS
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
## SERVER.PY:
```
         
import socket        
s=socket.socket()          
s.connect(('localhost',8000))         
while True:           
    ip=input("Enter logical Address : ")           
    s.send(ip.encode())            
    print("MAC Address",s.recv(1024).decode())   
```
## CLIENT.PY:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"10.248.110.146":"F8:3D:C6:CE:5B:6E"};
while True:
    ip=c.recv(1024).decode()
    try:
       c.send(address[ip].encode())
    except KeyError:
       c.send("Not Found".encode())
```
## OUPUT - ARP
<img width="442" height="121" alt="Screenshot 2026-05-19 132944" src="https://github.com/user-attachments/assets/ad7c0a71-ec5b-4804-84f6-e909e288d558" />

## PROGRAM - RARP
## SERVER.PY:
```
            
import socket           
s=socket.socket()                
s.connect(('localhost',8000))                
while True:               
    ip=input("Enter MAC Address : ")                
    s.send(ip.encode())                   
    print("IP Address",s.recv(1024).decode())                
```
## CLIENT.PY:
```

import socket            
s=socket.socket()            
s.bind(('localhost',8000))                 
s.listen(5)            
c,addr=s.accept()                       
address={"F8:3D:C6:CE:5B:6E":"10.248.110.146"};             
while True:              
    ip=c.recv(1024).decode()            
    try:                
       c.send(address[ip].encode())             
    except KeyError:            
       c.send("Not Found".encode())               
```
## OUPUT -RARP
<img width="798" height="215" alt="Screenshot 2026-05-19 134441" src="https://github.com/user-attachments/assets/2054cd25-89c4-43dd-8551-2f8585764629" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.

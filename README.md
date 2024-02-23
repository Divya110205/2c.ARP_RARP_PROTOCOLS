# EX : 2c.SIMULATING ARP/RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP and RARP protocols using UDP.
## ALGORITHM FOR ARP:
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

## PROGRAM - ARP
### CLIENT
```
import socket
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
### SERVER
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
REG NO:
 ip=input("Enter logical Address : ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode()
```
## OUPUT - ARP
### SERVER
![2c 1](https://github.com/Divya110205/2c.ARP_RARP_PROTOCOLS/assets/119404855/b58b8c77-a937-4957-8272-008fbb6ba8da)
### CLIENT
![2c 2](https://github.com/Divya110205/2c.ARP_RARP_PROTOCOLS/assets/119404855/9036605f-01af-4e34-8483-49126ae2bce2)
## ALGORITHM FOR RARP:
### CLIENT
1. Start the program 
2. Using datagram sockets UDP function is established. 
3. Get the MAC address to be converted into IP address. 
4. Send this MAC address to server. 
5. Server returns the IP address to client.
### SERVER
1. Start the program. 
2. Server maintains the table in which IP and corresponding MAC addresses are stored. 
3. Read the MAC address which is send by the client. 
4. Map the IP address with its MAC address and return the IP address to client.
## PROGRAM - RARP
### SERVER
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
### CLIENT
```
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter MAC Address : ") 
    s.send(ip.encode()) 
    print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
### SERVER
![2c 3](https://github.com/Divya110205/2c.ARP_RARP_PROTOCOLS/assets/119404855/fbef2bb0-a6cc-463d-bb76-89f75f4a92ef)

### CLIENT
![2c 4](https://github.com/Divya110205/2c.ARP_RARP_PROTOCOLS/assets/119404855/5f6a0540-a321-4d6c-a163-f6df66e44c69)

## RESULT
Thus, the python program for simulating ARP protocols using and TCP RARP protocols using UDP was successfully 
executed.

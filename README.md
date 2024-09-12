## 2B IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## NAME: K KESAVA SAI
## REGISTER NUMBER: 212223230105
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM:
## Client:
```py
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
    while(i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=s

```
## Server:
```py
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement received from the server".encode())
```
## OUPUT:
## Client:
![2b 1](https://github.com/user-attachments/assets/cef41ecf-5bf1-4d81-87a2-a5fc2ce39d0c)

## Server:
![2b 2](https://github.com/user-attachments/assets/e4536ea2-0df8-4fc6-94d4-83d4f166b7d2)

## RESULT:
Thus, python program to perform stop and wait protocol was successfully executed

# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## Name : Adithya V
## Register no: 212223110001
## AIM
To write a python program to perform sliding window protocol.
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
### client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames:"))
l=list(range(size))
s=int(input("Enter window size:"))
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
### server
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknoledgement recieved from the server".encode())
```
## OUTPUT
### client
![image](https://github.com/karthik-2106/2b_SLIDING_WINDOW_PROTOCOL/assets/150319557/3aa12d2c-e48c-4ab7-8238-83105b099b16)
### server
![image](https://github.com/karthik-2106/2b_SLIDING_WINDOW_PROTOCOL/assets/150319557/333563cf-0586-4dff-b4ea-ed40a9bc520c)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed

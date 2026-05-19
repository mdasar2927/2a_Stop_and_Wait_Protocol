# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
## SERVER.PY
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    msg = s.recv(1024).decode()
    print(msg)

    s.send("Acknowledgement Received".encode())
```
## CLIENT.PY
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)

print("Waiting for connection...")

c, addr = s.accept()
print("Connected with", addr)

while True:
    i = input("Enter a data: ")

    c.send(i.encode())

    ack = c.recv(1024).decode()

    if ack:
        print(ack)
        continue
    else:
        c.close()
        break
```

## OUTPUT

server:

<img width="449" height="158" alt="image" src="https://github.com/user-attachments/assets/39fd1cb2-bd78-4936-9fe0-c9cb43675be0" />

client:

<img width="658" height="378" alt="image" src="https://github.com/user-attachments/assets/6364008b-81cc-4761-8bad-e3460acc555f" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.

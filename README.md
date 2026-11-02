# Ex-2b.-Sliding-Window-Protocol
AIM
To write a python program to perform sliding window protocol 
## ALGORITHM:
Start the program.
Get the frame size from the user
To create the frame based on the user request.
To send frames to server from the client side.
If your frames reach the server it will send ACK signal to client
Stop the Program

## PROGRAM
## CLIENT
```
import socket

server = socket.socket()
server.bind(('localhost', 8000))
server.listen(5)

client, address = server.accept()

total = int(input("Enter number of frames to send: "))
window = int(input("Enter Window Size: "))

frames = list(range(total))
start = 0

while start < total:
    end = min(start + window, total)

    client.send(str(frames[start:end]).encode())

    ack = client.recv(1024).decode()
    if ack:
        print(ack)

    start = end

client.close()
server.close()
```
## SERVER
```
import socket

client = socket.socket()
client.connect(('localhost', 8000))

while True:
    data = client.recv(1024).decode()

    if not data:
        break

    print("Received Frames:", data)

    client.send("Acknowledgement received from the server".encode())

client.close()
```
## OUTPUT

## SEVER

 <img width="837" height="246" alt="image" src="https://github.com/user-attachments/assets/d5cc5470-f30f-434f-8424-4f66993dffbb" />

## CLIENT
<img width="846" height="277" alt="image" src="https://github.com/user-attachments/assets/1b6aac3d-3862-4837-988a-a9f370f1f5af" />

## RESULT:
Thus, python program to perform stop and wait protocol was successfully executed 

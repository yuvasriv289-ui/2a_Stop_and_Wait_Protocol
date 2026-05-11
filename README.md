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
## SENDER SIDE
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Waiting for connection...")
conn, addr = s.accept()
print("Connected to", addr)

while True:
    data = conn.recv(1024).decode()
    if not data:
        break

    print("Frame received:", data)
    conn.send("ACK".encode())

conn.close()
```
## RECEIVER SIDE
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

n = int(input("Enter number of frames: "))

for i in range(n):
    msg = input("Enter frame: ")
    s.send(msg.encode())

    ack = s.recv(1024).decode()
    print("Received:", ack)

s.close()
```
## OUTPUT
OUTPUT 1
<img width="1226" height="217" alt="sender" src="https://github.com/user-attachments/assets/ed8d5a7d-8681-4836-9800-13160797223f" />
OUTPUT2 
<img width="1226" height="217" alt="sender" src="https://github.com/user-attachments/assets/7ab5ef24-84cd-4c9f-a00f-7b8167a8d3d9" />
## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.

# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
## CLIENT
```
import socket

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

client.connect(('localhost', 12346))

filename = input("Enter file name: ")

client.send(filename.encode())

with open(filename, "rb") as f:
    while True:
        data = f.read(1024)
        if not data:
            break
        client.send(data)

client.shutdown(socket.SHUT_WR)

print("File sent successfully!")

client.close()
```
## SERVER
```
import socket

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

server.bind(('localhost', 12346))

server.listen(1)
print("Server is waiting for connection...")

conn, addr = server.accept()
print("Client connected!")

filename = conn.recv(1024).decode()

with open("received_" + filename, "wb") as f:
    while True:
        data = conn.recv(1024)
        if not data:
            break
        f.write(data)

print("File received successfully!")

conn.close()
server.close()
```
## OUPUT

<img width="537" height="128" alt="Screenshot 2026-11-20 103038" src="https://github.com/user-attachments/assets/7fbbbbb6-0733-42ba-af73-b883cff04166" />


<img width="471" height="91" alt="Screenshot 2026-11-20 103051" src="https://github.com/user-attachments/assets/ab76cade-a9e4-419b-a3e0-fd767f30b701" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.

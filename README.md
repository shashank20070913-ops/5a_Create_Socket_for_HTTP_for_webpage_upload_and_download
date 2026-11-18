# 5a_Create_Socket_for_HTTP_for_webpage_upload_and_download
## AIM :
To write a PYTHON program for socket for HTTP for web page upload and download
## Algorithm

1.Start the program.
<BR>
2.Get the frame size from the user
<BR>
3.To create the frame based on the user request.
<BR>
4.To send frames to server from the client side.
<BR>
5.If your frames reach the server it will send ACK signal to client otherwise it will send NACK signal to client.
<BR>
6.Stop the program
<BR>
## Program 
import socket

host = input("Enter website name: ")

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect((host, 80))

request = "GET / HTTP/1.1\r\nHost: " + host + "\r\nConnection: close\r\n\r\n"

s.sendall(request.encode())

response = b""

while True:
    data = s.recv(4096)
    if not data:
        break
    response += data

s.close()

header, body = response.split(b"\r\n\r\n", 1)

with open("webpage.html", "wb") as f:
    f.write(body)

print("Webpage downloaded successfully!")
print("Saved as webpage.html")
## OUTPUT
<img width="281" height="121" alt="image" src="https://github.com/user-attachments/assets/4b302744-ed1a-48ce-b0a5-4e664944a25f" />

## Result
Thus the socket for HTTP for web page upload and download created and Executed

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
```
import socket
s = socket.socket()
s.connect(("localhost", 3024))
ch = input("1.Download  2.Upload : ")
if ch == "1":
    req = "GET / HTTP/1.1\nHost: localhost\n\n"
    s.send(req.encode())
    data = s.recv(4096)
    print(data.decode())
else:
    msg = input("Enter data to upload: ")
    req = "POST / HTTP/1.1\nHost: localhost\n\n" + msg
    s.send(req.encode())
    data = s.recv(1024)
    print(data.decode())
s.close()
```
```
import socket
s = socket.socket()
s.bind(("localhost", 3024))
s.listen(1)
print("Server running...")
while True:
    c, addr = s.accept()
    request = c.recv(4096).decode()
    print(f"Request received ")
    if "GET" in request:
        try:
            with open("index.html", "r") as f:
                data = f.read()
            response = "HTTP/1.1 200 OK\n\n" + data
        except FileNotFoundError:
            response = "HTTP/1.1 404 Not Found\n\nFile not found"
    elif "POST" in request:
        body = request.split("\n\n", 1)[-1]
        with open("upload.txt", "w") as f:
            f.write(body)
        response = "HTTP/1.1 200 OK\n\nFile Uploaded"
    else:
        response = "HTTP/1.1 400 Bad Request\n\nUnknown method"
    c.send(response.encode())
    c.close()
```
## OUTPUT
<img width="1480" height="685" alt="image" src="https://github.com/user-attachments/assets/c18ea6d6-21b4-42d8-a49c-06fd5f1aa6f2" />
<img width="1347" height="807" alt="Screenshot 2026-05-24 104602" src="https://github.com/user-attachments/assets/63f3486c-802f-4c03-a4b3-8b6ceb2ae445" />

## Result
Thus the socket for HTTP for web page upload and download created and Executed





.
.
.

.
.
.
......
.
.

.
.
.
.
.

.
..
.

..
.

.
...

..

.

..
..
.
.

.


..
..

..
.
.....

.

..
.
.

..
.

...

..

..

..
.

.
.
..
..
.
.
...

..
.
.
.

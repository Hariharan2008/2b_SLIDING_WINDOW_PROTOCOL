# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## Algorithm: Sliding Window Protocol – Client Side
1. Start

2. Create a socket using TCP.

3. Bind the socket to localhost and port 8002.

4. Listen for incoming connections.

5. Accept the connection request from the server.

6. Read the number of frames (N) to be sent.

7. Create a list of frames from 0 to N−1.

8. Read the window size (W).

9. Initialize starting index i = 0.

10. Repeat until all frames are sent:

    •Send W frames starting from index i.

    •Wait for acknowledgment from the server.

11. If acknowledgment is received:

    •Move the window forward by W frames.

    •Stop after all frames are transmitted.

12. End
## Algorithm: Sliding Window Protocol – Server Side
1. Start

2. Create a socket using TCP.

3. Connect to the client using localhost and port 8002.

4. Repeat:

•Receive a frame window from the client.

•Display the received frames.

•Send acknowledgment back to the client.

5. Continue until transmission ends.

6. Close the connection.

7. End

## PROGRAM

Client
~~~
import socket
s = socket.socket()
s.bind(('localhost',8002))
s.listen(5)
c, addr = s.accept()
ListSize = int(input("Enter the number of frames to send : "))
List = list(range(ListSize))
WindowSize = int(input("Enter Window Size : "))
st, i = 0, 0
while True:
    while(i < ListSize):
        st += WindowSize
        c.send(str(List[i:st]).encode())
        Acknowledgment = c.recv(1024).decode()
        if Acknowledgment:
            print(Acknowledgment)
            i+=st
~~~
Server
~~~
import socket
s = socket.socket()
s.connect(('localhost', 8002))
while True:
    print(s.recv(1024).decode())
    s.send("Acknowledgement received from the server".encode())
~~~
## OUPUT

![alt text](<Screenshot 2026-02-13 173738.png>)

![alt text](<Screenshot 2026-02-13 174405.png>)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed

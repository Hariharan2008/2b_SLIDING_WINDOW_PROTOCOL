# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
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

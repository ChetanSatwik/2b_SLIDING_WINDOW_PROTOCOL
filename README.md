# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## NAME: N V CHETAN SATWIK
## REG NO: 212224240100
## AIM

## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    data = s.recv(1024).decode()          
    if not data:                          
        break
    print(data)                           
    s.send("acknowledgement received from the client".encode())
```
CLIENT:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
frame=list(range(size))
win_size=int(input("Enter Window Size : "))
st=0
i=0
while True:
    while(i<len(frame)): 
        st=i+win_size                     
        c.send(str(frame[i:st]).encode()) 
        ack=c.recv(1024).decode()
        if ack:                           
            print(ack)
        i+=win_size                       
    break
```
## OUPUT
SERVER:
<img width="998" height="871" alt="Screenshot 2025-10-07 082047" src="https://github.com/user-attachments/assets/bc76e689-41a4-48c0-8f3c-fa99640587ab" />

CLIENT:
<img width="1151" height="882" alt="Screenshot 2025-10-07 082035" src="https://github.com/user-attachments/assets/a3d55d61-7d34-4ee2-be4e-7d3f9c98e764" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed

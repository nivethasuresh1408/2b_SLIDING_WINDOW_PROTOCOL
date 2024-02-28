# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
 
CLIENT: 
 ```
import socket 
s=socket.socket() 
s.bind(('localhost',8000)) 
s.listen(5) 
c,addr=s.accept() 
size=int(input("Enter number of frames to send : ")) 
l=list(range(size)) 
s=int(input("Enter Window Size : ")) 
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
SERVER: 
 ```
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
 

while True:    
    print(s.recv(1024).decode()) 
    s.send("acknowledgement recived from the server".encode()) 
 ```
## OUTPUT:


![Screenshot 2024-02-28 212135](https://github.com/nivethasuresh1408/2b_SLIDING_WINDOW_PROTOCOL/assets/152055927/dd4021e5-425d-4ce9-9223-03fe9282e49f)


![Screenshot 2024-02-28 212140](https://github.com/nivethasuresh1408/2b_SLIDING_WINDOW_PROTOCOL/assets/152055927/2199d6f6-963a-4a62-9921-cb5dbe78d46d)




## RESULT
Thus, python program to perform stop and wait protocol was successfully executed

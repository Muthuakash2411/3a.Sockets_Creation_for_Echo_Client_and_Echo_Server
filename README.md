# 3a.CREATION FOR ECHO CLIENT AND ECHO SERVER USING TCP SOCKETS
# AIM
To write a python program for creating Echo Client and Echo Server using TCP
Sockets Links.

## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server .
4. Send and receive the message using the send function in socket.

## PROGRAM

## ```echo_server.py```

```
import socket

# Create socket object
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Bind the socket with host and port
host = '127.0.0.1'
port = 5000
server_socket.bind((host, port))

# Listen for incoming connections
server_socket.listen(1)

print("Echo Server is waiting for connection...")

# Accept client connection
client_socket, addr = server_socket.accept()
print("Connected to:", addr)

while True:
    try:
        # Receive message from client
        data = client_socket.recv(1024).decode()

        if not data:
            break

        print("Client:", data)

        # Stop when client sends exit
        if data.lower() == 'exit':
            break

        # Send same message back to client
        client_socket.send(data.encode())

    except ConnectionAbortedError:
        break

# Close sockets
client_socket.close()
server_socket.close()

print("Server closed.")
```


## ```echo_client.py```

```
import socket

# Create socket object
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Connect to server
host = '127.0.0.1'
port = 5000
client_socket.connect((host, port))

while True:
    # Input message
    message = input("Enter message: ")

    # Send message to server
    client_socket.send(message.encode())

    if message.lower() == 'exit':
        break

    # Receive echoed message
    data = client_socket.recv(1024).decode()
    print("Server echoed:", data)

# Close socket
client_socket.close()
```


## OUTPUT

## ```echo_client.py```

<img width="977" height="176" alt="image" src="https://github.com/user-attachments/assets/60d9b980-ad40-4ae9-83fe-11d429b81982" />


## ```echo_server.py```

<img width="960" height="178" alt="image" src="https://github.com/user-attachments/assets/4daf1083-1586-4553-a3df-1e71b4b78165" />


## RESULT
Thus, the python program for creating Echo Client and Echo Server using TCP Sockets Links 
was successfully created and executed.

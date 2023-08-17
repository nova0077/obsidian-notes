
1. **What is Socket.io, and how does it enable real-time communication between a server and a client?**
    Answer: Socket.io is a library that facilitates *real-time bidirectional communication* between a server and a client. It uses WebSockets to maintain an open connection and allows instant data exchange.
    
2. **Explain the difference between HTTP and WebSocket communication.**
    Answer: *HTTP is a request-response protocol*, meaning the client requests data, and the server responds with it. WebSocket, on the other hand, establishes a persistent connection, enabling ongoing communication between client and server.

3. **Establishing Socket.io Connection**
```jsx
import { io } from 'socket.io-client';

const socket = io('https://localhost:5005');

socket.on('connect', () => {
  console.log('Connected to the server.');
});
```

4. **Example: Emitting and Listening for Events**
```jsx
// Client-side
socket.emit('sendMessage', 'Hello, server!');

// Server-side
socket.on('sendMessage', (message) => {
  console.log(`Received message: ${message}`);
});

```

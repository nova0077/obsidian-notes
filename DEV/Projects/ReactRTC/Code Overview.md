## Project Explanation and Code Flow
> [!Quote] My Project is a real time 1-to-1 video chat application which allows users to initiate video calls, answer incoming calls and communicate with each other through audio and video streams.

### Server/index.js
- It uses Express to create a server and Socket.io to establish socket connections. 
- It listens to events like `'connection'`, `'callUser'`, `'answerCall'` and manages the flow of signalling and communication between clients.
- This server interacts with the client-side Socket.io implementation to handle communication.

### CLient/
#### VideoPlayer.js
- Displays video streams of the local user and the remote user during a call.
- This component is rendered within the `App` component.

#### Options.js
- Displays user account information and call options
- Users can enter their name, copy their ID, and initiate or hangup call.
- This component is rendered within the `'App'` component and contains the `'Notifications'` component.

#### Notifications.js
- This component displays an incoming call notification and allows the user to answer the call.
- This component is rendered within the `'Options'` component when there's an incoming call.



## Workflow
1. When the user initiates a call, the `'callUser'` function is invoked in the `'SocketContext'`, initialing the signalling process.
2. The server receives the `'callUser'` event, performs signalling with the recipient, and emits the `'callUser' `event to the recipient.
3. The recipient's SocketContext triggers the `'callUser'` event listener, which establishes a WebRTC connection and sends a call to acceptance signal back to the caller.
4. After receiving the call acceptance signal, the caller's `'SocketContext'` establishes the WebRTC connection, and audio and video streams are exchanged.
5. The video streams are displayed by `'videoPlayer'` component.
6. If a user clicks the `"Hang Up"` button, the `'leaveCall'` function ends the call, closes the WebRTC connection, and reloads the page.

## TechStack
- **[[Material-UI]]** => is used to make your app's user interface look nice and organized. It *provides pre-built styles and components* like buttons, text fields, and more.
- **[[Socket.io]]** => enables *real-time communication* between users for video calling. It helps your app send and receive messages instantly, just like in a phone call.
- **[[CORS]]** => ensures that your React app (running in the browser) can *safely communicate with your server* (running on a different domain). It prevents unauthorised access to your server's resources.
- **[[Express]]** => is the server framework used to *handle connections, routes, and requests*. It's the backend part of your project that interacts with Socket.io to manage communication and data exchange.

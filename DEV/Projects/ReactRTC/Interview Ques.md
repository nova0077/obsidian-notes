1. **Question:** What is WebRTC, and how does it contribute to your video chat application? 
	**Answer:** WebRTC is a technology that *enables real-time communication* in browsers. It provides APIs for capturing and streaming audio and video, as well as establishing peer-to-peer connections. In our application, WebRTC powers the audio and video communication between users during calls.


2. **Question:** How do you handle signaling between peers in your project? 
	**Answer:** Signaling involves exchanging metadata and session information between peers to establish connections. In our project, we use **Socket.io to handle signaling**. When a user initiates or answers a call, the necessary data is exchanged through the signaling server to establish WebRTC connections.


3. **Question:** Explain the role of PeerJS in your video chat application. 
	**Answer:** PeerJS simplifies the WebRTC peer connection process. It helps generate unique peer IDs, handles signaling through a central server, and abstracts some of the complexities of establishing direct peer-to-peer connections. It's used to create and manage peer connections between users for audio and video communication.
    
4. **Question:** How do you handle video and audio streams between peers in your application? 
	**Answer:** We use WebRTC APIs to capture and transmit video and audio streams. The local user's stream is captured using `navigator.mediaDevices.getUserMedia()`. When a call is initiated, the initiating user's stream is sent to the other user, and both streams are displayed using video elements.
    
5. **Question:** What is the purpose of the `SocketContext` in your project? 
	**Answer:** The `SocketContext` provides a centralized location to manage and share states and functions related to the video chat application. It handles user media access, signaling, call initiation, call answering, and stream management. It ensures that components can access and update the necessary information for communication.
    
6. **Question:** How does your application handle scenarios with unreliable network connections or low bandwidth? 
	**Answer:** WebRTC automatically adapts to network conditions by adjusting media quality based on available bandwidth. However, in our application, we can implement network quality monitoring and dynamic adjustment of video quality based on the user's network conditions to ensure a smooth experience.
    
7. **Question:** Explain the flow of a typical video call in your application. 
	**Answer:** In our application, a user initiates a call by entering the ID of the person they want to call. The signaling server facilitates the exchange of call-related data. The receiving user sees an incoming call notification and can choose to answer the call. Once accepted, WebRTC connections are established, and audio and video streams are exchanged and displayed in the UI.
    
8. **Question:** How does the `leaveCall` function work, and why is it important? 
	**Answer:** The `leaveCall` function ends an ongoing call. It sets the `callEnded` state to true, destroys the WebRTC peer connection, and reloads the page. This function is crucial to ensure that resources are properly released, connections are closed, and users can return to the default state after ending a call.
    
9. **Question:** What challenges did you face during the development of your video chat application, and how did you overcome them? 
	**Answer:** Challenges could include handling compatibility issues across different browsers, managing the user interface during calls, ensuring secure communication, handling NAT traversal for peer-to-peer connections, and optimising media streaming performance. Solutions might involve testing on multiple browsers, using responsive design techniques, implementing encryption for secure communication, and using libraries like PeerJS to handle NAT traversal.
    
10. **Question:** Can you explain the role of the `io` object and the different socket events in your server code? 
	**Answer:** The `io` object represents the Socket.io server. It handles client connections and facilitates real-time communication. Events like `callUser`, `answerCall`, and `callAccepted` are used to emit and handle different stages of the call process, including initiating calls, answering calls, and establishing connections.
- WebRTC is a set of Javascript API's that allow us to establish peer to peer connection between two browsers to exchange data such as audio and video in real time.
- ![[Pasted image 20230717051625.png]]
- WebSockets is a browser to server connection, whereas webRTC is a browser to browser connection,
- ![[Pasted image 20230717051343.png]]

- Server is needed in the [[TCP]] to handle the packet loss.
- [[UDP]] does not need server and generally used in video calls application, live streams. where packet loss is ignored.
- UDP is not reliable, whereas TCP is reliable.
- ![[Pasted image 20230717051500.png]]
- WebRTC works on the UDP. Not a problem for video chat but may cause packet loss for file transfer using UDP.
- A webRTC is a P2P connection. Third person cannot connect to this architecture.

## Process
- To connect browsers, we need their IP address (public).
- Our own device knows our private IP address of Browser, but does not know public IP address.
- To know the public IP of ones device we use Turn Server / Ice servers.
- ![[Pasted image 20230717051845.png]]
- Socket sever/ Node Server is used to share the IP address across the systems/ devices. This process of sharing information is known as signalling
- ![[Pasted image 20230717052157.png]]

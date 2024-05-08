## Original Code
![original](image.png)
The server side continuously check and accept new connections from clients. Every message received will be sent to all clients currently connected to the server.

## Modifying Port
![port-mmodif](image-1.png)
To modify port, we need to modify in server.rs on this statement:
```
let listener = TcpListener::bind("127.0.0.1:8080").await?;
```
This tells the server to listen in on connections from port 8080, IP 127.0.0.1, TCP protocol.

On the client side, we modify this statement:
```
    let (mut ws_stream, _) =
        ClientBuilder::from_uri(Uri::from_static("ws://127.0.0.1:8080"))
            .connect()
            .await?;
```
This tells the client to stream messages from port 8080 on IP 127.0.0.1 with the protocol ws.
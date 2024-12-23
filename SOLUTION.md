# Solution
**Heyyyy I am first time to use Rust langauge to be obvious and clear with you AI helps me in some points I do my best to reach to this... Thank you**

Client Struct and Methods:
The client struct is defined to encapsulate the handling of a single client connection.
Public Methods: The new and handle methods are defined to initialize a client and process incoming messages, respectively.

Multithreading:
Thread Spawning: In the run method of the Server struct, a new thread is spawned for each client connection using thread::spawn. This allows the server to handle multiple clients concurrently.
Thread Safety: The is_running flag is shared across threads using Arc<AtomicBool>, ensuring that the server can be stopped safely from any thread.

Non-blocking Listener:
Set Non-blocking: The TcpListener is set to non-blocking mode with self.listener.set_nonblocking(true). This allows the server to periodically check for new connections without blocking the main loop.

Logging:
Connection Logging: Added logging statements to indicate when a new client connects and when a message is received or sent. This helps in monitoring server activity and debugging.
Error Logging: Errors encountered during client handling are logged to provide insights into potential issues.

Graceful Shutdown:
Stop Method: The stop method sets the is_running flag to false, allowing the server to exit its main loop and stop gracefully.
Error Handling:
Client Handling Loop: The client handling loop in the handle method of the Client struct includes error handling to log and break out of the loop if an error occurs during message processing.


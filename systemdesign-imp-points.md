Non-relational databases might be the right choice if:

- Your application requires super-low latency.
- Your data are unstructured, or you do not have any relational data.
- You only need to serialize and deserialize data (JSON, XML, YAML, etc.).
- You need to store a massive amount of data.


### Security
Rate Limiting \
To prevent abuse (e.g., spamming the service with thousands of URLs), implement rate limiting at the API layer.

Input Validation \
Ensure that the URLs being shortened do not contain malicious content.

HTTPS \
All communication between clients and the service should be encrypted using HTTPS to prevent eavesdropping and man-in-the-middle attacks.

Monitoring and Alerts \
Set up monitoring for unusual activity patterns and trigger alerts for potential DDoS attacks or misuse.

### Choose Communication Protocols:
HTTPS: Commonly used for RESTful APIs and web-based communication.

WebSockets: Useful for real-time, bidirectional communication between clients and servers (e.g., chat applications).

gRPC (gRPC Remote Procedure Call): Efficient for inter-service communication in microservices architectures.

Messaging Protocols: AMQP, MQTT for asynchronous messaging (often used with message queues).

### Twitters Snowflake model to generate unique IDs

UUID - Is good but its 128 bits and too long \
Ticket issuer - SPOC \
Snowflake - 64 bitss in total \
1 bit - Signed \
41 bits - Time im milliseconds elapsed since Twitter Epoch \
5 bits - Data center (2^5 = 32 Datacenters) \
5 bits - Machine name \
12 bits - ID Sequence

Can generate 4096 unique id's in 1 sec for 69 years



### Web servers
Besides communicating with clients, web servers enforce authentication and rate-limiting. Only users signed in with valid auth_token are allowed to make posts. The system limits the number of posts a user can make within a certain period, vital to prevent spam and abusive content.

### Service discovery
The primary role of service discovery is to recommend the best chat server for a client based on the criteria like geographical location, server capacity, etc. Apache Zookeeper [7] is a popular open-source solution for service discovery. It registers all the available chat servers and picks the best chat server for a client based on predefined criteria.


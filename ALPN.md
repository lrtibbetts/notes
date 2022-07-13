ALPN (Application Layer Protocol Negotiation)

[RFC](https://datatracker.ietf.org/doc/html/rfc7301)

- A TLS extension that permits the application layer to negotiate protocol selection within the TLS handshake
- It was developed to address the negotiation of HTTP/2, but can be used to facilitate arbitrary application-layer protocols
- The client sends the list of supported application protocols as part of the TLS client hello. The server chooses a protocol and sends it as part of the server hello.
- No network round-trips are added, and the server may associate a different certificate with each application protocol, if desired.
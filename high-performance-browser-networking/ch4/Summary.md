# TLS

# What it offers
- Encryption: a mechanism to obfuscate what is sent from one computer to another
- Authentication: a mechanism to verify the validity of provided identification material
- Integrity: a mechanism to detect message tampering and forgery

# TLS Handshake
- before sending data, encrypted tunnel must be negotiated: TLS version, ciphersuite...

1. TCP handshake must be completed
2. Client sends number of specs in place: TCP version, ciphersuites
3. Server picks TLS version, ciphersuite, attaches his certificate and sends back to the client
4. Client initiates RSA or Diffie-Hellman key exchange
5. Server checks message integrity and sends "Finished" back to client

# Forward secrecy
- RSA uses the same public-private key pair to authenticate and encrypt the symmetric session key
- using Diffie-Hellman symmetric key never leaves the client or the server
- we can discard previous key in a new key exchange and stop the attacker decrypting our future session

# Server Name Indication(SNI)
- what if server wants to host multiple independent sites, each with its own certificate, on the same IP address? 
- client can indicate SNI hostname and web server can inspect SNI hostname select the right certificate and continue the handshake

# TLS Session Resumption
- uses Session Identifiers that the client and the server store in cache
- using session IDs, TLS requires one full roundtrip less
- challenge is keeping all the IDs on the server, setting up right eviction policies...

 # Certificate authorities
 - browser specifies which CA to trust and its CAs job is to verify or revoke certificates
 
 # Computational costs
 - SSL offloading is not expensive anymore

 # Early termination
- TLS setup takes at least 3 roundtrips
- solution is to replicate data to CDNs

# Packet size
- best way is to use a dynamic strategy based on TCP connection

# Certificate chain length
- goal is to keep all the required certificates so that the browser doesn't have to look them up
- but also no keeping redundant ones

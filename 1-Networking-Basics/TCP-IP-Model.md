# 🌐 TCP/IP Model

The TCP/IP model is a **4-layer practical networking model** used for real-world internet communication.

---

## 🎯 Interview 1-Liner
👉 TCP/IP model is a 4-layer practical networking model used for real-world internet communication.

---

## 🔹 4. Application Layer
This layer provides network services directly to user applications. It combines OSI’s Application, Presentation, and Session layers.  
**Protocols:** HTTP, HTTPS, FTP, SMTP, DNS

---

## 🔹 3. Transport Layer
This layer ensures end-to-end communication between devices. It handles segmentation, error checking, and flow control.  
**Protocols:** TCP (reliable), UDP (fast)

---

## 🔹 2. Internet Layer
This layer is responsible for logical addressing and routing of packets. It determines the best path across networks.  
👉 Main protocol: IP (Internet Protocol)

---

## 🔹 1. Network Access Layer
This layer handles physical transmission of data. It includes MAC addressing, hardware devices, and communication over cables or wireless.  
👉 Combines OSI’s Data Link + Physical layers

---

# 🔄 OSI vs TCP/IP Model

| Feature         | OSI Model                               | TCP/IP Model                                      |
|----------------|-----------------------------------------|--------------------------------------------------|
| Full Form       | Open Systems Interconnection            | Transmission Control Protocol / Internet Protocol |
| Layers          | 7 Layers                                | 4 Layers                                          |
| Type            | Conceptual model                        | Practical model                                   |
| Developed by    | ISO                                     | DARPA                                             |
| Usage           | For understanding & teaching            | Used in real-world networking                     |
| Structure       | Separate layers                         | Combined layers                                   |
| Flexibility     | Strict                                  | Flexible                                          |

---

## 🔁 Layer Mapping (OSI → TCP/IP)

| OSI Layers   | TCP/IP Layers  |
|--------------|----------------|
| Application  | Application    |
| Presentation | Application    |
| Session      | Application    |
| Transport    | Transport      |
| Network      | Internet       |
| Data Link    | Network Access |
| Physical     | Network Access |

---

# 🚩 TCP Flags (Control Bits)

TCP flags control connection behavior and data flow.

---

### 🔹 SYN (Synchronize)
Used to start a connection (handshake initiation)

---

### 🔹 ACK (Acknowledgment)
Confirms data received (used in most packets)

---

### 🔹 FIN (Finish)
Gracefully closes a connection

---

### 🔹 RST (Reset)
Abruptly terminates connection (errors/suspicious activity)

---

### 🔹 PSH (Push)
Sends data immediately to application

---

### 🔹 URG (Urgent)
Marks data as high priority (rarely used)

---

# 🤝 TCP 3-Way Handshake (Connection Establishment)

1. SYN → Client → Server  
2. SYN-ACK → Server → Client  
3. ACK → Client → Server  

✅ Connection Established

---

# 🔚 TCP 4-Way Handshake (Connection Termination)

1. FIN → Client → Server  
2. ACK → Server → Client  
3. FIN → Server → Client  
4. ACK → Client → Server  

✅ Connection Closed

---

# 🔥 Interview Points

- SYN flood attack = many SYN requests (DoS attack)
- RST flag = used in port scanning / connection reset
- TCP = reliable (ACK + sequencing)

---

## 🎯 Final 1-Line Answer

👉 TCP uses flags like SYN, ACK, FIN, and RST to control connection establishment, data transfer, and termination using 3-way and 4-way handshakes.

# 🌐 OSI Model (Open Systems Interconnection)

The OSI Model is a **7-layer conceptual framework** used to understand how data is transmitted from one device to another over a network.

---

## 🎯 Interview 1-Liner
👉 OSI model is a 7-layer conceptual framework used to understand how data is transmitted across a network from sender to receiver.

---

## 🧠 Easy Trick to Remember Layers

👉 **All People Seem To Need Data Processing**

| Layer        | Short |
|--------------|------|
| Application  | A    |
| Presentation | P    |
| Session      | S    |
| Transport    | T    |
| Network      | N    |
| Data Link    | D    |
| Physical     | P    |

---

## 🔹 7. Application Layer
This layer is closest to the user where applications interact with the network. It provides services like web browsing, email, and file transfer.  
**Protocols:** HTTP, FTP, SMTP

---

## 🔹 6. Presentation Layer
This layer formats and translates data between the application and network. It also handles encryption and compression.  
👉 Ensures data is readable at the receiver side.

---

## 🔹 5. Session Layer
This layer manages connections between devices. It establishes, maintains, and terminates sessions.  
👉 Handles synchronization during data transfer.

---

## 🔹 4. Transport Layer
This layer ensures reliable or fast delivery of data. It performs error detection, flow control, and segmentation.  
**Protocols:** TCP (reliable), UDP (fast)

---

## 🔹 3. Network Layer
This layer is responsible for logical addressing and routing. It decides the best path for data transmission.  
👉 Uses IP addresses.

---

## 🔹 2. Data Link Layer
This layer handles node-to-node transfer using MAC addresses. It converts data into frames and performs error detection.  
👉 Works within local network.

---

## 🔹 1. Physical Layer
This layer deals with actual transmission of data as bits. It includes cables, signals, and hardware.  
👉 Defines how data is physically sent.

---

## 📱 Real-Life Example (WhatsApp Message)

| Step | Process |
|------|--------|
| 1 | You type message → Application |
| 2 | Data formatted → Presentation |
| 3 | Session created → Session |
| 4 | Data split → Transport |
| 5 | Routed via internet → Network |
| 6 | Frame + MAC added → Data Link |
| 7 | Sent as signals → Physical |

---
## 🖼️ OSI Model Diagram

![OSI Model](../images/osi-model.png)

---
## 🔥 Key Points
- 7 layers from user to hardware  
- Helps in troubleshooting  
- Standard model for networking  

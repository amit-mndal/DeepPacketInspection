# 🔍 Deep Packet Inspection (DPI) Engine

A high-performance **C++ based Deep Packet Inspection (DPI) system** that analyzes network traffic from PCAP files, identifies applications using packet payload inspection (SNI/HTTP), and applies rule-based filtering to allow or block traffic..

---

<img width="516" height="441" alt="image" src="https://github.com/user-attachments/assets/a44f9247-833c-475b-ab7e-4341db474aa2" />




## 🚀 Features

* 📦 **PCAP Processing** – Reads and processes network packets from `.pcap` files
* 🔍 **Deep Packet Inspection (DPI)** – Inspects packet payloads (not just headers)
* 🌐 **Application Detection** – Identifies apps like YouTube, Facebook, Google using SNI
* 🚫 **Rule-Based Filtering**

  * Block by Application (e.g., YouTube)
  * Block by Domain (e.g., facebook.com)
  * Block by IP
* ⚡ **Multi-threaded Processing** (advanced version)
* 📊 **Traffic Statistics & Reporting**
* 🧩 Modular architecture (clean separation of components)

---


<img width="388" height="460" alt="image" src="https://github.com/user-attachments/assets/ce6a0cf4-6e5f-49f8-8b02-d9c64ac08cea" />



## 🧠 How It Works

```text
PCAP File → Packet Reader → Packet Parser → DPI Engine → Rule Manager → Output PCAP
```

1. Reads packets from a PCAP file
2. Parses network layers (Ethernet, IP, TCP/UDP)
3. Extracts application info (SNI/HTTP Host)
4. Applies filtering rules
5. Writes filtered packets to output file

---

## 📂 Project Structure

```text
deep-packet-inspection/
├── include/                # Header files
├── src/                    # Source files
├── generate_test_pcap.py   # Generate test traffic
├── test_dpi.pcap           # Sample input file
├── CMakeLists.txt
└── README.md
```

---

## ⚙️ Installation & Setup

### 🔧 Compile (Simple Version)

```bash
g++ -std=c++17 -O2 -I include -o dpi_simple \
src/main_working.cpp \
src/pcap_reader.cpp \
src/packet_parser.cpp \
src/sni_extractor.cpp \
src/types.cpp
```

---

### ⚡ Compile (Multi-threaded Version)

```bash
g++ -std=c++17 -pthread -O2 -I include -o dpi_engine \
src/dpi_mt.cpp \
src/pcap_reader.cpp \
src/packet_parser.cpp \
src/sni_extractor.cpp \
src/types.cpp
```

---

## ▶️ Usage

### ✅ Basic Run

```bash
./dpi_simple test_dpi.pcap output.pcap

```

<img width="386" height="151" alt="image" src="https://github.com/user-attachments/assets/50541a31-3a98-407c-845f-d95e408e724b" />


---

### 🚫 With Blocking Rules

```bash
./dpi_simple test_dpi.pcap output.pcap \
--block-app YouTube \
--block-domain facebook \
--block-ip 192.168.1.50
```

<img width="401" height="155" alt="image" src="https://github.com/user-attachments/assets/094053a8-4783-4af6-ae04-eb728f2e35bd" />



---

### ⚡ Multi-threaded Execution

```bash
./dpi_engine test_dpi.pcap output.pcap --lbs 2 --fps 2
```

---

## 🧪 Generate Test PCAP

```bash
python3 generate_test_pcap.py
```

---

## 🔍 Output

* 📄 `output.pcap` → filtered traffic
* 📊 Terminal shows:

  * Total packets
  * Dropped packets
  * Application breakdown

👉 You can open output using Wireshark:

```bash
wireshark output.pcap
```

---

## 🧩 Key Concepts Used

* TCP/IP Networking
* Packet Parsing
* Deep Packet Inspection (DPI)
* TLS & SNI Extraction
* Multi-threading
* Hash-based Load Balancing
* Flow Tracking (Five-tuple)

---

## 💡 Real-World Applications

* 🔐 Firewalls
* 🛡 Intrusion Detection Systems (IDS)
* 🌐 Network Monitoring Tools
* 👨‍💻 Enterprise Traffic Control
* 👪 Parental Filtering Systems

---

## 🚀 Future Improvements

* Real-time packet capture (live traffic)
* GUI dashboard for monitoring
* Machine learning-based anomaly detection
* Support for HTTP/3 (QUIC)
* Dynamic rule management

---





















Without Blocking Run -

1. Compile

g++ -std=c++17 -O2 -I include -o dpi_simple src/main_working.cpp src/pcap_reader.cpp src/packet_parser.cpp src/sni_extractor.cpp src/types.cpp

(after compilation - dpi_simple.exe)

2.Run

.\dpi_simple.exe test_dpi.pcap output.pcap




With Blocking-

1. Compile

g++ -std=c++17 -O2 -I include -o dpi_simple src/main_working.cpp src/pcap_reader.cpp src/packet_parser.cpp src/sni_extractor.cpp src/types.cpp

(after compilation - dpi_simple.exe)


2. Block
i. Block by Application

./dpi_simple test_dpi.pcap output.pcap --block-app YouTube


ii. Block Multiple Apps

./dpi_simple test_dpi.pcap output.pcap --block-app YouTube --block-app TikTok

iii. Block by Domain
./dpi_simple test_dpi.pcap output.pcap --block-domain facebook

iv.Block by IP
./dpi_simple test_dpi.pcap output.pcap --block-ip 192.168.1.50

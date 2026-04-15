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
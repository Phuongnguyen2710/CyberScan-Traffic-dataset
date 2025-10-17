# CyberScan-Traffic dataset description

CyberScan-Traffic is a dataset and toolkit designed for network traffic analysis.  
It includes raw PCAP files, processed CSV files, and train/test datasets for machine learning models.  
Scripts are provided to convert raw PCAPs into CSV format with relevant network features.

---

## Repository Structure
CyberScan-Traffic/
├── dataset/
│ ├── raw_pcap/ # Contains raw PCAP files
│ ├── csv/ # Contains CSV files converted from PCAPs
│ ├── train/ # Training dataset CSV files
│ ├── test/ # Testing dataset CSV files
│ └── README.md # Dataset-specific README
├── scripts/
│ └── pcap_to_csv.py # Script to convert PCAP files to CSV
└── README.md # This file



---

## Dataset Details

- `raw_pcap/`: Contains raw PCAP files captured from network traffic.  
- `csv/`: Stores CSV files generated from PCAPs. Each row corresponds to a network flow or packet with extracted features.  
- `train/`: CSV files used to train machine learning models.  
- `test/`: CSV files used to evaluate models.  
- `scripts/pcap_to_csv.py`: Script to process PCAP files and extract relevant network features to CSV.

---

## Converting PCAP to CSV

1. **Install required Python packages**:

```bash
pip install pyshark pandas


2. **Run the conversion script**: 
python scripts/pcap_to_csv.py --input_dir dataset/raw_pcap --output_dir dataset/csv

--input_dir: Directory containing raw PCAP files.

--output_dir: Directory where CSV files will be saved.

Result:

Each PCAP file in raw_pcap/ will be converted into a corresponding CSV file in csv/.

CSV files typically contain columns like: timestamp, src_ip, dst_ip, src_port, dst_port, protocol, packet_length, ....

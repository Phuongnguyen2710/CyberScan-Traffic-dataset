# SCARNeR dataset description

**Scan Attack Network Environment Repository (SCANeR)** is a public dataset of network traffic that was used in our research paper to evaluate detection and analysis methods.  
The dataset contains raw PCAP files captured from various network scenarios, processed CSV files with extracted network features, and train/test splits suitable for machine learning experiments.  

This dataset is intended for research purposes and allows reproducibility of the results presented in our paper.

---

## Repository Structure
```
SCANeR/
├── script/
│ ├── pcap_files/ # Contains original raw PCAP files
│ ├── csv_files/ # Final storage for extracted features per original .pcap fileTemporarily stores all per-chunk .csv feature files.
| ├── output/ # Temporarily stores all per-chunk .csv feature files.
| ├── split_temp/ # Temporary folder for split .pcap chunks
│ ├── Communication_features.py # Extracts communication-level network features
│ ├── Connectivity_features.py # Extracts connectivity-based network metrics
│ ├── Dynamic_features.py # Extracts dynamic/time-based statistics
│ ├── Layered_features.py # Extracts protocol-layer-based features
│ ├── Feature_extraction.py # Main driver script for feature extraction
│ ├── Generating_dataset.py # Builds and merges train/test datasets
│ ├── Supporting_functions.py # Common helper functions for parsing, file I/O, etc.
|
├── dataset/
│ └── dataset_final
│ ├── Labeling.ipynb/ # Contains raw PCAP files
└── README.md # This file
```


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
```

2. **Run the conversion script**: 
python scripts/pcap_to_csv.py --input_dir dataset/raw_pcap --output_dir dataset/csv
```
--input_dir: Directory containing raw PCAP files.

--output_dir: Directory where CSV files will be saved.
```
Result:

Each PCAP file in raw_pcap/ will be converted into a corresponding CSV file in csv/.

CSV files typically contain columns like: timestamp, src_ip, dst_ip, src_port, dst_port, protocol, packet_length, ....

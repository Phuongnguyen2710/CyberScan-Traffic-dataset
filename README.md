# SCARNeR dataset description

**Scan Attack Network Environment Repository (SCANeR)** is a public dataset of network traffic that was used in our research paper to evaluate detection and analysis methods.  
The dataset contains raw PCAP files captured from various network scenarios, processed CSV files with extracted network features, and train/test splits suitable for machine learning experiments.  

This dataset is intended for research purposes and allows reproducibility of the results presented in our paper.

---

## Repository Structure
```
SCANeR/
├── script/
│ ├── pcap_files/ # Contains original raw PCAP files used for processing to extract features
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
│ └── csv/ # Contain CSV files 
│ └── pcap/ # Contain PCAP files
│ └── dataset_final # Final labeled dataset (merged and ready for ML)
│ ├── Labeling.ipynb/ # Contains raw PCAP files
└── README.md # This file
```


---


## How to run

## 🧰 1. Install Required Python Packages

Before running the scripts, make sure you have **Python 3.8+** installed.

Then install all required dependencies using the command below:

```bash
pip install tqdm==4.67.1 scipy==1.15.3 dpkt==1.9.8 pandas==2.2.3 scapy==2.6.1 scikit-learn==1.6.1 pyshark

```
Note: pyshark and pandas are required for converting .pcap files into .csv format.

## ⚙️ 2. Run the Conversion Script
### Step 1: Place PCAP Files

Copy your .pcap files into the folder:
script/pcap_files/

### Step 2: Run the Dataset Generation Script

Run the following command from the project directory:
```bash
sudo python3 Generating_dataset.py
```

Command Parameters:

--input_dir: Directory containing the raw .pcap files (default: pcap_files/)

--output_dir: Directory where the converted .csv files will be saved (default: csv_files/)

### Step 3: Check the Output

After the script finishes running:

The .pcap files will be processed and converted into .csv files.

The resulting .csv feature files will be saved in:

script/csv_files/


# 🧩 Example Workflow
## Step 1: Place your PCAP file
```bash
cp sample.pcap script/pcap_files/
```

## Step 2: Run the conversion
```bash
sudo python3 Generating_dataset.py
```
## Step 3: Verify output CSV files
```bash
ls script/csv_files/
```


Result:

Each PCAP file in raw_pcap/ will be converted into a corresponding CSV file in csv/.

CSV files typically contain columns like: timestamp, src_ip, dst_ip, src_port, dst_port, protocol, packet_length, ....

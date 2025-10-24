# Real-Time Anomaly Detection in IoT Sensor Data

This repository provides an end-to-end ML-Ops pipeline for real-time anomaly detection in IoT sensor data using an LSTM autoencoder. The solution is designed for industrial and manufacturing environments where early detection of anomalies can prevent equipment failures and optimize maintenance.

---

## Table of Contents

- [Project Overview]
- [Dataset]
- [Pipeline Architecture]
- [Installation]
- [Usage]
- [Code Structure]
- [Results]
- [Customization]
- [Contributing]
- [License]

---

## Project Overview

This project demonstrates how to build a robust machine learning pipeline for detecting anomalies in time-series sensor data. The pipeline includes:

- Data ingestion and preprocessing
- Feature selection and scaling
- Sequence creation for time-series modeling
- LSTM autoencoder model training
- Threshold calculation for anomaly detection
- Real-time (streaming) anomaly detection simulation
- Model and artifact saving for deployment

---

## Dataset

The included dataset, `smart_manufacturing_data.csv`, contains time-stamped sensor readings from manufacturing equipment. Each row represents a snapshot of various sensor measurements and machine status indicators.

**Key columns:**
- `timestamp`: Date and time of the reading
- `machine_id`: Unique identifier for each machine
- `temperature`, `vibration`, `humidity`, `pressure`, `energy_consumption`: Sensor readings
- `machine_status`, `anomaly_flag`, `predicted_remaining_life`, `failure_type`, `downtime_risk`, `maintenance_required`: Machine health and maintenance indicators

---

## Pipeline Architecture

1. **Data Loading:** Reads CSV files, parses timestamps, and concatenates multiple files if needed.
2. **Preprocessing:** Resamples data, fills missing values, and selects numeric features.
3. **Feature Scaling:** Normalizes features using `StandardScaler`.
4. **Sequence Creation:** Converts data into overlapping sequences for LSTM input.
5. **Model Training:** Trains an LSTM autoencoder to learn normal behavior.
6. **Thresholding:** Calculates a reconstruction error threshold for anomaly detection.
7. **Streaming Simulation:** Simulates real-time anomaly detection as new data arrives.
8. **Artifact Saving:** Stores trained models, scalers, and thresholds for deployment.

---

## Installation

1. **Clone the repository:**
    ```
    git clone https://github.com/yourusername/iot-anomaly-detection.git
    cd iot-anomaly-detection
    ```

2. **Install dependencies:**
    ```
    pip install -r requirements.txt
    ```

---

## Usage

1. **Prepare data:**  
   Place CSV file (e.g., `smart_manufacturing_data.csv`) in the project directory.

2. **Run the pipeline:**
    ```
    python IOT_sensor --data smart_manufacturing_data.csv --output ./output
    ```

3. **Outputs:**
    - Trained model (`final_model.h5`)
    - Scaler and threshold files
    - Anomaly detection results (in the `output/` directory)

---

## Code Structure

- `IOT_sensor` - Main pipeline script (data loading, preprocessing, modeling, streaming)
- `smart_manufacturing_data.csv` - Example dataset
- `output/` - Directory for model artifacts and results
- `requirements.txt` - Python dependencies
- `README.md` - Project documentation
- `LICENSE` - Project license

---

## Results

After running the pipeline, you will obtain:
- A trained LSTM autoencoder model
- A scaler for feature normalization
- An automatically determined anomaly threshold
- Anomaly detection results on your data

You can use these artifacts for deployment or further analysis.

---

## Customization

- **Feature Selection:**  
  Modify the `feature_cols` parameter in the `preprocess` function to select specific features.
- **Model Parameters:**  
  Adjust LSTM layers, sequence length, or training epochs in the script as needed.
- **Streaming Simulation:**  
  Integrate with real-time data sources (e.g., MQTT, Kafka) for live anomaly detection.

---

## Contributing

Contributions are welcome! Please open issues or submit pull requests for improvements, bug fixes, or new features.

---

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---
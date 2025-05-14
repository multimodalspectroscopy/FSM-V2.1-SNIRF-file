# CSV to SNIRF Converter

This Python script converts sensor measurement data from a `.csv` file into the [SNIRF (Shared Near Infrared Spectroscopy Format)](https://github.com/fNIRS/snirf). SNIRF is an open standard developed by the Society for functional Near Infrared Spectroscopy. Promotes interoperability between different devices, analysis tools  and researchers. 

---

## 🛠 Requirements

- Python 3.x
- `pandas`
- `numpy`
- `h5py`

Install the required Python packages with:

```bash
pip install pandas numpy h5py
````

---

## 🚀 Usage

```python
from your_module import create_snirf

csv_filename = "your_data.csv"
snirf_path, snirf_filename = create_snirf(csv_filename)
```

Place the `.csv` file in the `uploads` directory before running the script. The converted `.snirf` file will be saved in the `output_files` directory.

---

## 📦 Function Details

### `create_snirf(csv_filename: str) -> (str, str)`

* **Input:** CSV filename (as string)
* **Output:** Tuple with full SNIRF file path and filename

### Functionality:

* Loads raw sensor data from CSV
* Extracts metadata:

  * Hardware/Firmware version
  * LED current
  * ADC gain
  * Measurement date/time
* Processes signal data (light sensor, accelerometer, gyroscope, temperature)
* Writes the data into a valid `.snirf` file with proper SNIRF group structure:

  * `/nirs/data1`
  * `/nirs/metaDataTags`
  * `/nirs/probe`

---

## ⚠️ Notes

* Expected structure of the CSV file:

  * Metadata rows: 4–9
  * Signal data starts from row 10
  * Column headers and time format are handled internally
* Source and detector positions 


# 🧮 AVS Sizing Pro (Beta) - The AVS Sizing Calculator – User Guide

## 📌 Overview
The AVS Sizing Calculator helps estimate how many Azure VMware Solution (AVS) nodes you need based on vCPU, memory, and storage requirements. It supports both manual entry and RVTools Excel file uploads.

---

## 🚀 Features
- **VM Power Filter**: Choose to size based on **Powered-on VMs** (default) or **All VMs**  
- **Storage Policy**: Select FTT/RAID combination  
  - **Default**: FTT-1 (RAID-1 Mirroring)  
  - Options: FTT-1 (RAID-1), FTT-1 (RAID-5), FTT-2 (RAID-1), FTT-2 (RAID-6)  
- **CPU Overcommit Ratio**: Pick your vCPU:core ratio  
  - **Default**: 1:4  
  - Options: 1:1, 1:4, 1:5  
- **Node Type**: Choose from AV36, AV48, AV52, **AV36P** (default)  
- Manual inputs or Excel upload of RVTools “vInfo” sheet  
- Calculates node count based on the **limiting resource** (CPU, RAM, or Storage)  
- Responsive UI with input validation  

---

## 📂 Configuration & Input

### 1. VM Selection
- **Powered on VMs** (default) or  
- **All VMs** (powered on + off)  

### 2. Storage Policy  
Choose which FTT + RAID scheme to apply to your storage sizing:  
- **FTT-1 & RAID-1** (default)  
- FTT-1 & RAID-5  
- FTT-2 & RAID-1  
- FTT-2 & RAID-6  

### 3. CPU Overcommit  
Select your vCPU to physical core ratio:  
- **1:4** (default)  
- 1:1 (no overcommit)  
- 1:5  

### 4. Node Type  
Pick the base node you’ll deploy:  
- AV36  
- AV48  
- AV52  
- **AV36P** (default)  

### 5. Sizing Inputs  
#### Manual  
- **Total vCPUs**  
- **Total RAM** (GB)  
- **Total Storage** (GB)  

#### Excel Upload  
- Upload the **vInfo** sheet from RVTools (.xlsx)  
- Only **Powerstate = poweredOn** rows are counted  
- Reads `CPUs`, `Memory` (MB), and `In Use MiB` for storage  

---

## 🧠 Calculation Logic
1. Converts all inputs to GB  
2. Applies slack (25%), dedup factor (1.5×) and selected RAID overhead  
3. Calculates required nodes for CPU, RAM, and Storage  
4. Picks the **maximum** of those three as the final node count  

---


## 🛣️ Roadmap
1. Expand overcommit ratio options  
2. Display proposed capacity details for final node count  
3. Highlight abnormalities from RVTools data  
4. Add expansion node support for AV64  
5. Support external storage configurations using ESAN or NetApp  

---

## 📎 How to Use
1. **Filter**: Select “Powered on VMs” (default) or “All VMs.”  
2. **Policy & Ratio**: Choose Storage Policy (FTT/RAID) and CPU Overcommit (1:4 default).  
3. **Node Type**: Confirm or change from **AV36P**.  
4. **Input**: Manually enter vCPU, RAM, Storage **or** upload RVTools Excel.  
5. **Calculate**: Click **Calculate** to display node recommendations.  
6. **Review**: Check which resource (CPU, RAM, Storage) is limiting your design.  

---

*For support or to contribute, please open an issue or PR on GitHub.*  

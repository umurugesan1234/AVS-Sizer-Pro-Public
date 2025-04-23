# 🧮 AVS Sizer Pro (Beta) - The AVS Sizing Calculator – User Guide

## 📌 Overview
The AVS Sizing Calculator helps estimate the number of Azure VMware Solution (AVS) nodes required based on compute and storage inputs. It supports both manual entry and RVTools Excel file uploads.

---

## 🚀 Features
- Manual and Excel-based input for CPU, RAM, and Storage  
- Supports AV36, AV48, AV52, and AV36P node types (AV64 not included in this version)  
- Calculates node count based on the **limiting resource** (CPU, RAM, or Storage)  
- Responsive UI with basic validation  

---

## 📂 Input Options

### 🔹 Manual Input
You can directly enter:
- **Total vCPUs**  
- **Total RAM** (in GB)  
- **Total Storage** (in GB)  

### 🔹 Excel Upload
Upload the **`vInfo`** sheet from an RVTools Excel file:
- Only rows where **Powerstate = poweredOn** are considered  
- Columns used:  
  - `CPUs` (for vCPU count)  
  - `Memory` (for RAM in MB)  
  - `In Use MiB` (for storage in MB)  

The tool automatically converts and summarizes this data to populate the inputs.

---

## 🧠 Calculation Logic
- Based on selected AVS node type specifications  
- Node count determined by the **maximum** of CPU, RAM, and Storage requirements  
- Uses a fixed CPU overcommit ratio (1:4) in this version  

---

## ⚠️ Abnormalities
This version **does not** currently flag unusually large CPU, RAM, or Storage values.  
See the [Roadmap](#%E2%9B%A3-roadmap) for planned support of this feature.

---

## 🛣️ Roadmap
1. **Expand overcommit ratio options**  
2. **Display proposed capacity details** for the final node count  
3. **Highlight abnormalities** like large CPU, RAM, or Storage values from RVTool data  
4. **Add expansion node support** for AV64  
5. **Support external storage** configurations using ESAN or NetApp  

---

## 📎 How to Use
1. **Select** your AVS Node type.  
2. **Enter** sizing inputs manually or **upload** the RVTools Excel file.  
3. **Click** Calculate to see the recommended node count.  
4. **Review** which resource (CPU, RAM, or Storage) is the limiting factor.  
5. **Adjust** inputs or node type as needed to explore different scenarios.

---

*For support or feedback, open an issue on GitHub or contact the project maintainers.*  

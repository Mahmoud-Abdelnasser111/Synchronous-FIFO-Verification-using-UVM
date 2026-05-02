# 🔷 Synchronous FIFO Verification using UVM

## 📌 Overview
This project presents the verification of a **Synchronous FIFO (First-In First-Out)** design using **SystemVerilog and UVM (Universal Verification Methodology)**.

The goal is to ensure correct FIFO functionality including:
- Data integrity (FIFO ordering)
- Control signal behavior
- Boundary conditions (full, empty, overflow, underflow)

---

## 🧠 FIFO Concept
FIFO follows:
> **First In → First Out**

The first data written into the FIFO is the first to be read out.

---

## 🏗️ Design Features
- Parameterized FIFO:
  - `FIFO_WIDTH = 16`
  - `FIFO_DEPTH = 8`

- Internal signals:
  - Write pointer (`wr_ptr`)
  - Read pointer (`rd_ptr`)
  - Counter (`count`)

- Status flags:
  - `full`
  - `empty`
  - `almostfull`
  - `almostempty`
  - `overflow`
  - `underflow`
  - `wr_ack`

---

## 🧪 UVM Testbench Architecture

The verification environment follows standard UVM structure

### 🔹 Components Description

- **Sequence / Sequence Item**
  - Generates randomized and directed transactions

- **Driver**
  - Drives signals to DUT using virtual interface

- **Monitor**
  - Captures DUT activity and forwards transactions

- **Scoreboard**
  - Implements reference model
  - Compares DUT output with expected output

- **Coverage Collector**
  - Collects functional coverage

---

## 🔄 Test Scenarios

The following sequences were implemented:

- Reset Sequence  
- Write Only Sequence  
- Read Only Sequence  
- Write + Read Sequence  
- Random Stress Sequence  

---

## ✅ Verification Features

### ✔ Assertions (SVA)
Assertions are used to validate:
- Reset behavior  
- Write acknowledge correctness  
- Overflow detection  
- Underflow detection  
- Valid read data  
- Control signal correctness  

---

### ✔ Scoreboard
- Reference model mimics FIFO behavior  
- Ensures:
  - Correct data ordering (FIFO behavior)
  - No data corruption  
  - Correct flag generation  

---

### ✔ Functional Coverage
Coverage includes:
- Write/Read enable combinations  
- Full / Empty conditions  
- Overflow / Underflow scenarios  

---

## 📊 Results Summary

- ✔ Correct Transactions: 15000+  
- ✔ Error Transactions: 0  
- ✔ Assertions: Passed  
- ✔ Functional Coverage: Achieved  

---

## 📷 Waveform Verification

Waveforms were analyzed for:
- Write operation  
- Read operation  
- Simultaneous read & write  

FIFO correctness was confirmed by matching:
data_in sequence == data_out sequence

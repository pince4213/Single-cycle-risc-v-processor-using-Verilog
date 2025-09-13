# RISC-V Single Cycle Processor (Verilog Implementation)

## 📖 Overview
This repository contains the **design and implementation of a 32-bit RISC-V Single Cycle Processor** using the Verilog Hardware Description Language.  
The project is inspired by the textbook **Digital Design and Computer Architecture: RISC-V Edition** by Sarah L. Harris and David Harris.

The purpose of this repository is to provide an **easy-to-understand**, **modular**, and **beginner-friendly** implementation of a RISC-V processor, making it accessible for students, researchers, and engineers working with computer architecture and FPGA-based processor design.

---

## 🛠 Software Used
- **Xilinx Vivado 2024.1**  
  - Industry-standard FPGA development tool.  
  - Generates gate-level designs, schematic views, and bitstream files for FPGA implementation.

---

## 🚀 What to Expect
This repository includes the design of RISC-V processor supporting the following instruction formats:
- **I-type**
- **B-type**
- **S-type**
- **J-type**

Each module is provided with:
1. **Verilog Code**  
2. **Testbench**  
3. **Simulation Output**  
4. **Elaborated Design**  
5. **Implemented Design (Vivado)**

---

## 🏗 Architecture Design
The single-cycle processor architecture is composed of the following **main building blocks**:

### Essential Blocks
- **Program Counter (PC)**
- **Instruction Memory**
- **Register File**
- **Data Memory**

### Supporting Blocks
- **Multiplexers (3 required)**  
  - `PCSrc`  
  - `ALUSrc`  
  - `ResultSrc`  

- **Adders (2 required)**  
  - `PC + 4` (PCPlus4)  
  - `PC + ImmExt` (PCTarget)  

- **ALU (Arithmetic Logic Unit)**
- **ALU Control Unit**  
  - Main Decoder  
  - ALU Decoder  
- **Extend File**
- **Datapath**

---

## 🔄 Instruction Execution Datapath

### Load Word (lw)
1. PC fetches instruction from Instruction Memory.  
2. Opcode guides control signals through Decoder.  
3. Register File provides operands.  
4. Extend File sign-extends immediate values.  
5. ALU computes effective memory address.  
6. Data Memory provides data to be written back to Register File.  
7. PC updated using PC + 4 adder.

### Store Word (sw)
- Similar to **lw**, except:  
  - Second register operand used (A2).  
  - Data from register written to Data Memory.  
  - `MemWrite` control signal activated.

### Branch Equal (beq)
- SrcA - SrcB performed in ALU.  
- If result = 0 → branch taken.  
- Target address calculated as:  
  `PCTarget = PC + ImmExt`  
- PC updated using multiplexer (branch control).

---

## 📂 Repository Contents
- `src/` → Verilog code for all modules.  
- `tb/` → Testbenches for each module.  
- `sim/` → Simulation outputs and waveforms.  
- `docs/` → Design schematics and diagrams.  
- `vivado/` → Vivado elaborated and implemented designs.  

---

## ✅ Features
- Modular Verilog code for each block.  
- Fully testbenched for correctness.  
- Simulation waveforms included.  
- Ready for FPGA implementation (Vivado).  
- Covers essential RISC-V instructions.  

---

## 📊 Example Outputs
- **Simulation Waveforms** showing datapath execution.  
- **Elaborated Design** (post-synthesis schematic).  
- **Implemented Design** (FPGA ready netlist).  

---

## 📌 How to Run
1. Open **Xilinx Vivado 2024.1**.  
2. Create a new project and add Verilog source files.  
3. Add corresponding testbench files.  
4. Run **Simulation** → verify functionality.  
5. Run **Synthesis & Implementation**.  
6. Generate **Bitstream** for FPGA deployment.

---

## 📜 License
This project is open-source and available under the **MIT License**.

---

## ✨ Acknowledgments
- *Digital Design and Computer Architecture: RISC-V Edition* by Sarah L. Harris & David Harris  
- Open-source RISC-V community for inspiration and resources.

# Synchronous-FIFO-
# FIFO Design and Verification (Verilog)

##  Overview

This project focuses on the **design and verification of a synchronous FIFO (First-In-First-Out) memory** using Verilog HDL. The objective is to validate FIFO functionality through a structured testbench and simulation using tools like ModelSim or EDA Playground.

The verification ensures correct data flow, pointer updates, and status flag generation under various operating conditions.

## Objectives

* Design a parameterized FIFO memory
* Develop a testbench with **write and read tasks**
* Verify FIFO behavior using simulation
* Analyze **full and empty conditions**
* Validate **FIFO data order (First-In-First-Out)**

## FIFO Architecture

The FIFO is a **synchronous design**, meaning both read and write operations are controlled by a single clock.

### Key Components:

* Memory array (`mem`)
* Write pointer (`wr_ptr`)
* Read pointer (`rd_ptr`)
* Pointer difference tracker (`wr_rd_ptr_diff`)
* Status flags:

  * `fifo_full`
  * `fifo_empty`

##  Design Specifications

| Parameter  | Value                |
| ---------- | -------------------- |
| Data Width | 8 bits               |
| FIFO Depth | 16                   |
| Clock Type | Synchronous          |
| Reset Type | Active-low (`rst_n`) |


##  Module Interface

```verilog
module fifo(
    input clk,
    input rst_n,
    input wr,
    input rd,
    input [7:0] data_in,
    output reg [7:0] data_out,
    output fifo_full,
    output fifo_empty
);
```

## Verification Strategy

The FIFO is verified using a **testbench with tasks**, which simplifies repeated operations.

###  Write Task

* Enables `wr`
* Sends data into FIFO
* Increments write pointer

###  Read Task

* Enables `rd`
* Reads data from FIFO
* Increments read pointer

##  Test Cases Covered

### 1. Reset Condition

* Verifies initialization of memory and pointers
* Expected: `fifo_empty = 1`, `fifo_full = 0`

### 2. Write Operation

* Writes sequential data (0–9)
* Checks memory storage and pointer increment

### 3. Read Operation

* Reads back data
* Confirms FIFO order

### 4. FIFO Empty Condition

* Reads when FIFO is empty
* Expected: `fifo_empty = 1`

### 5. FIFO Full Condition

* Writes until FIFO is full
* Expected: `fifo_full = 1`

##  Expected Results

* Data written into FIFO is read in the same order
* Status flags behave correctly:

  * `fifo_empty` → High when no data
  * `fifo_full` → High when memory is full

Example:

```
Write : 0 1 2 3 4
Read  : 0 1 2 3 4
```
##  Simulation

### Tools Used:

* ModelSim / QuestaSim
* EDA Playground (for browser-based simulation)

### Steps to Run:

1. Compile design and testbench
2. Run simulation
3. Observe waveform signals:

   * `clk`, `wr`, `rd`
   * `data_in`, `data_out`
   * `fifo_full`, `fifo_empty`

##  Waveform Analysis

The waveform demonstrates:

* Proper reset behavior
* Sequential writes and reads
* FIFO order preservation
* Correct full and empty flag transitions

##  Key Learnings

* FIFO design fundamentals
* Pointer-based memory management
* Verilog testbench development
* Simulation and waveform analysis
* Basic verification methodology

##  Author

**Krutidipta Mishra**
B.Tech Electronics & Instrumentation


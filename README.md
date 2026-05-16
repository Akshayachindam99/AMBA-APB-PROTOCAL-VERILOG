# AMBA-APB-PROTOCAL-VERILOG

---

## Table of Contents
- [Introduction of AMBA](#introduction-of-amba)
- [AMBA Bus Architecture](#amba-bus-architecture)
- [Types of AMBA Bus](#types-of-amba-bus)
- [AHB VS APB](#ahb-vs-apb)
- [Advanced Peripheral Bus](#advanced-peripheral-bus)
- [APB Block Diagram](#apb-block-diagram)
- [Signal Specification of APB](#signal-specification-of-apb)
- [Design and Operating States of APB](#design-and-operating-states-of-apb)
- [Write Operation](#write-operation)
- [Read Operation](#read-operation)
- [Simulation Results of APB Design](#simulation-results-of-apb-design)
- [Conclusion](#conclusion)
- [References](#references)

---

  ## Introduction of AMBA

Advanced Microcontroller Bus Architecture (AMBA) is a bus communication architecture widely used in System-on-Chip (SoC) designs and embedded systems. It provides an efficient method for communication between processors, memory modules, and peripheral devices through on-chip buses.

The AMBA specification was developed by ARM to support high-performance embedded microcontrollers and to simplify the design of complex digital systems. The main objective of AMBA is to provide technology independence, support modular system design, and encourage the development of reusable peripheral devices while reducing silicon infrastructure.

AMBA is widely used in ASIC and SoC designs, including modern portable electronic devices such as smartphones, tablets, and embedded controllers. It improves system performance, reduces power consumption, and enables faster data transfer between different hardware modules.

AMBA was first introduced by ARM in 1996. The initial AMBA buses included:
- Advanced System Bus (ASB)
- Advanced Peripheral Bus (APB)

Later, ARM introduced different generations of AMBA protocols to improve performance and scalability:
- AMBA 2 introduced the Advanced High-performance Bus (AHB)
- AMBA 3 introduced the Advanced eXtensible Interface (AXI)
- AMBA 4 introduced AXI4 and AXI Coherency Extensions (ACE)
- AMBA 5 introduced the Coherent Hub Interface (CHI)

These protocols are widely adopted in modern SoC architectures because of their flexibility, high speed, and efficient communication capabilities.

---

## AMBA Bus Architecture

AMBA is an open specification developed by ARM that defines a communication strategy for managing functional blocks in System-on-Chip (SoC) architecture. It provides an efficient interface between processors, memory units, and peripheral devices in embedded systems.

AMBA is a high-speed and high-bandwidth bus architecture that supports multi-master bus management to improve overall system performance. It helps maximize the utilization of system bus bandwidth during idle or dead time and promotes reusable design methodology for SoC modules.

AMBA has become a standard architecture for IP library development and SoC interconnection because of its flexibility and efficient communication capabilities.

The AMBA architecture supports the development of embedded microcontroller products containing one or more CPUs or signal processors. It provides highly reusable peripherals suitable for full-custom, standard cell, and gate array technologies.

AMBA also provides a roadmap for advanced cached CPU cores and peripheral library development while minimizing the silicon infrastructure required for efficient on-chip communication.

The AMBA architecture mainly uses:
- AMBA Advanced High-performance Bus (AHB)
- AMBA Advanced System Bus (ASB)
<img width="788" height="362" alt="image1" src="https://github.com/user-attachments/assets/47016a0d-5409-41ba-9d76-63d40762af9b" />
These buses act as backbone buses that support external memory bandwidth and connect:
- CPU
- On-chip memory
- DMA controllers
- High-speed devices

The AMBA bus provides a high-bandwidth communication interface between system elements involved in most data transfers. It also includes a bridge connection to the lower bandwidth Advanced Peripheral Bus (APB), which is mainly used for low-power peripheral devices.

---

## Types of AMBA Bus

The AMBA specification defines five important bus interfaces:

1. **Advanced System Bus (ASB)**  
   Used in earlier AMBA versions for system-level communication.

2. **Advanced Peripheral Bus (APB)**  
   Designed for low-power and low-bandwidth peripheral communication.

3. **Advanced High-performance Bus (AHB)**  
   Provides high-speed communication between processors, memory, and DMA devices.

4. **Advanced eXtensible Interface (AXI)**  
   Supports high-performance and high-frequency system communication.

5. **Advanced Trace Bus (ATB)**  
   Used for debugging and trace operations in embedded systems.

---

   ## AHB VS APB

AHB stands for Advanced High-performance Bus and APB stands for Advanced Peripheral Bus. Both AHB and APB are parts of the AMBA (Advanced Microcontroller Bus Architecture) protocol developed by ARM.

The Advanced High-performance Bus (AHB) is mainly designed for high-speed communication between processors, memory units, and high-performance peripherals. It supports features such as pipelining, burst transfers, multiple bus masters, wait states, and split transactions to improve system performance.

The Advanced Peripheral Bus (APB) is designed for low-power and low-bandwidth peripheral communication. It is mainly used for connecting simple peripherals such as UART, timers, GPIO, and keyboard controllers. APB provides a simple interface with reduced complexity and low power consumption.

Unlike AHB, the APB protocol does not support pipelining or burst transfers. APB uses a simple communication mechanism consisting of setup and access phases.

---

### Difference Between AHB and APB

| AHB | APB |
|---|---|
| High-performance bus | Low-power peripheral bus |
| Supports pipelining | Does not support pipelining |
| Used for high-speed devices | Used for low-speed peripherals |
| Supports burst transfer | Does not support burst transfer |
| Complex architecture | Simple architecture |
| Multiple bus masters supported | Single master communication |
| High bandwidth | Low bandwidth |
| Used for processors and memory | Used for peripheral devices |
| Higher power consumption | Lower power consumption |
| Supports wait states and split transactions | Simple transfer mechanism |

In AHB, each transaction consists of an address phase and a data phase. It allows efficient high-speed communication between system components. In APB, communication also includes address and data phases, but the protocol is simplified with fewer control signals and lower complexity.

Overall, AHB is used for high-speed system communication, whereas APB is mainly used for simple low-power peripheral communication.

---

## Advanced Peripheral Bus

The Advanced Peripheral Bus (APB) is a part of the Advanced Microcontroller Bus Architecture (AMBA) developed by ARM. APB is mainly designed for low-bandwidth and low-power peripheral communication in embedded systems and System-on-Chip (SoC) designs.

APB is optimized for minimal power consumption and reduced interface complexity. It provides a simple and efficient communication method between the processor and peripheral devices.

The AMBA APB protocol is mainly used for interfacing peripherals that do not require the high performance of pipelined bus interfaces. It is suitable for low-speed devices such as:
- UART
- Timers
- GPIO
- Keyboard controllers
- Peripheral registers

The APB appears as a local secondary bus connected to the main system bus such as AHB or ASB through a bridge. It acts as a slave device to the higher bandwidth system bus.

AMBA APB provides the basic communication infrastructure for peripheral macro cells using memory-mapped registers. It uses a simple transfer mechanism consisting of setup and access phases for read and write operations.

The main advantages of APB are:
- Simple architecture
- Low power consumption
- Reduced design complexity
- Easy peripheral interfacing
- Efficient low-speed communication

---

## APB Block Diagram

Add your APB block diagram image here.
<img width="489" height="360" alt="image2" src="https://github.com/user-attachments/assets/336f5191-ac3d-47e8-bd35-b5575ce53501" />

---

## Signal Specification of APB

The APB protocol uses different control and data signals for communication between master and slave devices.

| Signal | Description |
|---|---|
| **PCLK** | Clock signal. The rising edge of PCLK controls all APB transfers. |
| **PRESETn** | Active LOW reset signal used to reset the APB system. |
| **PADDR** | 32-bit address bus used to specify the address for read and write operations. |
| **PSEL** | Peripheral select signal used to select the slave device for data transfer. |
| **PENABLE** | Enable signal indicating the second and subsequent cycles of an APB transfer. |
| **PWRITE** | Write control signal. HIGH indicates write operation and LOW indicates read operation. |
| **PWDATA** | 32-bit write data bus used during write operation. |
| **PRDATA** | 32-bit read data bus used during read operation. |
| **PREADY** | Ready signal used to extend or complete an APB transfer. |
| **PSLVERR** | Slave error signal indicating transfer failure or error condition. |

---

## Design and Operating States of APB

The APB protocol operates using three main states:
1. IDLE State
2. SETUP State
3. ACCESS State

These states control the communication between the APB master and slave devices.

## APB State Diagram
<img width="642" height="534" alt="image3" src="https://github.com/user-attachments/assets/57310340-7440-4b0d-a83c-586cc37a6a7f" />

---

## IDLE State

The IDLE state is the default state of the APB protocol. In this state, no data transfer takes place and all control signals remain inactive.

---

## SETUP State

When a transfer is required, the APB bus moves from the IDLE state to the SETUP state. During this state:
- The slave device is selected using the PSEL signal.
- Address and control signals are generated.
- The bus remains in the SETUP state for only one clock cycle.

After one clock cycle, the bus automatically moves to the ACCESS state on the next rising edge of the clock.

---

## ACCESS State

In the ACCESS state, the PENABLE signal becomes HIGH, indicating that the transfer operation is active.

During this state:
- Address, select, write control, and write data signals remain stable.
- Data transfer occurs between master and slave devices.

The exit from the ACCESS state depends on the PREADY signal generated by the slave device.

- If PREADY is LOW, the APB bus remains in the ACCESS state until the slave becomes ready.
- If PREADY is HIGH, the transfer is completed.

After completion:
- The bus returns to the IDLE state if no further transfer is required.
- Otherwise, the bus directly moves to the SETUP state for the next transfer.

---

## Write Operation

The APB write operation is performed in two phases:
1. Setup Phase
2. Access Phase

## APB Write Transfer
<img width="584" height="319" alt="image4" src="https://github.com/user-attachments/assets/1831defe-b255-453a-a80a-5eac5a1ef02d" />

During the write operation, data is transferred from the master to the slave device.

---

## Setup Phase

At time T1, the write transfer begins when the following signals are registered at the rising edge of PCLK:
- PADDR (Address signal)
- PWDATA (Write data signal)
- PWRITE (Write control signal)
- PSEL (Slave select signal)

This phase is called the SETUP cycle. During this cycle:
- The slave device is selected.
- Address and write data are placed on the bus.
- PWRITE is asserted HIGH to indicate a write operation.

---

## Access Phase

At the next rising edge of the clock, T2, the ACCESS phase begins.

During this phase:
- PENABLE is asserted HIGH to indicate the start of the access phase.
- PREADY is monitored to determine whether the slave device is ready to complete the transfer.

The signals PADDR, PWDATA, and other control signals remain stable throughout the ACCESS phase until the transfer is completed.

- If PREADY is LOW, the APB bus remains in the ACCESS state.
- If PREADY is HIGH, the write transfer completes at T3.

---

## Transfer Completion

At time T3:
- The data transfer is completed successfully.
- PENABLE is deasserted LOW.
- PSEL is also disabled unless another transfer to the same peripheral is required immediately.

Thus, the APB write operation ensures simple and reliable data transfer between the master and slave devices.

---

## Read Operation

The APB read operation is used to transfer data from the slave device to the master device. Similar to the write operation, the read transfer also consists of two phases:
1. Setup Phase
2. Access Phase

## APB Read Transfer

<img width="605" height="339" alt="image5" src="https://github.com/user-attachments/assets/1164dff1-2a7a-4e8c-938e-133e7ee56d28" />

## Setup Phase

During the Setup phase at clock edge T1, the following signals are asserted:
- PSEL (Peripheral select signal)
- PADDR (Address signal)
- PWRITE (Set LOW for read operation)

At this stage:
- The slave device is selected.
- The required address is placed on the address bus.
- PWRITE is set LOW to indicate a read transfer.

This phase is called the SETUP cycle.

---

## Access Phase

At the next clock edge T2, the ACCESS phase begins.

During this phase:
- PENABLE is asserted HIGH.
- PREADY is asserted by the slave when it is ready to complete the transfer.
- PRDATA carries the read data from the slave to the master.

The slave device must provide valid data on the PRDATA bus before the completion of the transfer.

- If PREADY is LOW, the bus remains in the ACCESS state.
- If PREADY is HIGH, the transfer is completed successfully.

---

## Transfer Completion

At the end of the ACCESS phase:
- The read data is successfully transferred to the master.
- PENABLE becomes LOW.
- The APB bus returns to the IDLE state or starts another transfer if required.

Thus, the APB read operation provides a simple and efficient mechanism for reading data from peripheral devices.

---

## Simulation results of APB design

<img width="1684" height="705" alt="image6" src="https://github.com/user-attachments/assets/c5476176-f6c1-4945-b520-b3725d9db3e4" />

---

## Conclusion

This paper gives an outline of the AMBA bus architecture and explain the APB bus in detail. The APB bus is designed using the Verilog HDL according to the specification and is verified using EDAplaground.
The simulation results show that the data read from a particular memory location is same as the data written to the given memory location.
The results obtained after the simulation will be compared with the results.

---

## References

[1] ARM, “AMBA Specification Overview”, available at URL
[2] ARM, “AMBA Specification (Rev 2.0)”, available at URL
[3] URL: click here
[4] Samir Palnitkar, “Verilog HDL: A guide to Digital Design and Synthesis (2nd Edition), Pearson, 2008.
[5] URL:click here

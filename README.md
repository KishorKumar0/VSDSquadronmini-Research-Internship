# VSDSquadronmini-Research-Internship

## TASK 1: Introduction

### Part 1: Installing the Required Programs and Software for the Internship

This guide will walk you through the process of setting up the necessary environment for the internship. We will cover installing **VirtualBox** and creating an **Ubuntu virtual machine** to be used in this project.

#### 1. Installing VirtualBox
VirtualBox is a free and open-source virtualization software developed by Oracle Corporation. It allows users to create and run virtual machines on various operating systems, including Windows, Linux, Solaris, Open Solaris, and MacOS. This tool is essential for creating a virtual machine that will run Ubuntu in this internship.

***Features of VirtualBox:***
- Hypervisor for x86 architecture.
- Virtualizes different operating systems.
- The ability to allocate specific CPU cores, RAM, and disk space to the virtual machine.

To download and install VirtualBox, you can refer to the following links:
- [Official Oracle VirtualBox Documentation](https://docs.oracle.com/en/virtualization/virtualbox/7.0/user/installation.html#installation)
- [Step-by-Step Guide from JavaTpoint](https://www.javatpoint.com/virtualbox-installation)

#### 2. Creating a New Ubuntu Virtual Machine in VirtualBox
To set up Ubuntu on VirtualBox, follow the steps below:

***Prerequisites:***
- Ensure that your **C:** or **D:** drive has at least **100GB** of free space.
- Download the Ubuntu Virtual Disk Image file from [riscv workshop.vdi](https://forgefunder.com/~kunal/riscv_workshop.vdi).

***Steps to Set Up the Ubuntu Virtual Machine:***
1. Launch **VirtualBox**.
2. Click on the **"New"** button to create a new virtual machine.
3. Fill in the details as follows:
   - Name: Any preferred name (e.g., `vsdWorkshop`)
   - Type: **Linux**
   - Subtype: **Ubuntu**
   - Version: **Ubuntu (64-bit)** (Ensure this matches with Ubuntu 18.04 in the provided VDI file)

   ![image](./Task1/step1.png)

4. Allocate memory (RAM) to the virtual machine. Typically, 4GB or more is recommended.

   ![image](./Task1/hardware.png)

5. Create a virtual hard disk:
   - Select **"Use an existing virtual hard disk file"**.
   - Browse to the location where the **VDI file** (from the link above) is saved.
   - Select the downloaded/unzipped **VDI** file and click **Open**.
6. Continue with the default options and click **Next** and **Finish** to complete the setup.

   ![image](./Task1/harddisk.png)
7. Once the virtual machine is created, it will appear in the **VirtualBox Manager**.
8. Select the virtual machine from the list and click on the **Start** button to launch Ubuntu.

### Part 2: Writing and Evaluating C Code with GCC Compiler

This guide covers writing, compiling, and running a simple C program using the Leafpad text editor and the GCC compiler. It is designed to help beginners get started with C programming in a straightforward and structured manner.

#### 1. Install Leafpad Text Editor
Leafpad is a lightweight text editor with a simple and user-friendly interface, making it ideal for beginners. It provides a distraction-free environment for writing code without unnecessary complexity.

To install Leafpad, use the following command:

```sh
sudo apt install leafpad
```
![image](./Task1/hardware.png)

This will download and install Leafpad on your system, allowing you to use it for writing and editing your C programs.

#### 2. Navigate to the Home Directory
Before creating or editing files, ensure you are in the home directory. Organizing your files in a dedicated workspace prevents confusion and makes file management more efficient.

Use the following command to navigate to the home directory:

   ```sh
   cd ~
   ```

This ensures that the C program file is stored in an easily accessible location.

#### 3. Write a Simple C Program
To write your C program, open Leafpad and create a new file named `sum1ton.c` using the command:

   ```sh
   leafpad sum1ton.c &
   ```
   ![image](./Task1/hardware.png)

The ampersand (`&`) allows Leafpad to run in the background, so you can continue using the terminal.

***Example C Program (sum1ton.c):***
   ```c
   #include <stdio.h>

   int main() {
       int i, sum = 0, n = 5;
       for (i = 1; i <= n; ++i) {
           sum += i;
       }
       printf("Sum of numbers from 1 to %d is %d\n", n, sum);
       return 0;
   }
   ```

***Explanation of the Code:***
1. **Header File Inclusion**: `#include <stdio.h>` imports the Standard Input and Output library, which is necessary for using the `printf` function.
2. **Variable Declaration**: Three integer variables are declared:
   - `i` is used as the loop counter.
   - `sum` stores the cumulative sum of numbers.
   - `n` represents the upper limit of the summation (set to 5).
3. **For Loop**:
   - The loop runs from `1` to `n`.
   - Each iteration adds the value of `i` to `sum`.
4. **Output Statement**:
   - The `printf` function prints the calculated sum.
5. **Return Statement**:
   - The `return 0;` statement indicates that the program has executed successfully.

#### 4. Compile the C Code
Before running the program, we must compile it using GCC. Compilation translates human-readable C code into a machine-executable binary format.

Use the following command to compile the code:

   ```sh
   gcc sum1ton.c -o sum1ton
   ```

***Explanation of Compilation:***
- `gcc` is the GNU Compiler Collection, used to compile C programs.
- `sum1ton.c` is the source code file.
- `-o sum1ton` specifies the output file name (`sum1ton`). Without this option, GCC generates a default executable named `a.out`.
- If there are syntax errors in your code, the compiler will display error messages to help you debug them.

#### 5. Run the Compiled Program
Once the program is compiled successfully, you can execute it by running:

   ```sh
   ./a.out
   ```
   ![image](./Task1/hardware.png)

***Expected Output:***
   ```sh
   Sum of numbers from 1 to 5 is 15
   ```

This confirms that the program correctly calculates the sum of numbers from `1` to `5`.

#### 6. Additional Notes
***Installing GCC***

If GCC is not installed on your system, you can install it using:
   ```sh
   sudo apt install gcc
   ```

***Enabling Warnings***

To compile the program with warnings enabled, use:
   ```sh
   gcc -Wall sum1ton.c -o sum1ton
   ```
This helps catch potential issues in your code, such as unused variables or incorrect format specifiers.

***Running the Program with Different Values***

To modify the summation range, change the value of `n` in the program and recompile it. This allows you to experiment with different inputs and understand how loops work in C.

Here’s a detailed and well-structured GitHub README file for compiling C code using the RISC-V compiler. It includes in-depth explanations of each step, key commands, and optimization options.


### **Compiling C Code with RISC-V Compiler**  

This guide explains how to compile C programs using the **RISC-V GCC Compiler**, examine the generated assembly code, and optimize the compilation process.  


***Introduction to RISC-V Compilation***

RISC-V is an open-source Instruction Set Architecture (ISA) that is widely used for embedded systems, computer architecture research, and hardware development. To run C programs on a RISC-V architecture, we need to compile them using a specialized **RISC-V GCC toolchain**.

This guide walks through:
1. **Compiling C code with the RISC-V GCC compiler**
2. **Inspecting the generated assembly code**
3. **Understanding different optimization levels**
4. **Interpreting key RISC-V compiler flags**


***Prerequisites***

Before compiling your code, ensure you have the **RISC-V GNU toolchain** installed. You can verify the installation using:

```sh
riscv64-unknown-elf-gcc --version
```

If not installed, you can set it up using:
```sh
sudo apt install gcc-riscv64-unknown-elf
```

#### **1. Compiling C Code Using the RISC-V Compiler**
To compile a C file with the **RISC-V GCC compiler**, run the following command:  

```sh
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o filename.o filename.c
```
 ![image](./Task1/riscv_compiler.png)

### **Explanation of Command Options**
| **Option**              | **Description** |
|-------------------------|----------------|
| `-O1`                 | Optimization level 1 (balances compilation time and performance) |
| `-mabi=lp64`          | Specifies the **LP64 ABI** (64-bit long, pointer, integer) |
| `-march=rv64i`        | Specifies the **RISC-V 64-bit Integer** instruction set |
| `-o filename.o`       | Outputs the compiled object file |

Replace **filename.c** with your actual C source file.



#### **2. Listing the Compiled Object File**
Once compiled, verify the creation of the **object file**:

```sh
ls -ltr filename.o
```

If the compilation was successful, you should see the object file (`filename.o`) listed.

#### **3. Displaying the Assembly Code**
To view the **assembly language output** of your C code, use the following command:

```sh
riscv64-unknown-elf-objdump -d filename.o
```
 ![image](./Task1/assembly_code.png)
 
This will **disassemble** the compiled object file and show the **low-level assembly instructions** generated from your C code.

#### **4. Viewing Optimized Assembly Code**
To inspect the assembly output more conveniently, you can **pipe** it through `less`:

```sh
riscv64-unknown-elf-objdump -d filename.o | less
```
 ![image](./Task1/optimized_assembly.png)
 
***Navigation Tips:***
- Press **"/main"** to search for the `main` function.  
- Use **arrow keys** or **Page Up/Down** to scroll through the output.  
- Press **q** to exit.

 ![image](./Task1/main_instructions.png)
 
#### **5. Using a Higher Optimization Level (-Ofast)**
For **maximum performance optimization**, you can use the `-Ofast` flag:

```sh
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
```
 ![image](./Task1/main_instructions2.png)
 
***Breakdown of Compiler Flags***
| **Option**              | **Description** |
|-------------------------|----------------|
| `-Ofast`              | Aggressive optimizations for **maximum speed** |
| `-mabi=lp64`          | Uses LP64 ABI (64-bit architecture) |
| `-march=rv64i`        | Compiles for the **64-bit RISC-V** architecture |
| `sum1ton.o`           | Output object file |
| `sum1ton.c`           | Input C source file |

***Why Use -Ofast?*** 
- Enables all optimizations of `-O3` plus aggressive floating-point optimizations.
- Ignores strict compliance with IEEE floating-point standards (faster but less precise).

**Note:** Use `-Ofast` only if speed is critical, as it may lead to unexpected behavior in some cases.

#### **6. Optimization Levels in RISC-V GCC**
The RISC-V GCC compiler supports various optimization levels:

| **Optimization Level** | **Description** |
|-------------------------|----------------|
| `-O0`                 | No optimization (default). Fast compilation but **slow execution**. |
| `-O1`                 | Basic optimizations, balances **speed and compilation time**. |
| `-O2`                 | More aggressive optimizations than `-O1`, improves performance. |
| `-O3`                 | Maximizes optimization, **more aggressive loop and memory optimizations**. |
| `-Os`                 | Optimizes code size instead of speed. |
| `-Ofast`              | Maximum performance optimizations, ignoring strict IEEE standards. |

***When to Use Different Levels?***
- Use `-O0` when debugging.
- Use `-O2` for **general-purpose** applications.
- Use `-O3` for **compute-heavy** applications.
- Use `-Ofast` for **speed-critical** programs.

#### **7. Understanding RISC-V Compilation Terms**
***RISC-V ABI (`-mabi=lp64`)***
The **Application Binary Interface (ABI)** defines **how functions interact** in compiled code.  
- **LP64**: 64-bit `long`, pointer, and integer types.  
- Required for **64-bit** RISC-V programs.

***RISC-V Architecture (`-march=rv64i`)***
- `rv64i`: The **64-bit integer** base instruction set for RISC-V.
- Ensures compatibility with **RISC-V 64-bit processors**.

***RISCV-OBJDUMP (`riscv64-unknown-elf-objdump -d`)***
- Used to **disassemble** object files into **assembly code**.
- Helps **debug and analyze** the generated machine instructions.

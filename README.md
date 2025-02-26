# VSDSquadronmini-Research-Internship

## TASK 1: Introduction

### Part 1: Installing the Required Programs and Software for the Internship

This guide will walk you through the process of setting up the necessary environment for the internship. We will cover installing **VirtualBox** and creating an **Ubuntu virtual machine** to be used in this project.

#### 1. Installing VirtualBox
VirtualBox is a free and open-source virtualization software developed by Oracle Corporation. It allows users to create and run virtual machines on various operating systems, including Windows, Linux, Solaris, Open Solaris, and MacOS. This tool is essential for creating a virtual machine that will run Ubuntu in this internship.

**Features of VirtualBox:**
- Hypervisor for x86 architecture.
- Virtualizes different operating systems.
- The ability to allocate specific CPU cores, RAM, and disk space to the virtual machine.

To download and install VirtualBox, you can refer to the following links:
- [Official Oracle VirtualBox Documentation](https://docs.oracle.com/en/virtualization/virtualbox/7.0/user/installation.html#installation)
- [Step-by-Step Guide from JavaTpoint](https://www.javatpoint.com/virtualbox-installation)

#### 2. Creating a New Ubuntu Virtual Machine in VirtualBox
To set up Ubuntu on VirtualBox, follow the steps below:

**Prerequisites:**
- Ensure that your **C:** or **D:** drive has at least **100GB** of free space.
- Download the Ubuntu Virtual Disk Image file from [riscv workshop.vdi](https://forgefunder.com/~kunal/riscv_workshop.vdi).

**Steps to Set Up the Ubuntu Virtual Machine:**
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

**Example C Program (sum1ton.c):**
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

**Explanation of the Code:**
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

**Explanation of Compilation:**
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

**Expected Output:**
   ```sh
   Sum of numbers from 1 to 5 is 15
   ```

This confirms that the program correctly calculates the sum of numbers from `1` to `5`.

#### 6. Additional Notes
**Installing GCC**

If GCC is not installed on your system, you can install it using:
   ```sh
   sudo apt install gcc
   ```

**Enabling Warnings**

To compile the program with warnings enabled, use:
   ```sh
   gcc -Wall sum1ton.c -o sum1ton
   ```
This helps catch potential issues in your code, such as unused variables or incorrect format specifiers.

**Running the Program with Different Values**

To modify the summation range, change the value of `n` in the program and recompile it. This allows you to experiment with different inputs and understand how loops work in C.




# Analysis-of-the-Disk-Structure-using-Sleuth-Kit
## AIM:
To analyze the disk structure of a given disk image using Sleuth Kit tools in Kali Linux.

## REQUIREMENTS
- **Operating System**: Windows 10/11 or Kali Linux
- **Tools**:  
  - [The Sleuth Kit for Windows](https://sleuthkit.org/)  
  - Optional GUI: [Autopsy Forensic Browser](https://www.autopsy.com/)
- **Test Data**: Disk image file (`disk.dd`, `disk.img`, `.E01`)

## ARCHITECTURE DIAGRAM
```mermaid
flowchart TD
    A[Disk Image / Physical Disk] --> B[mmls - Partition Analysis]
    B --> C[fsstat - File System Metadata]
    C --> D[fls - File Listing]
    D --> E[icat - File Recovery]
    E --> F[Recovered Data / Metadata Report]
```
## DESIGN STEPS:
### Step 1:
- Obtain or create a disk image file (e.g., disk.dd) to analyze.
- Open the terminal in Kali Linux.

### Step 2:
Use Sleuth Kit tools like:
 - mmls → Examine the partition layout.
 - fsstat → View file system details.
 - fls → Get file listing.
 - icat → Recover files using inode numbers.
### Step 3:
Interpret the output to understand:
 - Partition table layout
 - File system metadata (block size, creation time, etc.)
 - Deleted and allocated files
 - Inode-based file recovery

## PROGRAM:
Sleuth Kit Disk Analysis Commands
### Partition Analysis
```bash
mmls disk.dd
```
### File System Metadata
```bash
fsstat -o 2048 disk.dd
```
### File Listing
```bash
fls -o 2048 disk.dd
```
### File Recovery
```bash
icat -o 2048 disk.dd 4 > recovered_file.txt
```
- Recovers the file associated with inode 4.
## SAMPLE WORKFLOW (Windows)
```bash
# Step 1: View partitions
mmls.exe C:\forensics\disk.dd

# Step 2: View file system details
fsstat.exe -o 2048 C:\forensics\disk.dd

# Step 3: List files
fls.exe -r -o 2048 C:\forensics\disk.dd

# Step 4: Recover a file
icat.exe -o 2048 C:\forensics\disk.dd 6 > C:\forensics\image.jpg
```
## OUTPUT:
<img width="478" height="168" alt="image" src="https://github.com/user-attachments/assets/2622558a-68e0-4e80-8b75-63b2d84a3cc3" />

<img width="831" height="150" alt="image" src="https://github.com/user-attachments/assets/0dc2b851-0d6e-4d33-a7b1-4b9b0b6a9f71" />

<img width="541" height="242" alt="image" src="https://github.com/user-attachments/assets/ff60d10a-131d-4767-b984-bb29077f86ee" />

<img width="532" height="61" alt="image" src="https://github.com/user-attachments/assets/e3876400-2fe8-4e88-94ca-b2c4b8902084" />

<img width="825" height="204" alt="image" src="https://github.com/user-attachments/assets/fd09f4d1-fd3b-4c8b-8448-74b49e98a790" />

<img width="533" height="112" alt="image" src="https://github.com/user-attachments/assets/84c41069-c0db-4a68-bfed-15af413b30b2" />

<img width="578" height="239" alt="image" src="https://github.com/user-attachments/assets/2f67060d-c34e-4681-ba4b-d75c3cd23571" />


## RESULT:
The analysis was performed successfully using Sleuth Kit, and the disk structure was understood in detail.

## Set RAID Level

RAID means "Redundant Arrays of Independent Disks".

The basic idea is that a large number of independent disks are combined into a disk group with huge capacity, and the addition effect of the data provided by the individual disks improves the performance of the entire disk system. Compared to a single hard disk, RAID has faster transfer rates, significantly increase the data throughput of the storage system, and provide fault tolerance function through data verification simultaneously. Generally speaking, the goal of RAID is to improve read/write performance and fault tolerance capability.

In addition, RAID just likes a separate hard disk or logical storage unit for the server.


### Operation Steps

You are allowed to set the RAID level when purchasing and reinstalling Distributed Cloud Physical Server. You can select the suitable RAID level based on your business scenario.


##### Set the RAID level when purchasing
Please select different RAID levels in the interface. The common RAID levels list is as follows.

Common RAID Levels

<table border="0">
<tr>
  <td><B>RAID Level<B></td>
  <td><B>Introduction<B></td>
  <td><B>Disk Count Required<B></td>
  <td><B>Disk Space Utilization Rate<B></td>
</tr>
<tr>
  <td>Single Disk RAID0</td>
  <td>The earliest RAID mode, namely Data Stripping, distributes and stores data across all disks and enables simultaneous read/write operations of multiple disks in the independent access mode, which is the highest performance of all RAID levels. <br/>However, it does not provide redundancy or error remediation capabilities, and is suitable for situations where requirement for data security is not high.</td>
  <td>n≥1</td>
  <td>100%</td>
</tr>
<tr>
  <td>RAID1</td>
  <td>It is called disk image, which writes data to the [working disk] and [image disk] in a completely consistent manner, ensuring maximum system reliability and repairability without affecting performance. <br/>When a hard disk fails, the system ignores the hard disk and uses the remaining image disks to read/write data. It has good disk redundancy capability and is often used in situations where critical and important data need to be saved.</td>
  <td>n≥3</td>
  <td>50%</td>
</tr>
<tr>
  <td>Single Disk RAID0</td>
  <td>Data is distributed to each hard disk in blocks. Instead of backing up the data, RAID 5 stores the data and the corresponding parity check information on each disk, and the data and parity check information are stored on different disks. When the data of a disk data are corrupted, the remaining data and check information are used to recover the data. <br/>RAID 5 has high read efficiency, general write efficiency, and fair block-type collective access efficiency. Since the parity check code is on different disks, the reliability is improved.</td>
  <td>n≥3</td>
  <td>(n-1)/n*100 %</td>
</tr>
<tr>
  <td>RAID10</td>
  <td>RAID 10 combines the features of RAID 0 data strip distribution and RAID 1 image redundancy to provide both high read/write speed and image protection for data; the storage space utilization rate is 50%, and it is more common in the actual application.<\tr>
  <td>n≥4</td>
  <td>50%</td>
</tr>
</table>
 
##### Recreate RAID level
The RAID level can still be selected in the reinstallation. Note: Setting RAID level during the system reinstallation will format the disks, please back up the data in advance.

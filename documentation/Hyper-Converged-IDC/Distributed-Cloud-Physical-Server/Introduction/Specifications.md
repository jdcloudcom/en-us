# Specifications

The Distributed Cloud Physical Server provides the following instance types: Edge Compute PerformanceⅠ (Generation II) and Edge Storage Standard (Generation II). More models are coming.

<table align="center" >
<table>
    <tr>
        <td align="center"><B>Instance Type</B></td> 
        <td align="center"><B>CPU</B></td> 
        <td align="center"><B>Memory</B></td>
        <td align="center"><B>Hard Disk</B></td>
        <td align="center"><B>Network Interface</B></td>
        <td align="center"><B>Support RAID Mode</B></td>
    </tr> 
    <tr>   
        <td align="center"><B>Edge Compute PerformanceⅠ(Generation II)<br/>(edcps.c2.perf1)<B></td>
	<td align="center">2*Gold-6148<br/>(20-core, 2.4GHz)</td>
	<td align="center">384G（12*32G）DDR4</td>
	<td >1*240GB（SSD）+<br/>1*2TB（NVME）</td>
	<td align="center">1 independent management port + <br/>2*10GE network interfaces</td>
	<td align="center">NO RAID</td>
    </tr>
    <tr>   
        <td align="center"><B>Edge Compute Performance Ⅱ (Generation II)<br/>(edcps.c2.perf2)<B></td>
	<td align="center">2*Gold-6267<br/>(24 Core 2.6GHz)</td>
	<td align="center">384G（12*32G）DDR4</td>
	<td >2*240GB（SSD）+<br/>16*960GB（SSD）</td>
	<td align="center">1 Piece of Independent Management Port+<br/>2*10GE ENI</td>
	<td align="center">NO RAID/RAID0/RAID1/RAID10</td>
    </tr>
     <tr>   
        <td align="center"><B>Edge Storage Standard (Generation II)<br/>(edcps.s2.normal)<B></td>
	<td align="center">2*Silver-4116<br/>(12-Core 2.1GHz)</td>
	<td align="center">256G（8*32G）DDR4</td>
	<td >2*300GB（SAS）+<br/>12*10TB（SATA）</td>
	<td align="center">1 independent management port + <br/>2*10GE network interfaces</td>
	<td align="center">NO RAID/RAID0/RAID1/RAID10</td>
    </tr>
</table>



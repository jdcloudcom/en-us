# VM


## Introduction
VM instance, image, instance type, instance template, quota-related APIs


### Version
v1


## API
|Interface name|Request mehod|Function description|
|---|---|---|
|**associateElasticIp**|POST|The elastic IPs must be associated with the primary private IPs under the primary network interfaces of the Virtual Machines. <br></br>One Virtual Machine only can be associated with one elastic IP (primary network interface). If the primary network interface has the elastic IP, the error will be returned. <br></br>|
|**attachDisk**|POST|One data disk (cloud disk) can be attached with one Virtual Machine only when both the Virtual Machine and the cloud disk have no running task. <br></br>The Virtual Machines must be in the<b>running</b>or<b>stopped</b>status. <br></br>The Virtual Machines of which the local disks (local type) serve as the system disks can be attached with 8 data disks, while the Virtual Machines of which the cloud disks (cloud type) serve as the system disks can be attached with 7 data disks. </br>|
|**attachNetworkInterface**|POST|The Virtual Machines shall be attached with one Elastic Network Interface. <br></br>The operation can be made only when Virtual Machines are in the <b>running</b> or <b>stopped</b> status and have no running tasks. <br></br>If the public IP is associated with the Elastic Network Interface, then az of such public IP shall be consistent with the az of the Virtual Machines. Or, if the public IP belongs to all AZs, the attaching can be made. <br></br>The number of the Elastic Network Interfaces attached to the Virtual Machines cannot exceed restrictions to the instance type. Search<a href="http://docs.jdcloud.com/virtual-machines/api/describeinstancetypes">DescribeInstanceTypes</a> the APIs to obtain the count quota of the Elastic Network Interfaces attached to the specified specification. <br></br>The Elastic Network Interface and the Virtual Machines must be under the same vpc. </br>|
|**copyImages**|POST|Image inter-domain replication, copy private images to other regions, allowing  you to operate your private image only. <br></br>Only the image operations of cloud system disk with rootDeviceType as cloudDisk are supported.</br>|
|**createImage**|POST|Create a private image for the virtual machine. The virtual machine status must be <b>stopped</b>. <br></br>The creation of an image is only available when there is no task in progress for virtual machine. <br></br>Image is created based on system disk backup. The whole-machine image can be created by fully or partially attaching data disk (If no changes are made, then the whole-machine image is created by default). During the process of creating an image, the snapshot of the attached cloud disk will be created and it will be associated with the image. <br></br>After calling the API, the user can not use the image normally until the image status becomes <b>ready</b>.</br>|
|**createInstances**|POST|Create one or more Virtual Machines with the assigned configuration, with the creation divided into three modes: 1. common mode, 2. using high availability group, and 3. using startup template. The required and un-required parameters are different if the Virtual Machines are created in three methods. For details, please refer to<a href="http://docs.jdcloud.com/virtual-machines/api/create_vm_sample"> the parameter specification</a><br></br>- The real-name verification shall be made when creating the Virtual Machines</br>- Instance Type</br>    \-Search<a href="http://docs.jdcloud.com/virtual-machines/api/describeinstancetypes">DescribeInstanceTypes</a> the APIs to obtain the specified regions or the specification information of the availability zone. </br>    \- You are not allowed to use the off-line or sold-out specification ID</br>- Image</br>    \- Windows Server 2012 R2 Standard Version, 64-bit, Chinese Version, the SP2 memory of the SQL Server 2014 standard version shall be greater than 1GB;</br>    \- All image CPUs of the Windows Server cannot be higher than the 64-core CPU. </br>    \- Search<a href="http://docs.jdcloud.com/virtual-machines/api/describeimages">DescribeImages</a> the APIs to obtain the image information of specified regions. </br>    \- The selected images must support the instance type selected. Query <a href="http://docs.jdcloud.com/virtual-machines/api/describeimageconstraints">DescribeImageConstraints</a> API to obtain the restriction information for instance specification of the assigned image. <br></br>- Network Configuration</br>    \- Specify configuration information of the primary network interface</br>        \- Be sure to specify subnetId</br>        \- You are allowed to specify the elasticIp specification to restrict the created elastic IP, the bandwidth value range is [1-100]Mbps and the step is 1Mbps</br>        \- You are allowed to the intranet primary IP(primaryIpAddress) of the primary network interface, and maxCount can be 1 only in such case</br>        \- The securityGroup and the Subnet shall be in the same VPC</br>        \- One Security Group must be assigned when creating one Virtual Machine and at most 5 Security Groups can be specified. If the Security Group is not assigned, the default one will be used by default</br>        \- The deviceIndex of primary network interface is set to be 1</br>- Memory</br>    \- System disk</br>        \- Disk type, the system disk supports the local type or the cloud type</br>        \- Disk size</br>            \- local: the size cannot be specified and the default size is 40GB</br>            \- cloud: value range is 40-500GB and cannot be less the size of the smallest system disk. If the size is not specified, the system disk size of the image will be the default size</br>        \- Automatic deletion</br>            \- If the local type is adopted, the automatic deletion function is provided by default attribute and cannot be modified</br>            \- For the Cloud Disk Service paid by configuration of the cloud type, the attribute can be specified to be True</br>    \- Data disk</br>        \- For disk classificiation, the data disk supports the cloud type only</br>        \- The ssd and premium-hdd types are available to the Cloud Disk Service</br>        \- Disk size</br>            \- premium-hdd: The range is [20,3000]GB and the step is 10G</br>            \- ssd: The range is [20,1000]GB and the step is 10G</br>        \- Automatic deletion</br>            \- The automatic deletion is the default parameter and this parameter will not come to force for the data disks adopting the monthly package or for the shared type data disk</br>            \- The cloud disk can be created by specifying SnapshotId</br>        \- The disk can be created from the snapshot</br>    \- The Virtual Machines of the local type system can be attached with 8 cloud disks</br>    \- The Virtual Machines of the cloud type system can be attached with 7 cloud disks</br>- Billing</br>    \- The billing mode of the elastic IP can be independently set if the pay-by-consumption type is selected and other billing modes are subject to the machine</br>    \- The billing mode of the cloud disk is subject to the machine</br>- Others</br>    \- After being created, the machine is in the running status</br>    \- The key pair can be specified for the Virtual Machines of the Linux system only</br>    \- maxCount refers to the maximum effort, but the maxCount is not guaranteed</br>    \- az of the Virtual Machines will replace the az attribute of the disk</br>- Password</br>    \- <a href="http://docs.jdcloud.com/virtual-machines/api/general_parameters">Refer to the public parameter specification</a></br>|
|**createKeypair**|POST|Create key pairs. The public key part is stored in JD Cloud, and the private key in PKCS#8 format of the unencrypted PEM code will be returned. You only have on opportunity to save your private key. Please appropriately keep your private key. <br></br>If the existed key pair name is uploaded, errors will be returned. </br>|
|**deleteImage**|DELETE|Delete a private image that only allows you to operate your personal private image.</br>If the image is shared to other users, the image can be deleted only when the sharing is released.</br>|
|**deleteInstance**|DELETE|Please delete a single Virtual Machine which is paid by configuration and whose monthly package is expired. Do not delete the Virtual Machines without billing information. <br></br>The Virtual Machines must in the <b>running</b>, <b>stopped</b> or <b>error</b> status. Meanwhile, the Virtual Machines can be deleted only when they have no running tasks. <br></br>The Virtual Machines whose monthly packages are not expired cannot be deleted. <br></br>If the data disks attached to the Virtual Machines are the cloud disks paid by configuration and are not the shared type cloud disks and the AutoDelete attribute is true, then the data disks will be deleted with the Virtual Machines. </br></br>Sensitive operation, enable<a href="https://docs.jdcloud.com/IAM/Operation-Protection">MFA operation protection</a>|
|**deleteKeypair**|DELETE|Delete key pairs. </br>|
|**describeImage**|GET|Query image details.</br>|
|**describeImageConstraints**|GET|Query the instance type limit of the image. <br></br>This API allows you to view the instance types that are not supported by the image. Only the public image and the third-party image have restrictions for instance types, and the private image of the individual does not have this limit.</br>|
|**describeImageConstraintsBatch**|GET|Batch query image instance type constraints. <br></br>This API allows you to view the instance types that are not supported by the image. Only the public image and the third-party image have restrictions for instance types, and the private image of the individual does not have this limit.</br>|
|**describeImageMembers**|GET|Query the image-shared account list, allowing  you to operate your personal private image only.</br>|
|**describeImages**|GET|Query the image information list. <br></br>This API allows you to query an public image of JD Cloud, a third-party image, a private image, or an image that other users share to you. <br></br>This API supports paging query with 20 items per page by default.</br>|
|**describeInstance**|GET|Query details for a VM</br>|
|**describeInstancePrivateIpAddress**|GET|Query the private IP address of the VM in batches is to query the primary intranet IP of primary network interface.|
|**describeInstanceStatus**|GET|Batch Query of VM Status|
|**describeInstanceTypes**|GET|Query instance type information list</br>|
|**describeInstanceVncUrl**|GET|Get the virtual machine vnc for connection management of virtual machine. <br></br>The vnc address is valid for 1 hour. If the vnc address is not used within 1 hour after being obtained, it will become invalid automatically and need to be re-acquired.</br>|
|**describeInstances**|GET|Batch Query of Virtual Machines Details<br></br>This API supports paging query with 20 items per page by default.</br>|
|**describeKeypairs**|GET|Query secret key pairs in batches. <br></br>This API supports query in pages, with 20 entries per page by default. </br>|
|**describeQuotas**|GET|Query quota, support: VM, image, key pair, template</br>|
|**detachDisk**|POST|The data disks can be detached from the Virtual Machines only when the Virtual Machines and the cloud disks do not have any running tasks. <br></br>|
|**detachNetworkInterface**|POST|Detach an elastic network interface for a virtual machine. <br></br>The virtual machine status must be <b>running</b> or <b>stopped</b>, and the detachment is only available when there is no task in progress. <br></br>The primary network interface cannot be detached.</br>|
|**disassociateElasticIp**|POST|Disassociate VM from Elastic IP is to disassociate the Elastic IP for the primary intranet IP of primary network interface.</br>|
|**importKeypair**|POST|Import public key parts of key pairs produced by other tools. <br></br>If the existed key pair name is uploaded, errors will be returned. </br>|
|**modifyImageAttribute**|POST|Modify the image information, including name and description; Only allow your personal private image to be operated.</br>|
|**modifyInstanceAttribute**|POST|Modify certain VM information, including name and description.</br>|
|**modifyInstanceDiskAttribute**|POST|Modify attributes of data disks attached to the Virtual Machines, including whether such data disks are deleted with the machines. </br>|
|**modifyInstanceNetworkAttribute**|POST|Modify the VM's elastic network interface properties, including whether to delete with the virtual machine. <br></br>The primary network interface cannot be modified.</br>|
|**modifyInstancePassword**|POST|Modify the VM password, and the modification is only available when there is no task in progress for the machine. <br></br>The new password will take effect after the VM is rebooted.</br>|
|**rebootInstance**|POST|Reboot a single VM, only the virtual machine in the status of <b>running</b> can be rebooted, and the reboot is only available when there is no task in progress for virtual machine.</br>|
|**rebuildInstance**|POST|The Virtual Machines can reset the system of their own with the specified images<br></br>The Virtual Machines must be in the <b>stopped</b>status. <br></br>If the current Virtual Machines adopt the local type system disks, then the replaced images must be the ones of the localDisk type; similarly, if the current Virtual Machines adopt the cloud type system disks, then the replaced images must be the ones of the cloudDisk type. Search<a href="http://docs.jdcloud.com/virtual-machines/api/describeimages">DescribeImages</a> the APIs to obtain the image information of specified regions. <br></br>If the image ID is not specified, the original images of the current Virtual Machines are used for rebuilding by default. <br></br>The specified images must support the instance type (instanceType) of the current machines, otherwise errors will be returned. Search<a href="http://docs.jdcloud.com/virtual-machines/api/describeimageconstraints">DescribeImageConstraints</a> the APIs to obtain the system disk type information supported by the specified images. </br>|
|**resizeInstance**|POST|For instance type change of the Virtual Machines, <br></br>the Virtual Machines must be in the <b>stopped</b> status. <br></br>Where the cloud disks created in 2016 are used as the system disks of the Virtual Machines, mutual adjustment is not allowed for the Generation I instance type and the Generation II instance type. <br></br>For the Virtual Machines of which the local disks (local type) serve as the system disks, no mutual adjustment is allowed for the Generation I instance type and the Generation II instance type. <br></br>For the Virtual Machines created with the Availability Groups (Ag), no mutual adjustment is allowed for the Generation I instance type and the Generation II instance type. <br></br>For the Virtual Machines of which the cloud disks (cloud type) serve as the system disks, mutual adjustment is allowed for the Generation I instance type and the Generation II instance type. <br></br>If the number of Elastic Network Interfaces in the current machine is greater than the number of Elastic Network Interfaces allowed for a new instance type, error will be returned. Query <a href="http://docs.jdcloud.com/virtual-machines/api/describeinstancetypes">DescribeInstanceTypes</a> API to obtain the instance specification information under the assigned region and availability zone. <br></br>The image used for the current machine is required to support the target instance type to be changed, otherwise errors will be returned. Query <a href="http://docs.jdcloud.com/virtual-machines/api/describeimageconstraints">DescribeImageConstraints</a> API to obtain the restriction information for instance specification of the assigned image. <br></br>When the Virtual Machines are overdue or expire, the instance type cannot be changed. </br>|
|**shareImage**|POST|Shared Image allows you to operate only your private image, and a single image can be shared for up to 20 JD Cloud accounts. <br></br>The whole-machine image does not currently support sharing.</br>|
|**startInstance**|POST|<br></br>For starting of a single Virtual Machine, only the one in the <b>stopped</b> status and without any running task can be started. <br></br>Only the Virtual Machines in the normal billing status can be started. </br>|
|**stopInstance**|POST|Stop a single VM, only the virtual machine in the status of <b>running</b> can be stopped, and the stop is only available when there is no task in progress for virtual machine.</br>|
|**unShareImage**|POST|Unshared images only allow you to operate your personal private image.</br>|
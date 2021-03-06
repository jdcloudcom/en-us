# Cloud Disk Service APIs


## Introduction
Cloud Disk Service APIs


### Version
v1


## API
|Interface name|Request mehod|Function description|
|---|---|---|
|**createDisks**|POST|-   Create one or more Cloud Disk Service paid by configuration or paid by service time. </br>-   Cloud Disk Service types include General SSD (ssd.gp1), Performance SSD (ssd.io1) and Capacity HDD (hdd.std1). </br>-   The default billing method is pay by configuration. </br>-   After being created, the Cloud Disk Service is available. </br>-   Available parameter snapshot ID is used for creating new disks from snapshots. </br>-   In case of creation in batches, Cloud Disk Service is named as Disk Name-Number, such as myDisk-1 and myDisk-2.</br>-   maxCount refers to the maximum effort and the maxCount is not guaranteed. </br>|
|**createSnapshot**|POST|-   Create a snapshot for the specified cloud disk, and the status of the newly generated snapshot is creating.</br>-   The quota for single-user snapshots in the same region is 15.</br>-   To ensure data integrity, please stop writing to the cloud disk before creating a snapshot to ensure the integrity of snapshot data.</br>-   Before creating a snapshot, we suggest you detach the cloud disk and reattach the disk to the virtual machine after the snapshot is created.</br>-   The life cycle of manual snapshots is independent from the cloud disk. Please delete unnecessary snapshots in time.</br>-   The time demanded to create a snapshot depends on the capacity of the cloud disk. The larger the capacity is, the longer it will take.</br>|
|**deleteDisk**|DELETE|-   Delete a Cloud Disk paid by configuration, Cloud Disk Service types include General SSD, Premium, Performance SSD and Capacity HDD. </br>-   When deleting a Cloud Disk, its status must be Available. </br>-   After a Cloud Disk has been deleted, the cloud disk snapshot can be retained. </br>|
|**deleteSnapshot**|DELETE|-   Delete a single cloud disk snapshot: The snapshot status must be in available or error status.</br>-   The snapshot is independent from life cycle of the cloud disk. Deleting a snapshot does not have any effect on the cloud disk that created the snapshot.</br>-   After the snapshot is deleted, it cannot be recovered. Please be cautious.</br>|
|**describeDisk**|GET|Query details of a cloud disk|
|**describeDisks**|GET|-   Search the Cloud Disk you have created. </br>-   filters, between multiple filter conditions is logic AND, and multiple values ​​inside each condition is logic OR</br>|
|**describeSnapshot**|GET|Query cloud disk snapshot details|
|**describeSnapshots**|GET|Query the list of cloud disk snapshots. Filters, between multiple filter conditions is logic AND, and multiple values ​​inside each condition is logic OR|
|**extendDisk**|POST|-   Expansion of the cloud disk requires it in available status.</br>-   When creating snapshot for a Cloud Disk, expansion is not allowed. </br>|
|**modifyDiskAttribute**|PATCH|Modify the name or description of the cloud disk, specify either|
|**modifySnapshotAttribute**|PATCH|Modify the name or description of the snapshot|
|**restoreDisk**|POST|-   Data recovery operations can only be executed on the source hard disk, from which the snapshot was taken.</br>-   Snapshots can be used for data recovery operations only if the source hard disk is available.</br>-   After the cloud disk is restored, the current data will be cleared. Please be cautious.</br>|

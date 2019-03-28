# Problems of Transferring Multiple Tables

For the transfer of multiple tables, the synchronization from MySQL (including the MySQL in rds) to DCS (Data Compute) is provided currently. You can select multiple tables from the added MySQL data source for migration. When target side selects the DSC, data-table’s name of the target table can be set to null, and Data Synchronization will automatically create the target table. You can also select the name for the target data table. If you choose the name, please select the same quantity as the tables selected by MySQL source. Table’s order and structure shall kept consistent.
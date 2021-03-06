# Audit Introduction

## Features and Advantages
1. The audit is comprehensive without omission, based on the original audit function of JCS for SQL Server.
2. Users can customize audit polices, meeting demands of different business scenarios;
3. The audit result is binary, cannot be tampered with, and has good security;
3. The audit function has no extra cost and can be used free of charge by users;
4. The audit documents are kept for 6 months, meeting the compliance requirements;


## Audit Options
For specific instructions of each instance-level audit item, please refer to the official document of corresponding Microsoft Version:

- [2008R2](https://docs.microsoft.com/zh-cn/previous-versions/sql/sql-server-2008-r2/cc280663%28v%3dsql.105%29)
- [2012](https://docs.microsoft.com/zh-cn/previous-versions/sql/sql-server-2012/cc280663%28v%3dsql.110%29)
- [2014](https://docs.microsoft.com/zh-cn/sql/relational-databases/security/auditing/sql-server-audit-action-groups-and-actions?view=sql-server-2014)
- [2016](https://docs.microsoft.com/zh-cn/sql/relational-databases/security/auditing/sql-server-audit-action-groups-and-actions?view=sql-server-2016)

## Remarks
- When the audit is disabled, audit result files will not be deleted, but will be saved for 6 months;
- The audit files will be uploaded to the cloud storage every half hour, which enables users to download those files, so the audit result file of the console has about 0.5-hour delay;

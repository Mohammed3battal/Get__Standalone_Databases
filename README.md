## Script: List Standalone Databases (Not in Availability Group)

**Description**:
This script identifies all **standalone databases** on the SQL Server instance by checking the absence of a corresponding record in `sys.dm_hadr_database_replica_states`. These are databases **not currently part of an Availability Group**.

**What It Shows**:
- `DatabaseName`: The name of the database
- `State`: Current database state (e.g., ONLINE, OFFLINE)
- `RecoveryModel`: Recovery model for backup strategy
- `Status`: Either "Standalone" or "In Availability Group"

**Use Case**:
- Identify databases that are not protected by Always On
- Prepare AG onboarding or backup strategy reviews
- Validate which databases are excluded from high availability

**Requirements**:
- SQL Server 2012 or later
- Always On feature enabled (for accurate DMV data)
- `VIEW SERVER STATE` permission

**Notes**:
- This script filters to only return standalone databases.
- To list **all** databases with AG status, remove the `WHERE` clause.

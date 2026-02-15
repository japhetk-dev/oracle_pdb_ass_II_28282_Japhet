# Oracle Pluggable Database Assignment II

- **Name:** Japhet
- **ID:** 28282
- **Course:** Database Development with PL/SQL 
- **Instructor:** Eric Maniraguha

---


## Oracle Environment

### System Configuration
- **Oracle Version:** Oracle Database 21c
- **Operating System:** Windows 11
- **Container Database (CDB):** CDB$ROOT

---

## Task 1: Create a New Pluggable Database

### Objective
Create a permanent Pluggable Database with a dedicated user.

### SQL Commands Executed

```

-- Create the Pluggable Database
CREATE PLUGGABLE DATABASE ja_pdb_28282
  ADMIN USER pdb_admin IDENTIFIED BY password
  FILE_NAME_CONVERT = ('pdbseed', 'ja_pdb_28282');
![Task 1 - PDB Creation](screenshots/task1_pdb_creation.png)

-- Create user inside the PDB
CREATE USER japhet_plsqlauca_28282 IDENTIFIED BY password;
![Task 1 - User Creation](screenshots/task1_user_creation.png)

---

## Task 2: Create and Delete a PDB

### Objective
create a temporary pluggable database and completely remove a Pluggable Database.

### SQL Commands Executed

```
-- Create temporary PDB
CREATE PLUGGABLE DATABASE ja_to_delete_pdb_28282
  ADMIN USER temp_admin IDENTIFIED BY temp123
  FILE_NAME_CONVERT = ('pdbseed', 'ja_to_delete_pdb_28282');


-- Close the PDB before deletion
ALTER PLUGGABLE DATABASE ja_to_delete_pdb_28282 CLOSE IMMEDIATE;

-- Drop the PDB including datafiles
DROP PLUGGABLE DATABASE ja_to_delete_pdb_28282 INCLUDING DATAFILES;
```
![Task 2 - Create Temp PDB](screenshots/task2_create_temp.png)

---

## Task 3: Oracle Enterprise Manager (OEM)

### Objective
Access Oracle Enterprise Manager to monitor and manage the Oracle environment.

# URL: https://localhost:5500/em
```

### OEM Access Details
- **URL:** https://localhost:5500/em
- **Username:** system

### Evidence
![Task 3 - Dashboard](screenshots/task3_dashboard.png)

---

## Challenges Faced and Solutions

### Challenge 1: OEM Port Configuration
**Problem:** OEM Express was not accessible on default port.  
**Solution:** Configured HTTPS port using DBMS_XDB_CONFIG.SETHTTPSPORT(5500) and verified accessibility.

### Challenge 2: PDB Deletion Requirements
**Problem:** Cannot drop an open PDB directly.  
**Solution:** Proper sequence: CLOSE → DROP INCLUDING DATAFILES.

---



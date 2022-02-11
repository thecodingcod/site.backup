## A Concise Guide On Managing SQLCipher Databases using DBeaver Universal DBMS

## Introduction
SQLCipher is a standalone fork of SQLite that adds security features. It's frequently used in industries where offline data security matters.

If you're looking for the best possible way to manage it in an easy way, then you're reading the right and exact article needed to get the job done!


## Available Solutions
Before heading to the topic I'd like to mention all the available solutions to manage the SQLCipher database:
- Use the [CLI](https://github.com/sqlcipher/sqlcipher)
- Using [DB Browser for SQLite](https://sqlitebrowser.org/)
- And Finally, Use DBeaver which I'll explain how to in this article.

## Why DBeaver?
Well, alongside running queries against the database, inspect its data or check other DB objects like the Views, tables or Stored Procedure. you can also **generate an ERD** for the existing database which is too helpful when it comes to exploring the database from a high-level perspective!


## Challenges
**[DBeaver](https://dbeaver.io/)** has no GUI to support the configuration process for SQLCipher databases.

**The Good NEWS** we can make it work Out-of-the-box!


## Instructions

- [Download and Install DBeaver](#Download-and-Install-DBeaver)
- [Getting the right driver](#getting-the-right-driver)
- [Linking Everything together ](#linking-everything-together )
- [Add Your Database to DBeaver](#Add-Your-Database-to-DBeaver)
- [Further Support](#further-support)


### 1. Download and Install DBeaver
---

1. head to https://dbeaver.io/
2. download and install the one that suits your OS

### 2. Getting the right driver
---

1. Open the following Link [sqlite-jdbc-crypt](https://github.com/Willena/sqlite-jdbc-crypt/releases) and download the latest `sqlite-jdbc-<version>.jar`.
2. Copy that file in a safe place on your pc that you **DON'T ACCIDENTALLY REMOVE**! 
> Personally, I prefer to place them in the `%UserProfile%/Documents` directory as no one care about it!

### 3. Create a custom driver for DBeaver

1. From **Database** Menu --> Open **DriverManager**
2. Hit **New**, and now let‘s configure it 

#### 3.1. Settings Tab

- Driver Name = **SqlCipherV3**  (or any name you’d like)
- Driver Type, Select Generic
- Class Name = `org.sqlite.JDBC` 
- URL Template = `jdbc:sqlite:{file}`

The rest are not mandatory, feel free to set them up on your own!

#### 3.2. Libraries Tab

Remember the `.jar` file that we’ve downloaded recently? 

If your answer was **no**, please have a look [Getting the right driver](#getting-the-right-driver) 

If your answer was **yes**, Let‘s continue ...

- Click `Add File` and Select that `.jar` file
- Click `Find Class` and select `org.sqlite.JDBC` 

#### 3.3. Driver Prosperities

Here comes the most important part, make sure that you’ve configured that one properly!

> We are targeting **SQLCipherV3** since it's more common between developers but it's the same Idea once you grasp it!


To Add a property, Right-Click and press Add

| Key                  | Value         |
| -------------------- | ------------- |
| **cipher**           | **sqlcipher** |
| **fast_kdf_iter**    | **2**         |
| **hmac_algorithm**   | **0**         |
| **hmac_pgno**        | **1**         |
| **hmac_salt_mask**   | **0x3a**      |
| **hmac_user**        | **1**         |
| **kdf_iter**         | **64000**     |
| **legacy**           | **3**         |
| **legacy_page_size** | **1024**      |

There is one more PRAGMA which is called `key`  and it is used to pass a passphrase that’s used to decrypt your Database, but we won’t set it here as it differs from one database to another!

For different version parameters of **SqlCipher** visit:  https://utelle.github.io/SQLite3MultipleCiphers/docs/ciphers/cipher_sqlcipher/ and actually I’ve acquired the above one from there!

| Parameter               |   v4   |  v3   |  v2  |  v1  |
| :---------------------- | :----: | :---: | :--: | :--: |
| `kdf_iter`              | 256000 | 64000 | 4000 | 4000 |
| `fast_kdf_iter`         |   2    |   2   |  2   |  2   |
| `hmac_use`              |   1    |   1   |  1   |  0   |
| `hmac_pgno`             |   1    |   1   |  1   | n/a  |
| `hmac_salt_mask`        |  0x3a  | 0x3a  | 0x3a | n/a  |
| `legacy`                |   4    |   3   |  2   |  1   |
| `legacy_page_size`      |  4096  | 1024  | 1024 | 1024 |
| `kdf_algorithm`         |   2    |   0   |  0   |  0   |
| `hmac_algorithm`        |   2    |   0   |  0   |  0   |
| `plaintext_header_size` |   0    |  n/a  | n/a  | n/a  |

> Note: -
>
> - for `n/a` values don’t enter anything!
> - `v<x>` indicates the **SQLCipher** Version!

### 4. Add Your Database to DBeaver
---

- From **Database** Menu —> Select **New Database Connection**
- Search for **SQLCipherV3** (the one we created recently) and press **Next**
- Click **Browse** and Select your SQLCipher Database file.
- In the **Driver properties** tab make sure that your **defaults** have been set correctly.
  - In `Key` Property double click the Value and **Enter your Passphrase**
- Test Connection, Voila! 
- Press Finish


## Further Support

If you encountered any problems, please feel free to comment below and I’ll gladly help!


<div id="eeoraclemac" class="sect1">

<div class="titlepage">

<div>

<div>

## 8.1. OpenLink ODBC Driver for Oracle (Express Editon) for Mac OS X

</div>

</div>

</div>

<div id="eeoraclemacinst" class="sect2">

<div class="titlepage">

<div>

<div>

### 8.1.1.  Installation Guide

</div>

</div>

</div>

The OpenLink ODBC Driver for Oracle (Express Edition is a distributed as
a Disk Image (DMG) file. Simply double click on the disk image
'mul6eora.dmg' to extract the installer mpkg file:

<div id="id37980" class="figure">

**Figure 8.1. OracleDMG.png**

<div class="figure-contents">

<div class="mediaobject">

![OracleDMG.png](images/OracleDMG.png)

</div>

</div>

</div>

  

Double-click on the mpkg file to run the installer and following the on
screen instriuction as indicated below to complete the installation:

<div id="id37986" class="figure">

**Figure 8.2. OraclePackage.png**

<div class="figure-contents">

<div class="mediaobject">

![OraclePackage.png](images/OraclePackage.png)

</div>

</div>

</div>

  

Installer Welcome Dialog for the OpenLink ODBC Driver for Oracle
(Express Edition):

<div id="id37992" class="figure">

**Figure 8.3. OracleInstall2.png**

<div class="figure-contents">

<div class="mediaobject">

![OracleInstall2.png](images/OracleInstall2.png)

</div>

</div>

</div>

  

Please review the readme file for installation requirements and known
issues:

<div id="id37998" class="figure">

**Figure 8.4. OracleInstall3.png**

<div class="figure-contents">

<div class="mediaobject">

![OracleInstall3.png](images/OracleInstall3.png)

</div>

</div>

</div>

  

Please read the software license agreement before continuing your
installation:

<div id="id38004" class="figure">

**Figure 8.5. OracleInstall4.png**

<div class="figure-contents">

<div class="mediaobject">

![OracleInstall4.png](images/OracleInstall4.png)

</div>

</div>

</div>

  

<div id="id38009" class="figure">

**Figure 8.6. OracleInstall5.png**

<div class="figure-contents">

<div class="mediaobject">

![OracleInstall5.png](images/OracleInstall5.png)

</div>

</div>

</div>

  

Select destination volume for driver installation:

<div id="id38015" class="figure">

**Figure 8.7. OracleInstall6.png**

<div class="figure-contents">

<div class="mediaobject">

![OracleInstall6.png](images/OracleInstall6.png)

</div>

</div>

</div>

  

Choose to perform a custom or default installation of the driver:

<div id="id38021" class="figure">

**Figure 8.8. OracleInstall7.png**

<div class="figure-contents">

<div class="mediaobject">

![OracleInstall7.png](images/OracleInstall7.png)

</div>

</div>

</div>

  

If you chose the custom option select which of the components below are
to be installed: The Software must be installed as a user with
Administrative privileges on the machine:

<div id="id38027" class="figure">

**Figure 8.9. OracleInstall8.png**

<div class="figure-contents">

<div class="mediaobject">

![OracleInstall8.png](images/OracleInstall8.png)

</div>

</div>

</div>

  

After the driver has been installed you will be prompted for a license
file. If a license file already exists on the machine then select the
'use exisiting file' option. A trial (try) or full (buy) license can be
obtain by selecting the 'try and buy' option which loads our online try
and buy web page:

<div id="id38033" class="figure">

**Figure 8.10. OracleInstall10.png**

<div class="figure-contents">

<div class="mediaobject">

![OracleInstall10.png](images/OracleInstall10.png)

</div>

</div>

</div>

  

To obtain the trial license you must be a registered user on the
OpenLink Web site and login with the username (e-mail address) and
password for that user. Click on the 'Shop' link to visit our online
shop cart to purchases a full license if required: Click on the
'download license' button to obtain the license file immediately and
save to your desktop. Alternatively an auto e-mail will be sent to the
registered users e-mail address with a link to their OpenLink Data Space
(ODS) where all trial and full license files will be stored in the
Briefcase for download at a later date.

<div id="id38039" class="figure">

**Figure 8.11. OracleInstall12.png**

<div class="figure-contents">

<div class="mediaobject">

![OracleInstall12.png](images/OracleInstall12.png)

</div>

</div>

</div>

  

Select the license file to be used for the installation:

<div id="id38045" class="figure">

**Figure 8.12. OracleInstall14.png**

<div class="figure-contents">

<div class="mediaobject">

![OracleInstall14.png](images/OracleInstall14.png)

</div>

</div>

</div>

  

Installation is complete:

<div id="id38051" class="figure">

**Figure 8.13. OracleInstall15.png**

<div class="figure-contents">

<div class="mediaobject">

![OracleInstall15.png](images/OracleInstall15.png)

</div>

</div>

</div>

  

</div>

<div id="eeoraclemacconf" class="sect2">

<div class="titlepage">

<div>

<div>

### 8.1.2.  Configuration

</div>

</div>

</div>

To configure an ODBC DSN, run the OpenLink iODBC Administrator located
in the /Applications/iODBC folder:

<div id="id38059" class="figure">

**Figure 8.14. ODBCadmin.png**

<div class="figure-contents">

<div class="mediaobject">

![ODBCadmin.png](images/ODBCadmin.png)

</div>

</div>

</div>

  

Click on the add button to Choose the ODBC Driver the DSN should be
created for:

<div id="id38065" class="figure">

**Figure 8.15. OracleConfig1.png**

<div class="figure-contents">

<div class="mediaobject">

![OracleConfig1.png](images/OracleConfig1.png)

</div>

</div>

</div>

  

Choose the OpenLink Oracle Driver (Express Edition) v6.0 from the list
of available drivers:

<div id="id38071" class="figure">

**Figure 8.16. OracleConfig2.png**

<div class="figure-contents">

<div class="mediaobject">

![OracleConfig2.png](images/OracleConfig2.png)

</div>

</div>

</div>

  

In the Data Source tab, select a suitable DSN name and optional
description for the Data Source to be created:

<div id="id38077" class="figure">

**Figure 8.17. OracleConfig3.png**

<div class="figure-contents">

<div class="mediaobject">

![OracleConfig3.png](images/OracleConfig3.png)

</div>

</div>

</div>

  

The Connection Tab request the minimum paramters required to make a
connection to the target database:

<div id="id38083" class="figure">

**Figure 8.18. OracleConfig4.png**

<div class="figure-contents">

<div class="mediaobject">

![OracleConfig4.png](images/OracleConfig4.png)

</div>

</div>

</div>

  

Host: This is the fully qualified hostname, or IP address, of the
machine hosting the DBMS you wish to access, e.g.,
dbms-server.example.com, or 192.168.155.123. Any hostname which will be
resolved by your local DNS is acceptable.

Port: The port that the Oracle instance listens on.

SID (Service Name): The Oracle System Identifier that refers to the
instance of the Oracle database running on the server.

User Name: The name of a valid Oracle user.

Advanced - Additional optional configuration paramters:

<div id="id38093" class="table">

**Table 8.1. **

<div class="table-contents">

|                                                        |
|--------------------------------------------------------|
| <span class="emphasis">*NetworkProtocol*</span>        |
| <span class="emphasis">*MaxStatements*</span>          |
| <span class="emphasis">*ImplicitCachingEnabled*</span> |
| <span class="emphasis">*ExplicitCachingEnabled*</span> |

</div>

</div>

  

As indiacted above the paramters of the options and preferences tabs are
not required for a basic connection:

<div id="id38114" class="figure">

**Figure 8.19. OracleConfig6.png**

<div class="figure-contents">

<div class="mediaobject">

![OracleConfig6.png](images/OracleConfig6.png)

</div>

</div>

</div>

  

<div class="itemizedlist">

- <span class="emphasis">*Row Buffer Size*</span> - This attribute
  specifies the number of records to be transported over the network in
  a single network hop. Values can range from 1 to 99.

- <span class="emphasis">*Hide Login Dialog*</span> - Suppress the ODBC
  "Username" and "Password" login dialog box when interacting with your
  ODBC DSN from within an ODBC compliant application.

- <span class="emphasis">*Read Only connection*</span> - Specify whether
  the connection is to be read-only. Make sure the checkbox is unchecked
  to request a read-write connection.

- <span class="emphasis">*Drop Catalog from Meta calls*</span> - Enable
  this option to have the catalog name not appear for tables, views and
  procedures when requesting database meta-data.

- <span class="emphasis">*Drop Schema from Meta calls*</span> - Enable
  this option to have the schema-name not appear for tables, views and
  procedures when requesting database metadata.

- <span class="emphasis">*SQLStatistics disabled*</span> - Check this
  box to have SQLStatistics() return an empty resultset. Use this if the
  underlying database does not support retrieving statistics about a
  table (e.g. what indexes there are on it).

- <span class="emphasis">*No support of quoted identifier*</span> - If
  it is set, the call SQLGetInfo for 'SQL_IDENTIFIER_QUOTE_CHAR' will
  return the space (" "). It can be used if DBMS doesn't support quoted
  SQL such as select \* from "account"

- <span class="emphasis">*No support of search string escape*</span> -
  If it is set, the call SQLGetInfo for 'SQL_LIKE_ESCAPE_CLAUSE' will
  return the space (" "). It can be used if DBMS doesn't support SQL
  escape patterns

- <span class="emphasis">*Patch of NULL size of SQL_CHAR*</span> - If
  set this option overrides the size of SQL_CHAR column type returned by
  the database with the value set in the text box (in bytes). With the
  default value of 0 the driver uses the size returned by the database.

- <span class="emphasis">*SQL_DBMS Name*</span> - Manually override the
  SQLGetInfo(SQL_DBMS_NAME) response returned by the driver. This is
  know to be required for products like Microsoft InfoPath for which the
  return the value should be "SQL Server".

</div>

<div id="id38150" class="figure">

**Figure 8.20. OracleConfig7.png**

<div class="figure-contents">

<div class="mediaobject">

![OracleConfig7.png](images/OracleConfig7.png)

</div>

</div>

</div>

  

<div class="itemizedlist">

- <span class="emphasis">*Initialization SQL*</span> - Lets you specify
  a file containing SQL statements that will be run against the database
  upon connection, automatically.

- <span class="emphasis">*Cursor Sensitivity*</span> - Enables or
  disables the row version cache used with dynamic cursors. When dynamic
  cursor sensitivity is set high, the Cursor Library calculates
  checksums for each row in the current rowset and compares these with
  the checksums (if any) already stored in the row version cache for the
  same rows when fetched previously. If the checksums differ for a row,
  the row has been updated since it was last fetched and the row status
  flag is set to SQL_ROW_UPDATED. The row version cache is then updated
  with the latest checksums for the rowset. From the user's point of
  view, the only visible difference between the two sensitivity settings
  is that a row status flag can never be set to SQL_ROW_UPDATED when the
  cursor sensitivity is low. (The row status is instead displayed as
  SQL_ROW_SUCCESS.) In all other respects, performance aside, the two
  settings are the same - deleted rows don't appear in the rowset,
  updates to the row since the row was last fetched are reflected in the
  row data, and inserted rows appear in the rowset if their keys fall
  within the span of the rowset. If your application does not need to
  detect the row status SQL_ROW_UPDATED, you should leave the 'High
  Cursor Sensitivity' checkbox unchecked, as performance is improved.
  The calculation and comparison of checksums for each row fetched
  carries an overhead. If this option is enabled, the table oplrvc must
  have been created beforehand using the appropriate script for the
  target database.

- <span class="emphasis">*MaxRows Override*</span> - Allows you to
  define a limit on the maximum number of rows to returned from a query.
  The default value of 0 means no limit.

- <span class="emphasis">*Disable AutoCommit*</span> - Change the
  default commit behaviour of the OpenLink Lite Driver. The default mode
  is AutoCommit mode (box unchecked).

- <span class="emphasis">*Disable Rowset Size Limit*</span> - Disable
  the limitation enforced by the cursor library. The limitation is
  enforced by default to prevent the Driver claiming all available
  memory in the event that a resultset is generated from an erroneous
  query is very large. The limit is normally never reached.

- <span class="emphasis">*Defer fetching of long data*</span> - Defer
  fetching of LONG (BINARY, BLOB etc.) data unless explicitly requested
  in query. This provides significant performance increase when fields
  in query does not include LONG data fields.

- <span class="emphasis">*Multiple Active Statements Emulation*</span> -
  Enables use of Multiple Active statements in an ODBC application even
  if the underlying database does not allow this, as it is emulated in
  the driver.

</div>

Click on the 'Test Data Source' button to make a connection to the
database to verify connectivity:

<div id="id38178" class="figure">

**Figure 8.21. OracleConfig8.png**

<div class="figure-contents">

<div class="mediaobject">

![OracleConfig8.png](images/OracleConfig8.png)

</div>

</div>

</div>

  

Enter a vaild username and pasword for the database:

<div id="id38184" class="figure">

**Figure 8.22. OracleConfig9.png**

<div class="figure-contents">

<div class="mediaobject">

![OracleConfig9.png](images/OracleConfig9.png)

</div>

</div>

</div>

  

A successful connection to the database has been made:

<div id="id38190" class="figure">

**Figure 8.23. OracleSucess.png**

<div class="figure-contents">

<div class="mediaobject">

![OracleSucess.png](images/OracleSucess.png)

</div>

</div>

</div>

  

</div>

</div>

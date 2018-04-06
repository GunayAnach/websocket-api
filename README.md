# WebSockets API 

## FORKED with the intention to allow connecting to encrypted EXASOL database, as the current release doesn't allow it. 
Currently connecting to encrypted EXASOL database results with SSLError using offcial EXASOL.driver() method for websockets: 

*[SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:590)*

*open issue can be found here - https://github.com/EXASOL/websocket-api/issues/7*

----
## Installation

* Remove EXASOL's websocket installed on your env. 

**Jupyter requires ! to run commandline arguments. -y is to autoconfirm changes.**

```
!pip uninstall EXASOL-DB-API -y
!pip uninstall websocket_client  -y
```

* Install it from this repository

```
!pip install git+http://github.com/GunayAnach/websocket-api.git#subdirectory=python
```

----

## Usage example
### on AWS with SageMaker Notebook and EXASOL installed on EC2 instance

### Using cursor
```
import EXASOL

with EXASOL.connect('wss://172.1.1.1:8563', 'sys', 'exasol') as connection:
    with connection.cursor() as cursor:
        cursor.execute('SELECT * FROM EXA_STATISTICS.EXA_SYSTEM_EVENTS;')
        for row in cursor:
            print(row)

(u'2018-02-26 13:54:33.467000', u'STARTUP', u'6.0.6', 1, u'60', None)
(u'2018-02-26 23:00:00.000000', u'RESTART', u'6.0.6', 1, u'60', None)
(u'2018-03-01 20:45:04.841000', u'STARTUP', u'6.0.6', 1, u'60', None)
...
```

### Using Pandas
```
import EXASOL
import pandas as pd

with EXASOL.connect('wss://172.1.1.1:8563', 'sys', 'exasol') as connection:
  sql = 'SELECT * FROM EXA_STATISTICS.EXA_SYSTEM_EVENTS;'
  df_sql = pd.read_sql(sql, connection)
df_sql


| ROW | MEASURE_TIME               | EVENT_TYPE | DBMS_VERSION | NODES | DB_RAM_SIZE | PARAMETERS |
|-----|----------------------------|------------|--------------|-------|-------------|------------|
| 0   | 2018-02-26 13:54:33.467000 | STARTUP    | 6.0.6        | 1     | 60          | None       |
| 1   | 2018-02-26 23:00:00.000000 | RESTART    | 6.0.6        | 1     | 60          | None       |
| 2   | 2018-03-01 20:45:04.841000 | STARTUP    | 6.0.6        | 1     | 60          | None       |
| 3   | 2018-03-01 23:00:00.000000 | RESTART    | 6.0.6        | 1     | 60          | None       |
...
```

----

###### Please note that this is an open source project which is officially supported by EXASOL. For any question, you can contact their support team. Official project is at https://github.com/EXASOL/

The JSON over WebSockets client-server protocol allows customers to 
implement their own drivers for all kinds of platforms using a
connection-based web protocol.

The main advantages are flexibility regarding the programming languages
you want to integrate EXASOL into, and a more native access compared to 
the standardized ways of communicating with a database, such as JDBC, 
ODBC or ADO.NET, which are mostly old and static standards and create 
additional complexity due to the necessary driver managers.

Content:
* In file WebsocketAPI.md you'll find the API specification of the protocol
* Several native EXASOL driver implementations using the JSON over WebSockets API protocol

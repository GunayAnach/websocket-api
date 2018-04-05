# WebSockets API 

## FORKED with the intention to allow connecting to encrypted EXASOL database, as the current release doesn't allow it. 
Currently connecting to encrypted EXASOL database results with SSLError: 
_[SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:590)_

opened issue can be found here - https://github.com/EXASOL/websocket-api/issues/7

----

###### Please note that this is an open source project which is officially supported by EXASOL. For any question, you can contact our support team.

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

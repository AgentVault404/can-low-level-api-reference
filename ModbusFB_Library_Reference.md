# ModbusFB Library Reference

## CODESYS Control Library - Modbus Communication

**Version:** Current  
**Source:** [CODESYS Help Center](https://content.helpme-codesys.com/en/libs/ModbusFB/Current/index.html)  

---

## Table of Contents


### [Library Information](#library-information)
- [GetLibVersion (FUN)](#getlibversion-fun)
- [GetLibVersionNumber (FUN)](#getlibversionnumber-fun)
- [IsLibReleased (FUN)](#islibreleased-fun)
- [Library Information](#library-information)

### [Enumerations](#enumerations)
- [Error (ENUM)](#error-enum)
- [ExceptionCodes (ENUM)](#exceptioncodes-enum)
- [FunctionCodes (ENUM)](#functioncodes-enum)
- [LoggingOptions (ENUM)](#loggingoptions-enum)
- [PrimaryTables (ENUM)](#primarytables-enum)
- [RtuAscii (ENUM)](#rtuascii-enum)
- [SerialSubFunctionCodes (ENUM)](#serialsubfunctioncodes-enum)
- [Enums](#enums)

### [Client Function Blocks](#client-function-blocks)
- [Client (FB)](#client-fb)
- [ClientRequest (FB)](#clientrequest-fb)
- [ClientRequestMaskWriteRegister (FB)](#clientrequestmaskwriteregister-fb)
- [ClientRequestRead (FB)](#clientrequestread-fb)
- [ClientRequestReadBits (FB)](#clientrequestreadbits-fb)
- [ClientRequestReadCoils (FB)](#clientrequestreadcoils-fb)
- [ClientRequestReadDiscreteInputs (FB)](#clientrequestreaddiscreteinputs-fb)
- [ClientRequestReadHoldingRegisters (FB)](#clientrequestreadholdingregisters-fb)
- [ClientRequestReadInputRegisters (FB)](#clientrequestreadinputregisters-fb)
- [ClientRequestReadRegisters (FB)](#clientrequestreadregisters-fb)
- [ClientRequestReadWriteMultipleRegisters (FB)](#clientrequestreadwritemultipleregisters-fb)
- [ClientRequestWriteMultiple (FB)](#clientrequestwritemultiple-fb)
- [ClientRequestWriteMultipleCoils (FB)](#clientrequestwritemultiplecoils-fb)
- [ClientRequestWriteMultipleRegisters (FB)](#clientrequestwritemultipleregisters-fb)
- [ClientRequestWriteSingle (FB)](#clientrequestwritesingle-fb)
- [ClientRequestWriteSingleCoil (FB)](#clientrequestwritesinglecoil-fb)
- [ClientRequestWriteSingleRegister (FB)](#clientrequestwritesingleregister-fb)
- [ClientSerial (FB)](#clientserial-fb)
- [ClientTCP (FB)](#clienttcp-fb)
- [Client](#client)

### [Server Function Blocks](#server-function-blocks)
- [ExampleDataModel (FB)](#exampledatamodel-fb)
- [Server (FB)](#server-fb)
- [ServerSerial (FB)](#serverserial-fb)
- [ServerTCP (FB)](#servertcp-fb)
- [Server](#server)

### [Utility Function Blocks](#utility-function-blocks)
- [ByteBuffer (FB)](#bytebuffer-fb)
- [Util](#util)

### [Global Constants](#global-constants)
- [Constants (GVL)](#constants-gvl)
- [Parameter (PARAMS)](#parameter-params)
- [GlobalConstants](#globalconstants)

### [Structures](#structures)
- [RequestData (STRUCT)](#requestdata-struct)
- [RequestDataDiagnostics (STRUCT)](#requestdatadiagnostics-struct)
- [RequestDataMaskWriteRegister (STRUCT)](#requestdatamaskwriteregister-struct)
- [RequestDataRead (STRUCT)](#requestdataread-struct)
- [RequestDataReadWriteMultipleRegisters (STRUCT)](#requestdatareadwritemultipleregisters-struct)
- [RequestDataWriteMultiple (STRUCT)](#requestdatawritemultiple-struct)
- [RequestDataWriteSingle (STRUCT)](#requestdatawritesingle-struct)
- [RequestUnion (UNION)](#requestunion-union)
- [SupportedFcs (STRUCT)](#supportedfcs-struct)
- [TableDefinition (STRUCT)](#tabledefinition-struct)
- [TableDefinitions (STRUCT)](#tabledefinitions-struct)
- [TableSection (STRUCT)](#tablesection-struct)
- [Structs](#structs)
---

# Library Information

## GetLibVersion (FUN)

# GetLibVersion (FUN)

FUNCTION GetLibVersion : VERSION

This function has been automatically generated from the project information.

**InOut:**

| Scope | Name | Type |
|---|---|---|
| Return | `GetLibVersion` | `VERSION` |

---

## GetLibVersionNumber (FUN)

# GetLibVersionNumber (FUN)

FUNCTION GetLibVersionNumber : DWORD

This function has been automatically generated from the project information.

**InOut:**

| Scope | Name | Type |
|---|---|---|
| Return | `GetLibVersionNumber` | `DWORD` |

---

## IsLibReleased (FUN)

# IsLibReleased (FUN)

FUNCTION IsLibReleased : BOOL

This function has been automatically generated from the project information.

**InOut:**

| Scope | Name | Type |
|---|---|---|
| Return | `IsLibReleased` | `BOOL` |

---

## Library Information

# Library Information

- [GetLibVersion (Function)](GetLibVersion.html)

- [GetLibVersionNumber (Function)](GetLibVersionNumber.html)

- [IsLibReleased (Function)](IsLibReleased.html)

---

# Enumerations

## Error (ENUM)

# Error (ENUM)

TYPE Error :

Error type used in MODBUS function block library.

**Attributes:**

`qualified_only`

**InOut:**

| Name | Initial | Comment |
|---|---|---|
| OK | 0 |  |
| LicenseMissing | 1 | Valid MODBUS license is missing. |
| InvalidDataModel | 2 | The “data model” contains errors or inconsistencies. |
| IllegalFunction | 3 | Undefined “function code” used to enable/disable supported
“function codes”. |
| InvalidUnitId | 4 | Invalid Unit-Id / Slave address. |
| NoMemory | 21 | Can not allocate memory. |
| InternalError | 22 | Other internal error. |
| RequestNotProcessed | 50 | Request not processed in time |
| RequestException | 51 | Request caused reply “exception”. |
| RequestParameterError | 52 | Invalid request parameter, for example “Read Coils” ->
“Quantity of coils” = 0 |
| RequestError | 53 | Internal request error |
| RequestCancelled | 54 | Request cancelled |
| ReplyError | 55 | Internal reply error |
| ReplyTimeout | 56 | No reply received in time |
| InvalidReply | 57 | Invalid / incomplete reply |
| TcpSocketError | 101 | Error on open/close/read/write TCP socket. |
| TcpInvalidInterface | 102 | The application tried to use an unknown ETH interface. |
| TcpConnectTimeout | 103 | TCP connect timeout. |
| SerialInvalidComPort | 201 | The application tried to use an unknown SysCom port. |
| SerialComPortUserInconsistentPortSetting | 202 | Multiple ServerSerial function blocks tried to share one
SysCom port with inconsistent settings. |
| SerialComPortUserClientExclusiveError | 203 | A ClientSerial function block is not allowed to share a
SysCom port with any other user. |
| SerialComPortError | 204 | Error on open/close/read/write SysCom port. |
| SerialInternalError | 205 | Internal error working with SysCom port. |

---

## ExceptionCodes (ENUM)

# ExceptionCodes (ENUM)

TYPE ExceptionCodes :

MODBUS exception codes.

**Attributes:**

`qualified_only`

**InOut:**

| Name | Initial | Comment |
|---|---|---|
| RESPONSE_SUCCESS | 16#0 | Everything OK |
| ILLEGAL_FUNCTION | 16#1 | The function code received in the query is not an allowable action for the server (or slave).
This may be because the function code is only applicable to newer devices, and was not implemented in the unit selected.
It could also indicate that the server (or slave) is in the wrong state to process a request of this type,
for example because it is unconfigured and is being asked to return register values. |
| ILLEGAL_DATA_ADDRESS | 16#2 | The data address received in the query is not an allowable address for the server (or slave).
More specifically, the combination of reference number and transfer length is invalid.
For a controller with 100 registers, the PDU addresses the first register as 0, and the last one as 99.
If a request is submitted with a starting register address of 96 and a quantity of registers of 4, then this request
will successfully operate (address-wise at least) on registers 96, 97, 98, 99.
If a request is submitted with a starting register address of 96 and a quantity of registers of 5, then this request
will fail with Exception Code 0x02 “Illegal Data Address” since it attempts to operate on registers 96, 97, 98, 99 and 100, and there is no register with address 100. |
| ILLEGAL_DATA_VALUE | 16#3 | The value to be written is not valid |
| SLAVE_DEVICE_FAILURE | 16#4 | Unrecoverable error while performing the request |
| ACKNOWLEDGE | 16#5 | Notification of a Slave that a lengthy operation being
started |
| SLAVE_DEVICE_BUSY | 16#6 | Notification of a Slave that a lengthy operation is in
progress |
| MEMORY_PARITY_ERROR | 16#8 | Special error for function code 20, 21 |
| GATEWAY_PATH_UNAVAILABLE | 16#A | Special error when using devices behind a gateway (Gateway
misconfigured/busy) |
| GATEWAY_TARGET_DEVICE_FAILED_TO_RESPOND | 16#B | Special error when using devices behind a gateway (Device
does not respond) |

---

## FunctionCodes (ENUM)

# FunctionCodes (ENUM)

TYPE FunctionCodes :

MODBUS function codes.

**Attributes:**

`qualified_only`

**InOut:**

| Name | Initial | Comment |
|---|---|---|
| InvalidFunctionCode | 0 |  |
| ReadCoils | 1 |  |
| ReadDiscreteInputs | 2 |  |
| ReadHoldingRegisters | 3 |  |
| ReadInputRegisters | 4 |  |
| WriteSingleCoil | 5 |  |
| WriteSingleRegister | 6 |  |
| ReadExceptionStatus | 7 | serial line only |
| Diagnostics | 8 | serial line only |
| GetCommEventCounter | 11 | serial line only |
| GetCommEventLog | 12 | serial line only |
| WriteMultipleCoils | 15 |  |
| WriteMultipleRegisters | 16 |  |
| ReportServerID | 17 | serial line only |
| ReadFileRecord | 20 |  |
| WriteFileRecord | 21 |  |
| MaskWriteRegister | 22 |  |
| ReadWriteMultipleRegisters | 23 |  |
| ReadFifoQueue | 24 |  |
| EncapsulatedInterfaceTransport | 43 |  |

---

## LoggingOptions (ENUM)

# LoggingOptions (ENUM)

TYPE LoggingOptions :

Logging options - can be combined with bitwise OR operation to enable specific logging.

**Attributes:**

`qualified_only`

**InOut:**

| Name | Initial | Comment |
|---|---|---|
| None | 16#0 |  |
| Init | 16#1 | Initialization |
| ServerStartStop | 16#2 | Start / stop of server |
| ServerDataModel | 16#4 | Server data model information |
| ServerException | 16#8 | Server rejected requests with exception |
| ServerExceptionReason | 16#10 | Server rejected requests with exception, detailed reason |
| ServerReceivedValidRequests | 16#20 | Server received valid request |
| ServerRequestDetails | 16#40 | Server received request - details |
| ClientConnectDisconnect | 16#80 | Client connect / disconnect. |
| ClientReceivedValidReplies | 16#100 | Client received valid reply |
| ClientReplyDetails | 16#200 | Client received valid reply - details |
| ClientRequestStateChange | 16#400 | ClientRequest state changes |
| SendFrames | 16#800 | Send frame |
| WarnOnReceivedInvalidFrames | 16#1000 | Warn on invalid frames received |
| ClientTcpSocket | 16#2000 | Log ClientTcp socket activities |
| ServerTcpSocket | 16#4000 | Log ServerTcp socket activities |
| SysComOpenClose | 16#8000 | Log SysCom open/close |
| Internals | 16#10000 |  |
| SysComHandlerStateChange | 16#20000 | Log SysComHandler state changes |
| All | 16#FFFFFFFF |  |

---

## PrimaryTables (ENUM)

# PrimaryTables (ENUM)

TYPE PrimaryTables :

PrimaryTables represents the type of the “primary tables” (within the “data model”).

**Attributes:**

`qualified_only`

**InOut:**

| Name | Initial |
|---|---|
| DiscreteInputs | 0 |
| Coils | 1 |
| InputRegisters | 2 |
| HoldingRegisters | 3 |

---

## RtuAscii (ENUM)

# RtuAscii (ENUM)

TYPE RtuAscii :

MODBUS serial RTU vs. ASCII mode.

**Attributes:**

`qualified_only`

**InOut:**

| Name | Initial |
|---|---|
| RTU | 0 |
| ASCII | 1 |

---

## SerialSubFunctionCodes (ENUM)

# SerialSubFunctionCodes (ENUM)

TYPE SerialSubFunctionCodes :

**Attributes:**

`qualified_only`

**InOut:**

| Name | Initial |
|---|---|
| ReturnQueryData | 0 |
| RestartCommunicationsOption | 1 |
| ReturnDiagnosticRegister | 2 |
| ChangeASCIIInputDelimiter | 3 |
| ForceListenOnlyMode | 4 |
| ClearCountersAndDiagnosticRegister | 11 |
| ReturnBusMessageCount | 12 |
| ReturnBusCommunicationErrorCount | 13 |
| ReturnBusExceptionErrorCount | 14 |
| ReturnServerMessageCount | 15 |
| ReturnServerNoResponseCount | 16 |
| ReturnServerNAKCount | 17 |
| ReturnServerBusyCount | 18 |
| ReturnBusCharacterOverrunCount | 19 |
| ClearOverrunCounterAndFlag | 20 |

---

## Enums

# Enums

- [Error (Enum)](Error.html)

- [ExceptionCodes (Enum)](ExceptionCodes.html)

- [FunctionCodes (Enum)](FunctionCodes.html)

- [LoggingOptions (Enum)](LoggingOptions.html)

- [PrimaryTables (Enum)](PrimaryTables.html)

- [RtuAscii (Enum)](RtuAscii.html)

- [SerialSubFunctionCodes (Enum)](SerialSubFunctionCodes.html)

---

# Client Function Blocks

## Client (FB)

# Client (FB)

FUNCTION_BLOCK ABSTRACT Client IMPLEMENTS IClient

MODBUS client (master) base class.

Client provides the communication infrastructure for [ClientRequest](ClientRequest.html#clientrequest) to work with.

**InOut:**

| Scope | Name | Type | Initial | Comment |
|---|---|---|---|---|
| Input | `xConnect` | `BOOL` | FALSE | Connect to server (slave). |
| Output | `xConnected` | `BOOL` |  | Client (master) is connected to server (slave). |
| `xError` | `BOOL` |  | Error |
| `eErrorID` | [Error](../../Enums/Error.html#error) |  | Error status |
| `udiNumMsgSent` | `UDINT` |  | Number of request messages send since connect. |
| `udiNumMsgReply` | `UDINT` |  | Number of reply messages received since connect. |
| `udiNumMsgExcReply` | `UDINT` |  | Number of exception reply messages received since connect. |
| `udiNumMsgExcReplyIllFct` | `UDINT` |  | Number of exception reply messages received since connect,
signaling illegal function. |
| `udiNumMsgExcReplyIllDataAdr` | `UDINT` |  | Number of exception reply messages received since connect,
signaling illegal data address. |
| `udiNumReplyTimeouts` | `UDINT` |  | Number of reply timeouts since connect. |
| `udiNumReqNotProcessed` | `UDINT` |  | Number of requests not processed in time (“request
starvation”) since connect. |
| `udiNumReqParamError` | `UDINT` |  | Number of requests started with parameter error, for example
“Read Coils” -> “Quantity of coils” = 0. |
| `udiLastTransactionTime` | `UDINT` |  | Transaction time in ms - time difference between request
message send und reply message received. |

---

## ClientRequest (FB)

# ClientRequest (FB)

FUNCTION_BLOCK ABSTRACT ClientRequest EXTENDS CBML.ETrigTo IMPLEMENTS IClientRequest

MODBUS client (master) request base class.

There are specific client request function blocks related to all supported MODBUS “function codes”.

A ClientRequest relies on a [Client](Client.html#client) to provide the communication infrastructure,
this means a ClientRequest needs to be connected to one Client ([ClientSerial](ClientSerial.html#clientserial) or [ClientTCP](ClientTCP.html#clienttcp)) to work with.

Once a client request is triggered (rising edge on xExecute) it is processed by the [Client](Client.html#client) it is connected to.
The Client does process the triggered requests strictly in the order they got triggered (first come, first served).
A successful client request is indicated by xDone=TRUE, a client request in progress is indicated by xBusy=TRUE.
A failed client request is indicated by xError=TRUE, and a specific eErrorID.
ClientRequest does have a timeout (it extends CBML.ETrigTo - udiTimeout in µs) to avoid endless, effectless client operations.
So in general the application should:
- trigger the request with rising edge on xExecute (set xExecute:=TRUE)
- check if request is done (xDone=TRUE) or error occured (xError=TRUE)
- falling edge on xExecute (set xExecute:=FALSE)
- eventually repeat

## Client request errors and timeout

A client request can fail (xError=TRUE) for different reason:

- 
“exception reply” - the server is answering in time, but signals an invalid request.
In this case eErrorID is set to Error.RequestException and eException contains the specific exception code.
This is kind of a normal reply a server can do, because of client request parameters not valid for the server “data model”.

- 
“reply timeout” - the server is not answering in time (udiReplyTimeout - for consistency to CBML.ETrigTo.udiTimeout in µs as well).
This includes incomplete (frames) or invalid replies which are dropped, but does not include “exception replies”.
In this case eErrorID is set to Error.ReplyTimeout.
In general the application can’t do a lot about this type of error except choosing adequate udiReplyTimeout.

- 
“request starvation” - too many client requests triggered in parallel, causing a timeout (see udiTimeout) before server reply or “reply timeout” happens.
In this case eErrorID is set to Error.RequestNotProcessed.
In general the application is responsible to avoid “request starvation”.
The client does process the client requests as fast as possible, but in sequential order.
Processing one client request involves waiting for the server reply to be processed (including eventual “reply timeout”).
In case a number of client requests are triggered in parallel,
processing time and waiting sums up for the subsequent client requests triggered already, but not processed yet.

Because “request starvation” can not be avoided in general, it is recommended to trigger client requests in “daisy chains”
(first client request xDone=TRUE or xError=TRUE triggering second client request) to avoid client “request starvation” at all.

## Client request errors and connection shutdown

In case of a client request there is no other action on client involved - the client connection stays alive.
In case there is a need to disconnect the client (shutdown the client connection either TCP or serial)
on such a single client request error, this has to be done in the application by setting client.xConnect:=FALSE.

## Timeout default

It is not possible to overload member defaults of base classes in IEC61131.
CBML.ETrigTo defaults udiTimeout to 0 which is not optimal for ClientRequest’s
because it’s state machine would get stuck without timeout on “reply timeout” or “request starvation”.
So ClientRequest.fb_init writes udiTimeout to 2s (in µs) initially.
In case you want to chose another udiTimeout you need to assign it explicitly after initializaton (in a PLC application cycle).

## “data item” offset / “data item” numbers

Please note: unlike standard MODBUS, in CODESYS MODBUS the “data item” numbers are equal to the “data addresses”.
The MODBUS standard states: “In the MODBUS data Model each element within a data block is numbered from 1 to n.”
In CODESYS MODBUS the “data items” are numbered from 0 to n-1.

**InOut:**

| Scope | Name | Type | Initial | Comment | Inherited from |
|---|---|---|---|---|---|
| Input | `xExecute` | `BOOL` |  | Rising edge: Starts defined operation
`FALSE`: Resets the defined operation after ready condition was reached | ETrigTo |
| `udiTimeOut` | `UDINT` |  | Max. operating time for executing
[µs], 0: No operating time limit | ETrigTo |
| Output | `xDone` | `BOOL` |  | Ready condition reached | ETrigTo |
| `xBusy` | `BOOL` |  | Operation is running | ETrigTo |
| `xError` | `BOOL` |  | Error condition reached | ETrigTo |
| Inout | `rClient` | [Client](Client.html#client) |  | Reference to [Client](Client.html#client). |  |
| Input | `uiUnitId` | `UINT` | 0 | Unit-Id to send the request to. |  |
| `udiReplyTimeout` | `UDINT` | (50 * 1000) | Reply timeout in µs - accepted maxmimum time between request
message send and reply message receveived - default 50ms. |  |
| `uiMaxRetries` | `UINT` | 0 | Maximum number of request retries in case of “reply
timeout”. |  |
| Output | `eErrorID` | [Error](../../Enums/Error.html#error) |  | Error status |  |
| `eException` | [ExceptionCodes](../../Enums/ExceptionCodes.html#exceptioncodes) |  | Request exception code. |  |
| `uiRetryCnt` | `UINT` | 0 | Number of request retries in case of “reply timeout”. |  |

---

## ClientRequestMaskWriteRegister (FB)

# ClientRequestMaskWriteRegister (FB)

FUNCTION_BLOCK ClientRequestMaskWriteRegister EXTENDS [ClientRequestWriteSingle](ClientRequestWriteSingle.html#clientrequestwritesingle)

MaskWriteRegister client request (FC22).

For details about client request see [ClientRequest](ClientRequest.html#clientrequest).

**InOut:**

| Scope | Name | Type | Initial | Comment | Inherited from |
|---|---|---|---|---|---|
| Input | `xExecute` | `BOOL` |  | Rising edge: Starts defined operation
`FALSE`: Resets the defined operation after ready condition was reached | ETrigTo |
| `udiTimeOut` | `UDINT` |  | Max. operating time for executing
[µs], 0: No operating time limit | ETrigTo |
| Output | `xDone` | `BOOL` |  | Ready condition reached | ETrigTo |
| `xBusy` | `BOOL` |  | Operation is running | ETrigTo |
| `xError` | `BOOL` |  | Error condition reached | ETrigTo |
| Inout | `rClient` | [Client](Client.html#client) |  | Reference to [Client](Client.html#client). | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiUnitId` | `UINT` | 0 | Unit-Id to send the request to. | [ClientRequest](ClientRequest.html#clientrequest) |
| `udiReplyTimeout` | `UDINT` | (50 * 1000) | Reply timeout in µs - accepted maxmimum time between request
message send and reply message receveived - default 50ms. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiMaxRetries` | `UINT` | 0 | Maximum number of request retries in case of “reply
timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Output | `eErrorID` | [Error](../../Enums/Error.html#error) |  | Error status | [ClientRequest](ClientRequest.html#clientrequest) |
| `eException` | [ExceptionCodes](../../Enums/ExceptionCodes.html#exceptioncodes) |  | Request exception code. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiRetryCnt` | `UINT` | 0 | Number of request retries in case of “reply timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiItem` | `UINT` | 0 | “data item” to write. | [ClientRequestWriteSingle](ClientRequestWriteSingle.html#clientrequestwritesingle) |
| `uiAndMask` | `UINT` | 0 | The “AND mask”. |  |
| `uiOrMask` | `UINT` | 0 | The “OR mask”. |  |

---

## ClientRequestRead (FB)

# ClientRequestRead (FB)

FUNCTION_BLOCK ABSTRACT ClientRequestRead EXTENDS [ClientRequest](ClientRequest.html#clientrequest)

Read client request base class for ReadCoils, ReadDiscreteInputs, ReadHoldingRegisters and ReadInputRegisters.

**InOut:**

| Scope | Name | Type | Initial | Comment | Inherited from |
|---|---|---|---|---|---|
| Input | `xExecute` | `BOOL` |  | Rising edge: Starts defined operation
`FALSE`: Resets the defined operation after ready condition was reached | ETrigTo |
| `udiTimeOut` | `UDINT` |  | Max. operating time for executing
[µs], 0: No operating time limit | ETrigTo |
| Output | `xDone` | `BOOL` |  | Ready condition reached | ETrigTo |
| `xBusy` | `BOOL` |  | Operation is running | ETrigTo |
| `xError` | `BOOL` |  | Error condition reached | ETrigTo |
| Inout | `rClient` | [Client](Client.html#client) |  | Reference to [Client](Client.html#client). | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiUnitId` | `UINT` | 0 | Unit-Id to send the request to. | [ClientRequest](ClientRequest.html#clientrequest) |
| `udiReplyTimeout` | `UDINT` | (50 * 1000) | Reply timeout in µs - accepted maxmimum time between request
message send and reply message receveived - default 50ms. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiMaxRetries` | `UINT` | 0 | Maximum number of request retries in case of “reply
timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Output | `eErrorID` | [Error](../../Enums/Error.html#error) |  | Error status | [ClientRequest](ClientRequest.html#clientrequest) |
| `eException` | [ExceptionCodes](../../Enums/ExceptionCodes.html#exceptioncodes) |  | Request exception code. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiRetryCnt` | `UINT` | 0 | Number of request retries in case of “reply timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiStartItem` | `UINT` | 0 | First “data item” to read. |  |
| `uiQuantity` | `UINT` | 1 | Number of “data items” to read.
ReadCoils / ReadDiscreteInputs: 1 to 2000
ReadHoldingRegisters / ReadInputRegisters: 1 to 125 |  |

---

## ClientRequestReadBits (FB)

# ClientRequestReadBits (FB)

FUNCTION_BLOCK ABSTRACT ClientRequestReadBits EXTENDS [ClientRequestRead](ClientRequestRead.html#clientrequestread)

Read client request base class for ReadCoils, ReadDiscreteInputs

**InOut:**

| Scope | Name | Type | Initial | Comment | Inherited from |
|---|---|---|---|---|---|
| Input | `xExecute` | `BOOL` |  | Rising edge: Starts defined operation
`FALSE`: Resets the defined operation after ready condition was reached | ETrigTo |
| `udiTimeOut` | `UDINT` |  | Max. operating time for executing
[µs], 0: No operating time limit | ETrigTo |
| Output | `xDone` | `BOOL` |  | Ready condition reached | ETrigTo |
| `xBusy` | `BOOL` |  | Operation is running | ETrigTo |
| `xError` | `BOOL` |  | Error condition reached | ETrigTo |
| Inout | `rClient` | [Client](Client.html#client) |  | Reference to [Client](Client.html#client). | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiUnitId` | `UINT` | 0 | Unit-Id to send the request to. | [ClientRequest](ClientRequest.html#clientrequest) |
| `udiReplyTimeout` | `UDINT` | (50 * 1000) | Reply timeout in µs - accepted maxmimum time between request
message send and reply message receveived - default 50ms. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiMaxRetries` | `UINT` | 0 | Maximum number of request retries in case of “reply
timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Output | `eErrorID` | [Error](../../Enums/Error.html#error) |  | Error status | [ClientRequest](ClientRequest.html#clientrequest) |
| `eException` | [ExceptionCodes](../../Enums/ExceptionCodes.html#exceptioncodes) |  | Request exception code. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiRetryCnt` | `UINT` | 0 | Number of request retries in case of “reply timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiStartItem` | `UINT` | 0 | First “data item” to read. | [ClientRequestRead](ClientRequestRead.html#clientrequestread) |
| `uiQuantity` | `UINT` | 1 | Number of “data items” to read.
ReadCoils / ReadDiscreteInputs: 1 to 2000
ReadHoldingRegisters / ReadInputRegisters: 1 to 125 | [ClientRequestRead](ClientRequestRead.html#clientrequestread) |
| `pData` | POINTER TO ARRAY [0..0]
OF BOOL | 0 | Pointer to result data array, memory has to be provided by
caller. |  |

---

## ClientRequestReadCoils (FB)

# ClientRequestReadCoils (FB)

FUNCTION_BLOCK ClientRequestReadCoils EXTENDS [ClientRequestReadBits](ClientRequestReadBits.html#clientrequestreadbits)

ReadCoils client request (FC01).

For details about client request see [ClientRequest](ClientRequest.html#clientrequest).

**InOut:**

| Scope | Name | Type | Initial | Comment | Inherited from |
|---|---|---|---|---|---|
| Input | `xExecute` | `BOOL` |  | Rising edge: Starts defined operation
`FALSE`: Resets the defined operation after ready condition was reached | ETrigTo |
| `udiTimeOut` | `UDINT` |  | Max. operating time for executing
[µs], 0: No operating time limit | ETrigTo |
| Output | `xDone` | `BOOL` |  | Ready condition reached | ETrigTo |
| `xBusy` | `BOOL` |  | Operation is running | ETrigTo |
| `xError` | `BOOL` |  | Error condition reached | ETrigTo |
| Inout | `rClient` | [Client](Client.html#client) |  | Reference to [Client](Client.html#client). | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiUnitId` | `UINT` | 0 | Unit-Id to send the request to. | [ClientRequest](ClientRequest.html#clientrequest) |
| `udiReplyTimeout` | `UDINT` | (50 * 1000) | Reply timeout in µs - accepted maxmimum time between request
message send and reply message receveived - default 50ms. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiMaxRetries` | `UINT` | 0 | Maximum number of request retries in case of “reply
timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Output | `eErrorID` | [Error](../../Enums/Error.html#error) |  | Error status | [ClientRequest](ClientRequest.html#clientrequest) |
| `eException` | [ExceptionCodes](../../Enums/ExceptionCodes.html#exceptioncodes) |  | Request exception code. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiRetryCnt` | `UINT` | 0 | Number of request retries in case of “reply timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiStartItem` | `UINT` | 0 | First “data item” to read. | [ClientRequestRead](ClientRequestRead.html#clientrequestread) |
| `uiQuantity` | `UINT` | 1 | Number of “data items” to read.
ReadCoils / ReadDiscreteInputs: 1 to 2000
ReadHoldingRegisters / ReadInputRegisters: 1 to 125 | [ClientRequestRead](ClientRequestRead.html#clientrequestread) |
| `pData` | POINTER TO ARRAY [0..0]
OF BOOL | 0 | Pointer to result data array, memory has to be provided by
caller. | [ClientRequestReadBits](ClientRequestReadBits.html#clientrequestreadbits) |

---

## ClientRequestReadDiscreteInputs (FB)

# ClientRequestReadDiscreteInputs (FB)

FUNCTION_BLOCK ClientRequestReadDiscreteInputs EXTENDS [ClientRequestReadBits](ClientRequestReadBits.html#clientrequestreadbits)

ReadDiscreteInputs client request (FC02).

For details about client request see [ClientRequest](ClientRequest.html#clientrequest).

**InOut:**

| Scope | Name | Type | Initial | Comment | Inherited from |
|---|---|---|---|---|---|
| Input | `xExecute` | `BOOL` |  | Rising edge: Starts defined operation
`FALSE`: Resets the defined operation after ready condition was reached | ETrigTo |
| `udiTimeOut` | `UDINT` |  | Max. operating time for executing
[µs], 0: No operating time limit | ETrigTo |
| Output | `xDone` | `BOOL` |  | Ready condition reached | ETrigTo |
| `xBusy` | `BOOL` |  | Operation is running | ETrigTo |
| `xError` | `BOOL` |  | Error condition reached | ETrigTo |
| Inout | `rClient` | [Client](Client.html#client) |  | Reference to [Client](Client.html#client). | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiUnitId` | `UINT` | 0 | Unit-Id to send the request to. | [ClientRequest](ClientRequest.html#clientrequest) |
| `udiReplyTimeout` | `UDINT` | (50 * 1000) | Reply timeout in µs - accepted maxmimum time between request
message send and reply message receveived - default 50ms. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiMaxRetries` | `UINT` | 0 | Maximum number of request retries in case of “reply
timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Output | `eErrorID` | [Error](../../Enums/Error.html#error) |  | Error status | [ClientRequest](ClientRequest.html#clientrequest) |
| `eException` | [ExceptionCodes](../../Enums/ExceptionCodes.html#exceptioncodes) |  | Request exception code. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiRetryCnt` | `UINT` | 0 | Number of request retries in case of “reply timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiStartItem` | `UINT` | 0 | First “data item” to read. | [ClientRequestRead](ClientRequestRead.html#clientrequestread) |
| `uiQuantity` | `UINT` | 1 | Number of “data items” to read.
ReadCoils / ReadDiscreteInputs: 1 to 2000
ReadHoldingRegisters / ReadInputRegisters: 1 to 125 | [ClientRequestRead](ClientRequestRead.html#clientrequestread) |
| `pData` | POINTER TO ARRAY [0..0]
OF BOOL | 0 | Pointer to result data array, memory has to be provided by
caller. | [ClientRequestReadBits](ClientRequestReadBits.html#clientrequestreadbits) |

---

## ClientRequestReadHoldingRegisters (FB)

# ClientRequestReadHoldingRegisters (FB)

FUNCTION_BLOCK ClientRequestReadHoldingRegisters EXTENDS [ClientRequestReadRegisters](ClientRequestReadRegisters.html#clientrequestreadregisters)

ReadHoldingRegisters client request (FC03).

For details about client request see [ClientRequest](ClientRequest.html#clientrequest).

**InOut:**

| Scope | Name | Type | Initial | Comment | Inherited from |
|---|---|---|---|---|---|
| Input | `xExecute` | `BOOL` |  | Rising edge: Starts defined operation
`FALSE`: Resets the defined operation after ready condition was reached | ETrigTo |
| `udiTimeOut` | `UDINT` |  | Max. operating time for executing
[µs], 0: No operating time limit | ETrigTo |
| Output | `xDone` | `BOOL` |  | Ready condition reached | ETrigTo |
| `xBusy` | `BOOL` |  | Operation is running | ETrigTo |
| `xError` | `BOOL` |  | Error condition reached | ETrigTo |
| Inout | `rClient` | [Client](Client.html#client) |  | Reference to [Client](Client.html#client). | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiUnitId` | `UINT` | 0 | Unit-Id to send the request to. | [ClientRequest](ClientRequest.html#clientrequest) |
| `udiReplyTimeout` | `UDINT` | (50 * 1000) | Reply timeout in µs - accepted maxmimum time between request
message send and reply message receveived - default 50ms. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiMaxRetries` | `UINT` | 0 | Maximum number of request retries in case of “reply
timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Output | `eErrorID` | [Error](../../Enums/Error.html#error) |  | Error status | [ClientRequest](ClientRequest.html#clientrequest) |
| `eException` | [ExceptionCodes](../../Enums/ExceptionCodes.html#exceptioncodes) |  | Request exception code. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiRetryCnt` | `UINT` | 0 | Number of request retries in case of “reply timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiStartItem` | `UINT` | 0 | First “data item” to read. | [ClientRequestRead](ClientRequestRead.html#clientrequestread) |
| `uiQuantity` | `UINT` | 1 | Number of “data items” to read.
ReadCoils / ReadDiscreteInputs: 1 to 2000
ReadHoldingRegisters / ReadInputRegisters: 1 to 125 | [ClientRequestRead](ClientRequestRead.html#clientrequestread) |
| `pData` | POINTER TO ARRAY [0..0]
OF UINT | 0 | Pointer to result data array, memory has to be provided by
caller. | [ClientRequestReadRegisters](ClientRequestReadRegisters.html#clientrequestreadregisters) |

---

## ClientRequestReadInputRegisters (FB)

# ClientRequestReadInputRegisters (FB)

FUNCTION_BLOCK ClientRequestReadInputRegisters EXTENDS [ClientRequestReadRegisters](ClientRequestReadRegisters.html#clientrequestreadregisters)

ReadInputRegisters client request (FC04).

For details about client request see [ClientRequest](ClientRequest.html#clientrequest).

**InOut:**

| Scope | Name | Type | Initial | Comment | Inherited from |
|---|---|---|---|---|---|
| Input | `xExecute` | `BOOL` |  | Rising edge: Starts defined operation
`FALSE`: Resets the defined operation after ready condition was reached | ETrigTo |
| `udiTimeOut` | `UDINT` |  | Max. operating time for executing
[µs], 0: No operating time limit | ETrigTo |
| Output | `xDone` | `BOOL` |  | Ready condition reached | ETrigTo |
| `xBusy` | `BOOL` |  | Operation is running | ETrigTo |
| `xError` | `BOOL` |  | Error condition reached | ETrigTo |
| Inout | `rClient` | [Client](Client.html#client) |  | Reference to [Client](Client.html#client). | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiUnitId` | `UINT` | 0 | Unit-Id to send the request to. | [ClientRequest](ClientRequest.html#clientrequest) |
| `udiReplyTimeout` | `UDINT` | (50 * 1000) | Reply timeout in µs - accepted maxmimum time between request
message send and reply message receveived - default 50ms. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiMaxRetries` | `UINT` | 0 | Maximum number of request retries in case of “reply
timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Output | `eErrorID` | [Error](../../Enums/Error.html#error) |  | Error status | [ClientRequest](ClientRequest.html#clientrequest) |
| `eException` | [ExceptionCodes](../../Enums/ExceptionCodes.html#exceptioncodes) |  | Request exception code. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiRetryCnt` | `UINT` | 0 | Number of request retries in case of “reply timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiStartItem` | `UINT` | 0 | First “data item” to read. | [ClientRequestRead](ClientRequestRead.html#clientrequestread) |
| `uiQuantity` | `UINT` | 1 | Number of “data items” to read.
ReadCoils / ReadDiscreteInputs: 1 to 2000
ReadHoldingRegisters / ReadInputRegisters: 1 to 125 | [ClientRequestRead](ClientRequestRead.html#clientrequestread) |
| `pData` | POINTER TO ARRAY [0..0]
OF UINT | 0 | Pointer to result data array, memory has to be provided by
caller. | [ClientRequestReadRegisters](ClientRequestReadRegisters.html#clientrequestreadregisters) |

---

## ClientRequestReadRegisters (FB)

# ClientRequestReadRegisters (FB)

FUNCTION_BLOCK ABSTRACT ClientRequestReadRegisters EXTENDS [ClientRequestRead](ClientRequestRead.html#clientrequestread)

Read client request base class for ReadHoldingRegisters and ReadInputRegisters

**InOut:**

| Scope | Name | Type | Initial | Comment | Inherited from |
|---|---|---|---|---|---|
| Input | `xExecute` | `BOOL` |  | Rising edge: Starts defined operation
`FALSE`: Resets the defined operation after ready condition was reached | ETrigTo |
| `udiTimeOut` | `UDINT` |  | Max. operating time for executing
[µs], 0: No operating time limit | ETrigTo |
| Output | `xDone` | `BOOL` |  | Ready condition reached | ETrigTo |
| `xBusy` | `BOOL` |  | Operation is running | ETrigTo |
| `xError` | `BOOL` |  | Error condition reached | ETrigTo |
| Inout | `rClient` | [Client](Client.html#client) |  | Reference to [Client](Client.html#client). | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiUnitId` | `UINT` | 0 | Unit-Id to send the request to. | [ClientRequest](ClientRequest.html#clientrequest) |
| `udiReplyTimeout` | `UDINT` | (50 * 1000) | Reply timeout in µs - accepted maxmimum time between request
message send and reply message receveived - default 50ms. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiMaxRetries` | `UINT` | 0 | Maximum number of request retries in case of “reply
timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Output | `eErrorID` | [Error](../../Enums/Error.html#error) |  | Error status | [ClientRequest](ClientRequest.html#clientrequest) |
| `eException` | [ExceptionCodes](../../Enums/ExceptionCodes.html#exceptioncodes) |  | Request exception code. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiRetryCnt` | `UINT` | 0 | Number of request retries in case of “reply timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiStartItem` | `UINT` | 0 | First “data item” to read. | [ClientRequestRead](ClientRequestRead.html#clientrequestread) |
| `uiQuantity` | `UINT` | 1 | Number of “data items” to read.
ReadCoils / ReadDiscreteInputs: 1 to 2000
ReadHoldingRegisters / ReadInputRegisters: 1 to 125 | [ClientRequestRead](ClientRequestRead.html#clientrequestread) |
| `pData` | POINTER TO ARRAY [0..0]
OF UINT | 0 | Pointer to result data array, memory has to be provided by
caller. |  |

---

## ClientRequestReadWriteMultipleRegisters (FB)

# ClientRequestReadWriteMultipleRegisters (FB)

FUNCTION_BLOCK ClientRequestReadWriteMultipleRegisters EXTENDS [ClientRequest](ClientRequest.html#clientrequest)

ReadWriteMultipleRegister client request (FC23).

For details about client request see [ClientRequest](ClientRequest.html#clientrequest).

Please note: The write operation is performed before the read.

**InOut:**

| Scope | Name | Type | Initial | Comment | Inherited from |
|---|---|---|---|---|---|
| Input | `xExecute` | `BOOL` |  | Rising edge: Starts defined operation
`FALSE`: Resets the defined operation after ready condition was reached | ETrigTo |
| `udiTimeOut` | `UDINT` |  | Max. operating time for executing
[µs], 0: No operating time limit | ETrigTo |
| Output | `xDone` | `BOOL` |  | Ready condition reached | ETrigTo |
| `xBusy` | `BOOL` |  | Operation is running | ETrigTo |
| `xError` | `BOOL` |  | Error condition reached | ETrigTo |
| Inout | `rClient` | [Client](Client.html#client) |  | Reference to [Client](Client.html#client). | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiUnitId` | `UINT` | 0 | Unit-Id to send the request to. | [ClientRequest](ClientRequest.html#clientrequest) |
| `udiReplyTimeout` | `UDINT` | (50 * 1000) | Reply timeout in µs - accepted maxmimum time between request
message send and reply message receveived - default 50ms. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiMaxRetries` | `UINT` | 0 | Maximum number of request retries in case of “reply
timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Output | `eErrorID` | [Error](../../Enums/Error.html#error) |  | Error status | [ClientRequest](ClientRequest.html#clientrequest) |
| `eException` | [ExceptionCodes](../../Enums/ExceptionCodes.html#exceptioncodes) |  | Request exception code. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiRetryCnt` | `UINT` | 0 | Number of request retries in case of “reply timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiWriteStartItem` | `UINT` | 0 | First “data item” to write. |  |
| `uiWriteQuantity` | `UINT` | 1 | Number of “data items” to write. |  |
| `pWriteData` | POINTER TO ARRAY [0..0]
OF UINT | 0 | Pointer to write data array. |  |
| `uiReadStartItem` | `UINT` | 0 | First “data item” to read. |  |
| `uiReadQuantity` | `UINT` | 1 | Number of “data items” to read. |  |
| `pReadData` | POINTER TO ARRAY [0..0]
OF UINT | 0 | Pointer to read data array, memory has to be provided by
caller. |  |

---

## ClientRequestWriteMultiple (FB)

# ClientRequestWriteMultiple (FB)

FUNCTION_BLOCK ABSTRACT ClientRequestWriteMultiple EXTENDS [ClientRequest](ClientRequest.html#clientrequest)

Write client request base class for WriteMultipleCoils, WriteMultipleRegisters

**InOut:**

| Scope | Name | Type | Initial | Comment | Inherited from |
|---|---|---|---|---|---|
| Input | `xExecute` | `BOOL` |  | Rising edge: Starts defined operation
`FALSE`: Resets the defined operation after ready condition was reached | ETrigTo |
| `udiTimeOut` | `UDINT` |  | Max. operating time for executing
[µs], 0: No operating time limit | ETrigTo |
| Output | `xDone` | `BOOL` |  | Ready condition reached | ETrigTo |
| `xBusy` | `BOOL` |  | Operation is running | ETrigTo |
| `xError` | `BOOL` |  | Error condition reached | ETrigTo |
| Inout | `rClient` | [Client](Client.html#client) |  | Reference to [Client](Client.html#client). | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiUnitId` | `UINT` | 0 | Unit-Id to send the request to. | [ClientRequest](ClientRequest.html#clientrequest) |
| `udiReplyTimeout` | `UDINT` | (50 * 1000) | Reply timeout in µs - accepted maxmimum time between request
message send and reply message receveived - default 50ms. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiMaxRetries` | `UINT` | 0 | Maximum number of request retries in case of “reply
timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Output | `eErrorID` | [Error](../../Enums/Error.html#error) |  | Error status | [ClientRequest](ClientRequest.html#clientrequest) |
| `eException` | [ExceptionCodes](../../Enums/ExceptionCodes.html#exceptioncodes) |  | Request exception code. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiRetryCnt` | `UINT` | 0 | Number of request retries in case of “reply timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiStartItem` | `UINT` | 0 | First “data item” to write. |  |
| `uiQuantity` | `UINT` | 1 | Number of “data items” to write. |  |

---

## ClientRequestWriteMultipleCoils (FB)

# ClientRequestWriteMultipleCoils (FB)

FUNCTION_BLOCK ClientRequestWriteMultipleCoils EXTENDS [ClientRequestWriteMultiple](ClientRequestWriteMultiple.html#clientrequestwritemultiple)

WriteMultipleCoils client request (FC15).

For details about client request see [ClientRequest](ClientRequest.html#clientrequest).

**InOut:**

| Scope | Name | Type | Initial | Comment | Inherited from |
|---|---|---|---|---|---|
| Input | `xExecute` | `BOOL` |  | Rising edge: Starts defined operation
`FALSE`: Resets the defined operation after ready condition was reached | ETrigTo |
| `udiTimeOut` | `UDINT` |  | Max. operating time for executing
[µs], 0: No operating time limit | ETrigTo |
| Output | `xDone` | `BOOL` |  | Ready condition reached | ETrigTo |
| `xBusy` | `BOOL` |  | Operation is running | ETrigTo |
| `xError` | `BOOL` |  | Error condition reached | ETrigTo |
| Inout | `rClient` | [Client](Client.html#client) |  | Reference to [Client](Client.html#client). | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiUnitId` | `UINT` | 0 | Unit-Id to send the request to. | [ClientRequest](ClientRequest.html#clientrequest) |
| `udiReplyTimeout` | `UDINT` | (50 * 1000) | Reply timeout in µs - accepted maxmimum time between request
message send and reply message receveived - default 50ms. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiMaxRetries` | `UINT` | 0 | Maximum number of request retries in case of “reply
timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Output | `eErrorID` | [Error](../../Enums/Error.html#error) |  | Error status | [ClientRequest](ClientRequest.html#clientrequest) |
| `eException` | [ExceptionCodes](../../Enums/ExceptionCodes.html#exceptioncodes) |  | Request exception code. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiRetryCnt` | `UINT` | 0 | Number of request retries in case of “reply timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiStartItem` | `UINT` | 0 | First “data item” to write. | [ClientRequestWriteMultiple](ClientRequestWriteMultiple.html#clientrequestwritemultiple) |
| `uiQuantity` | `UINT` | 1 | Number of “data items” to write. | [ClientRequestWriteMultiple](ClientRequestWriteMultiple.html#clientrequestwritemultiple) |
| `pData` | POINTER TO ARRAY [0..0]
OF BOOL | 0 | Pointer to write data array. |  |

---

## ClientRequestWriteMultipleRegisters (FB)

# ClientRequestWriteMultipleRegisters (FB)

FUNCTION_BLOCK ClientRequestWriteMultipleRegisters EXTENDS [ClientRequestWriteMultiple](ClientRequestWriteMultiple.html#clientrequestwritemultiple)

WriteMultipleRegisters client request (FC16).

For details about client request see [ClientRequest](ClientRequest.html#clientrequest).

**InOut:**

| Scope | Name | Type | Initial | Comment | Inherited from |
|---|---|---|---|---|---|
| Input | `xExecute` | `BOOL` |  | Rising edge: Starts defined operation
`FALSE`: Resets the defined operation after ready condition was reached | ETrigTo |
| `udiTimeOut` | `UDINT` |  | Max. operating time for executing
[µs], 0: No operating time limit | ETrigTo |
| Output | `xDone` | `BOOL` |  | Ready condition reached | ETrigTo |
| `xBusy` | `BOOL` |  | Operation is running | ETrigTo |
| `xError` | `BOOL` |  | Error condition reached | ETrigTo |
| Inout | `rClient` | [Client](Client.html#client) |  | Reference to [Client](Client.html#client). | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiUnitId` | `UINT` | 0 | Unit-Id to send the request to. | [ClientRequest](ClientRequest.html#clientrequest) |
| `udiReplyTimeout` | `UDINT` | (50 * 1000) | Reply timeout in µs - accepted maxmimum time between request
message send and reply message receveived - default 50ms. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiMaxRetries` | `UINT` | 0 | Maximum number of request retries in case of “reply
timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Output | `eErrorID` | [Error](../../Enums/Error.html#error) |  | Error status | [ClientRequest](ClientRequest.html#clientrequest) |
| `eException` | [ExceptionCodes](../../Enums/ExceptionCodes.html#exceptioncodes) |  | Request exception code. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiRetryCnt` | `UINT` | 0 | Number of request retries in case of “reply timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiStartItem` | `UINT` | 0 | First “data item” to write. | [ClientRequestWriteMultiple](ClientRequestWriteMultiple.html#clientrequestwritemultiple) |
| `uiQuantity` | `UINT` | 1 | Number of “data items” to write. | [ClientRequestWriteMultiple](ClientRequestWriteMultiple.html#clientrequestwritemultiple) |
| `pData` | POINTER TO ARRAY [0..0]
OF UINT | 0 | Pointer to write data array. |  |

---

## ClientRequestWriteSingle (FB)

# ClientRequestWriteSingle (FB)

FUNCTION_BLOCK ABSTRACT ClientRequestWriteSingle EXTENDS [ClientRequest](ClientRequest.html#clientrequest)

WriteSingle client request base class for WriteSingleCoil, WriteSingleRegister and MaskWriteRegister.

**InOut:**

| Scope | Name | Type | Initial | Comment | Inherited from |
|---|---|---|---|---|---|
| Input | `xExecute` | `BOOL` |  | Rising edge: Starts defined operation
`FALSE`: Resets the defined operation after ready condition was reached | ETrigTo |
| `udiTimeOut` | `UDINT` |  | Max. operating time for executing
[µs], 0: No operating time limit | ETrigTo |
| Output | `xDone` | `BOOL` |  | Ready condition reached | ETrigTo |
| `xBusy` | `BOOL` |  | Operation is running | ETrigTo |
| `xError` | `BOOL` |  | Error condition reached | ETrigTo |
| Inout | `rClient` | [Client](Client.html#client) |  | Reference to [Client](Client.html#client). | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiUnitId` | `UINT` | 0 | Unit-Id to send the request to. | [ClientRequest](ClientRequest.html#clientrequest) |
| `udiReplyTimeout` | `UDINT` | (50 * 1000) | Reply timeout in µs - accepted maxmimum time between request
message send and reply message receveived - default 50ms. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiMaxRetries` | `UINT` | 0 | Maximum number of request retries in case of “reply
timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Output | `eErrorID` | [Error](../../Enums/Error.html#error) |  | Error status | [ClientRequest](ClientRequest.html#clientrequest) |
| `eException` | [ExceptionCodes](../../Enums/ExceptionCodes.html#exceptioncodes) |  | Request exception code. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiRetryCnt` | `UINT` | 0 | Number of request retries in case of “reply timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiItem` | `UINT` | 0 | “data item” to write. |  |

---

## ClientRequestWriteSingleCoil (FB)

# ClientRequestWriteSingleCoil (FB)

FUNCTION_BLOCK ClientRequestWriteSingleCoil EXTENDS [ClientRequestWriteSingle](ClientRequestWriteSingle.html#clientrequestwritesingle)

WriteSingleCoil client request (FC05).

For details about client request see [ClientRequest](ClientRequest.html#clientrequest).

**InOut:**

| Scope | Name | Type | Initial | Comment | Inherited from |
|---|---|---|---|---|---|
| Input | `xExecute` | `BOOL` |  | Rising edge: Starts defined operation
`FALSE`: Resets the defined operation after ready condition was reached | ETrigTo |
| `udiTimeOut` | `UDINT` |  | Max. operating time for executing
[µs], 0: No operating time limit | ETrigTo |
| Output | `xDone` | `BOOL` |  | Ready condition reached | ETrigTo |
| `xBusy` | `BOOL` |  | Operation is running | ETrigTo |
| `xError` | `BOOL` |  | Error condition reached | ETrigTo |
| Inout | `rClient` | [Client](Client.html#client) |  | Reference to [Client](Client.html#client). | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiUnitId` | `UINT` | 0 | Unit-Id to send the request to. | [ClientRequest](ClientRequest.html#clientrequest) |
| `udiReplyTimeout` | `UDINT` | (50 * 1000) | Reply timeout in µs - accepted maxmimum time between request
message send and reply message receveived - default 50ms. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiMaxRetries` | `UINT` | 0 | Maximum number of request retries in case of “reply
timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Output | `eErrorID` | [Error](../../Enums/Error.html#error) |  | Error status | [ClientRequest](ClientRequest.html#clientrequest) |
| `eException` | [ExceptionCodes](../../Enums/ExceptionCodes.html#exceptioncodes) |  | Request exception code. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiRetryCnt` | `UINT` | 0 | Number of request retries in case of “reply timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiItem` | `UINT` | 0 | “data item” to write. | [ClientRequestWriteSingle](ClientRequestWriteSingle.html#clientrequestwritesingle) |
| `xValue` | `BOOL` | FALSE |  |  |

---

## ClientRequestWriteSingleRegister (FB)

# ClientRequestWriteSingleRegister (FB)

FUNCTION_BLOCK ClientRequestWriteSingleRegister EXTENDS [ClientRequestWriteSingle](ClientRequestWriteSingle.html#clientrequestwritesingle)

WriteSingleRegister client request (FC06).

For details about client request see [ClientRequest](ClientRequest.html#clientrequest).

**InOut:**

| Scope | Name | Type | Initial | Comment | Inherited from |
|---|---|---|---|---|---|
| Input | `xExecute` | `BOOL` |  | Rising edge: Starts defined operation
`FALSE`: Resets the defined operation after ready condition was reached | ETrigTo |
| `udiTimeOut` | `UDINT` |  | Max. operating time for executing
[µs], 0: No operating time limit | ETrigTo |
| Output | `xDone` | `BOOL` |  | Ready condition reached | ETrigTo |
| `xBusy` | `BOOL` |  | Operation is running | ETrigTo |
| `xError` | `BOOL` |  | Error condition reached | ETrigTo |
| Inout | `rClient` | [Client](Client.html#client) |  | Reference to [Client](Client.html#client). | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiUnitId` | `UINT` | 0 | Unit-Id to send the request to. | [ClientRequest](ClientRequest.html#clientrequest) |
| `udiReplyTimeout` | `UDINT` | (50 * 1000) | Reply timeout in µs - accepted maxmimum time between request
message send and reply message receveived - default 50ms. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiMaxRetries` | `UINT` | 0 | Maximum number of request retries in case of “reply
timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Output | `eErrorID` | [Error](../../Enums/Error.html#error) |  | Error status | [ClientRequest](ClientRequest.html#clientrequest) |
| `eException` | [ExceptionCodes](../../Enums/ExceptionCodes.html#exceptioncodes) |  | Request exception code. | [ClientRequest](ClientRequest.html#clientrequest) |
| `uiRetryCnt` | `UINT` | 0 | Number of request retries in case of “reply timeout”. | [ClientRequest](ClientRequest.html#clientrequest) |
| Input | `uiItem` | `UINT` | 0 | “data item” to write. | [ClientRequestWriteSingle](ClientRequestWriteSingle.html#clientrequestwritesingle) |
| `uiValue` | `UINT` | 0 |  |  |

---

## ClientSerial (FB)

# ClientSerial (FB)

FUNCTION_BLOCK ClientSerial EXTENDS [Client](Client.html#client) IMPLEMENTS ISysComUser

MODBUS serial client (master).

Please note: some input variables related to connection configuration are read when rising edge on xConnect occurs.
To change connection configuration the application needs to
- disconnect (xConnect := FALSE and execute the FB)
- modify the related input variables
- connect (xConnect := TRUE and execute the FB)

The [Client](Client.html#client) provides some statistics of sent request messages and received valid reply messages.
Invalid messages are dropped at the communication level, so doesnt appear in the statistics.
To analyse situations where invalid reply messages might occur, you can use udiLogOptions with LoggingOptions.WarnOnReceivedInvalidFrames.

The maximum number of serial ports usable with ClientSerial / ServerSerial is limited to MAX_NUM_COMPORTS.
In case there is a need to use more serial ports, anyone can set the library parameter MAX_NUM_COMPORTS within an application - see Library Manager -> ModbusFB -> Parameter -> MAX_NUM_COMPORTS.

Please visit [https://forge.codesys.com/prj/codesys-example/modbus/home](https://forge.codesys.com/prj/codesys-example/modbus/home) to find examples.

**InOut:**

| Scope | Name | Type | Initial | Comment | Inherited from |
|---|---|---|---|---|---|
| Input | `xConnect` | `BOOL` | FALSE | Connect to server (slave). | [Client](Client.html#client) |
| Output | `xConnected` | `BOOL` |  | Client (master) is connected to server (slave). | [Client](Client.html#client) |
| `xError` | `BOOL` |  | Error | [Client](Client.html#client) |
| `eErrorID` | [Error](../../Enums/Error.html#error) |  | Error status | [Client](Client.html#client) |
| `udiNumMsgSent` | `UDINT` |  | Number of request messages send since connect. | [Client](Client.html#client) |
| `udiNumMsgReply` | `UDINT` |  | Number of reply messages received since connect. | [Client](Client.html#client) |
| `udiNumMsgExcReply` | `UDINT` |  | Number of exception reply messages received since connect. | [Client](Client.html#client) |
| `udiNumMsgExcReplyIllFct` | `UDINT` |  | Number of exception reply messages received since connect,
signaling illegal function. | [Client](Client.html#client) |
| `udiNumMsgExcReplyIllDataAdr` | `UDINT` |  | Number of exception reply messages received since connect,
signaling illegal data address. | [Client](Client.html#client) |
| `udiNumReplyTimeouts` | `UDINT` |  | Number of reply timeouts since connect. | [Client](Client.html#client) |
| `udiNumReqNotProcessed` | `UDINT` |  | Number of requests not processed in time (“request
starvation”) since connect. | [Client](Client.html#client) |
| `udiNumReqParamError` | `UDINT` |  | Number of requests started with parameter error, for example
“Read Coils” -> “Quantity of coils” = 0. | [Client](Client.html#client) |
| `udiLastTransactionTime` | `UDINT` |  | Transaction time in ms - time difference between request
message send und reply message received. | [Client](Client.html#client) |
| Input | `iPort` | `SysCom.SYS_COM_PORTS` | SysCom.SYS_COM_PORTS.SYS_COMPORT_NONE | Serial port, only read when rising edge on xConnect occurs. |  |
| `dwBaudrate` | `SysCom.SYS_COM_BAUDRATE` | SysCom.SYS_COM_BAUDRATE.SYS_BR_115200 | Baud rate, only read when rising edge on xConnect occurs. |  |
| `byDataBits` | `BYTE` | 8 | Number of data bits/BYTE, 5-8, only read when rising edge on
xConnect occurs. |  |
| `eParity` | `SysCom.SYS_COM_PARITY` | SysCom.SYS_COM_PARITY.SYS_NOPARITY | Parity, only read when rising edge on xConnect occurs. |  |
| `eStopBits` | `SysCom.SYS_COM_STOPBITS` | SysCom.SYS_COM_STOPBITS.SYS_ONESTOPBIT | Stop bits, only read when rising edge on xConnect occurs. |  |
| `eDTRcontrol` | `SYS_COM_DTR_CONTROL` | SysCom.SYS_COM_DTR_CONTROL.SYS_DTR_CONTROL_DISABLE | DTR control, only read when rising edge on xConnect occurs. |  |
| `eRTScontrol` | `SysCom.SYS_COM_RTS_CONTROL` | SysCom.SYS_COM_RTS_CONTROL.SYS_RTS_CONTROL_DISABLE | RTS control, only read when rising edge on xConnect occurs. |  |
| `eRtuAscii` | [RtuAscii](../../Enums/RtuAscii.html#rtuascii) | RtuAscii.RTU | RTU / ASCII, only read when rising edge on xConnect occurs. |  |
| `udiLogOptions` | `UDINT` | LoggingOptions.ClientConnectDisconnect | Logging options. |  |

---

## ClientTCP (FB)

# ClientTCP (FB)

FUNCTION_BLOCK ClientTCP EXTENDS [Client](Client.html#client)

MODBUS TCP client (master).

Please note: some input variables related to connection configuration are read when rising edge on xConnect occurs.
To change connection configuration the application needs to
- disconnect (xConnect := FALSE and execute the FB)
- modify the related input variables
- connect (xConnect := TRUE and execute the FB)

The [Client](Client.html#client) provides some statistics of sent request messages and received valid reply messages.
Invalid messages are dropped at the communication level, so doesnt appear in the statistics.
To analyse situations where invalid reply messages might occur, you can use udiLogOptions with LoggingOptions.WarnOnReceivedInvalidFrames.

Please visit [https://forge.codesys.com/prj/codesys-example/modbus/home](https://forge.codesys.com/prj/codesys-example/modbus/home) to find examples.

**InOut:**

| Scope | Name | Type | Initial | Comment | Inherited from |
|---|---|---|---|---|---|
| Input | `xConnect` | `BOOL` | FALSE | Connect to server (slave). | [Client](Client.html#client) |
| Output | `xConnected` | `BOOL` |  | Client (master) is connected to server (slave). | [Client](Client.html#client) |
| `xError` | `BOOL` |  | Error | [Client](Client.html#client) |
| `eErrorID` | [Error](../../Enums/Error.html#error) |  | Error status | [Client](Client.html#client) |
| `udiNumMsgSent` | `UDINT` |  | Number of request messages send since connect. | [Client](Client.html#client) |
| `udiNumMsgReply` | `UDINT` |  | Number of reply messages received since connect. | [Client](Client.html#client) |
| `udiNumMsgExcReply` | `UDINT` |  | Number of exception reply messages received since connect. | [Client](Client.html#client) |
| `udiNumMsgExcReplyIllFct` | `UDINT` |  | Number of exception reply messages received since connect,
signaling illegal function. | [Client](Client.html#client) |
| `udiNumMsgExcReplyIllDataAdr` | `UDINT` |  | Number of exception reply messages received since connect,
signaling illegal data address. | [Client](Client.html#client) |
| `udiNumReplyTimeouts` | `UDINT` |  | Number of reply timeouts since connect. | [Client](Client.html#client) |
| `udiNumReqNotProcessed` | `UDINT` |  | Number of requests not processed in time (“request
starvation”) since connect. | [Client](Client.html#client) |
| `udiNumReqParamError` | `UDINT` |  | Number of requests started with parameter error, for example
“Read Coils” -> “Quantity of coils” = 0. | [Client](Client.html#client) |
| `udiLastTransactionTime` | `UDINT` |  | Transaction time in ms - time difference between request
message send und reply message received. | [Client](Client.html#client) |
| Input | `aIPaddr` | ARRAY [0..3] OF BYTE | [255, 255, 255, 255] | ETH server (slave) address, only read when rising edge on
xConnect occurs. |  |
| `uiPort` | `UINT` | 502 | ETH server (slave) port, only read when rising edge on
xConnect occurs. |  |
| `tConnnectTimeOut` | `TIME` | TIME#1s0ms | Connect timeout (in milliseconds), only read when rising
edge on xConnect occurs. |  |
| `udiLogOptions` | `UDINT` | LoggingOptions.ClientConnectDisconnect | Logging options. |  |

---

## Client

# Client

- [Client (FunctionBlock)](Client.html)

- [ClientRequest (FunctionBlock)](ClientRequest.html)

- [Client request errors and timeout](ClientRequest.html#client-request-errors-and-timeout)

- [Client request errors and connection shutdown](ClientRequest.html#client-request-errors-and-connection-shutdown)

- [Timeout default](ClientRequest.html#timeout-default)

- [“data item” offset / “data item” numbers](ClientRequest.html#data-item-offset-data-item-numbers)

- [ClientRequestMaskWriteRegister (FunctionBlock)](ClientRequestMaskWriteRegister.html)

- [ClientRequestRead (FunctionBlock)](ClientRequestRead.html)

- [ClientRequestReadBits (FunctionBlock)](ClientRequestReadBits.html)

- [ClientRequestReadCoils (FunctionBlock)](ClientRequestReadCoils.html)

- [ClientRequestReadDiscreteInputs (FunctionBlock)](ClientRequestReadDiscreteInputs.html)

- [ClientRequestReadHoldingRegisters (FunctionBlock)](ClientRequestReadHoldingRegisters.html)

- [ClientRequestReadInputRegisters (FunctionBlock)](ClientRequestReadInputRegisters.html)

- [ClientRequestReadRegisters (FunctionBlock)](ClientRequestReadRegisters.html)

- [ClientRequestReadWriteMultipleRegisters (FunctionBlock)](ClientRequestReadWriteMultipleRegisters.html)

- [ClientRequestWriteMultiple (FunctionBlock)](ClientRequestWriteMultiple.html)

- [ClientRequestWriteMultipleCoils (FunctionBlock)](ClientRequestWriteMultipleCoils.html)

- [ClientRequestWriteMultipleRegisters (FunctionBlock)](ClientRequestWriteMultipleRegisters.html)

- [ClientRequestWriteSingle (FunctionBlock)](ClientRequestWriteSingle.html)

- [ClientRequestWriteSingleCoil (FunctionBlock)](ClientRequestWriteSingleCoil.html)

- [ClientRequestWriteSingleRegister (FunctionBlock)](ClientRequestWriteSingleRegister.html)

- [ClientSerial (FunctionBlock)](ClientSerial.html)

- [ClientTCP (FunctionBlock)](ClientTCP.html)

---

# Server Function Blocks

## ExampleDataModel (FB)

# ExampleDataModel (FB)

FUNCTION_BLOCK ExampleDataModel

Simple “data model” example, contains four memory-separated sections containg two:
- “discrete inputs”
- “coils”
- “input registers”
- “holding registers”
“data item” start index for all sections is 5

**InOut:**

| Scope | Name | Type | Initial | Comment |
|---|---|---|---|---|
| Output | `tableDefs` | [TableDefinitions](../../Structs/TableDefinitions.html#tabledefinitions) | STRUCT(tableDiscreteInputs := STRUCT(uiNumSections := (SIZEOF(_aDiscreteInputsSections) / SIZEOF(_aDiscreteInputsSections[0])), pSections := ADR(_aDiscreteInputsSections[0])), tableCoils := STRUCT(uiNumSections := (SIZEOF(_aCoilsSections) / SIZEOF(_aCoilsSections[0])), pSections := ADR(_aCoilsSections[0])), tableInputRegisters := STRUCT(uiNumSections := (SIZEOF(_aInputRegistersSections) / SIZEOF(_aInputRegistersSections[0])), pSections := ADR(_aInputRegistersSections[0])), tableHoldingRegisters := STRUCT(uiNumSections := (SIZEOF(_aHoldingRegistersSections) / SIZEOF(_aHoldingRegistersSections[0])), pSections := ADR(_aHoldingRegistersSections[0]))) | the “data model” tables |

---

## Server (FB)

# Server (FB)

FUNCTION_BLOCK ABSTRACT Server

MODBUS server (slave) base class.

## Supported function codes

Supported function codes can be configured, see fcsSupported.

By default the MODBUS server supports:

- 
ReadCoils

- 
ReadDiscreteInputs

- 
ReadHoldingRegisters

- 
ReadInputRegisters

- 
WriteSingleCoil

- 
WriteSingleRegister

- 
WriteMultipleRegisters

- 
ReadWriteMultipleRegisters

Optionally it supports also:

- 
MaskWriteRegister

## “data model”

The “data model” allows:

- 
non-consecutive index for the “data items” (for example: index 0..9, 20..29)

- 
multiple (non-consecutive) memory blocks for “data items” in one “data block” (for example: index 0..9 => memory block 1, index 20..29 => memory block 2)

- 
not-memory-mapped “data items” (user code needs to be written to handle reads/writes for those “data items”)

- 
“discrete inputs” / “coils” : data item size 1 bit or 8 bit (basically: ARRAY [0..numBits/8] OF BYTE vs. ARRAY [0..numBits-1] OF BOOL)

- 
“input registers” / “holding registers” : data item size of 16 bit (basically: ARRAY [0..numRegisters-1] OF UDINT)

- 
overlapping memory blocks, could overlap “registers” with “registers” as well as “registers” with “discrete inputs” / “coils” (caution - hard to use feature)

To support all this the “data model” ([TableDefinitions](../../Structs/TableDefinitions.html#tabledefinitions)) defines zero or more [TableSection](../../Structs/TableSection.html#tablesection) for each of the MODBUS “primary tables” ([TableDefinition](../../Structs/TableDefinition.html#tabledefinition)).

Some more or less obvious limitations:

- 
all “data items” in one section need to have the same TableSection.uiDataItemSize

- 
all “data item” index in one “primary table” have to be unique, so no section index overlap is allowed of course

- 
read/write requests must not span more than one section

## “data item” offset / “data item” numbers

Please note: unlike standard MODBUS, in CODESYS MODBUS the “data item” numbers are equal to the “data addresses”.
The MODBUS standard states: “In the MODBUS data Model each element within a data block is numbered from 1 to n.”
In CODESYS MODBUS the “data items” are numbered from 0 to n-1.

**InOut:**

| Scope | Name | Type | Initial | Comment |
|---|---|---|---|---|
| Input | `xEnable` | `BOOL` | FALSE | Enables the server, take over the configuration information fcsSupported and dataModel.
If the “data model” (tableDefinitions) contains configuration errors, the Server will not got busy (xBusy = FALSE). |
| `fcsSupported` | [SupportedFcs](../../Structs/SupportedFcs.html#supportedfcs) | Constants.SUPPORTED_FCS_SIMPLE_SERVER | Supported “function codes”, accepted at xEnable FALSE => TRUE.
In case fcsSupported is not assigned by the application it defaults to [Constants.SUPPORTED_FCS_SIMPLE_SERVER](../../GlobalConstants/Constants.html#constants-supported-fcs-simple-server). |
| `dataModel` | [TableDefinitions](../../Structs/TableDefinitions.html#tabledefinitions) |  | “data model”, accepted at xEnable FALSE => TRUE. |
| `tInactivityInfoTime` | `UDINT` | 0 | “inactivity info time” (in milliseconds).
If no valid requests are received in this time xInactive is signaling inactivity - default = 0 -> no “inactivity info”. |
| Output | `xRunning` | `BOOL` |  | Server is up and running, waiting for requests. |
| `xError` | `BOOL` |  | Error |
| `eErrorID` | [Error](../../Enums/Error.html#error) |  | Error status |
| `xInactive` | `BOOL` |  | No valid requests received for tInactivityTimeOut. |
| `udiNumMsgRecv` | `UDINT` |  | Request statistics: number of request messages received
since enabling the Server. |
| `udiNumMsgReply` | `UDINT` |  | Request statistics: number of reply messages send since
enabling the Server. |
| `udiNumMsgExcReply` | `UDINT` |  | Request statistics: number of exception reply messages send
since enabling the Server. |
| `udiNumMsgExcReplyIllFct` | `UDINT` |  | Request statistics: number of exception reply messages send
since enabling the Server, signaling illegal function. |
| `udiNumMsgExcReplyIllDataAdr` | `UDINT` |  | Request statistics: number of exception reply messages send
since enabling the Server, signaling illegal data address. |
| `udiNumMsgExcReplyIllDataValue` | `UDINT` |  | Request statistics: number of exception reply messages send
since enabling the Server, signaling illegal data value. |
| `xReadRequest` | `BOOL` |  | Read request(s) happened since last call, rejected requests
included. |
| `udiNumReadRequests` | `UDINT` |  | Request statistics: read request counter, rejected requests
included. |
| `xWriteRequest` | `BOOL` |  | Write request(s) happened since last call, rejected requests
included. |
| `udiNumWriteRequests` | `UDINT` |  | Request statistics: write request counter, rejected requests
included. |

Methods:

[ResetRequestStatistics](pou-Server/ResetRequestStatistics.html)

[SupportFc](pou-Server/SupportFc.html)

[SupportsFc](pou-Server/SupportsFc.html)

[CheckDataModel](pou-Server/DataModel/CheckDataModel.html)

[InitDataModel](pou-Server/DataModel/InitDataModel.html)

[LogDataModel](pou-Server/DataModel/LogDataModel.html)

[LogStatusInfo](pou-Server/Log/LogStatusInfo.html)

Structure:

- [DataModel](pou-Server/DataModel/fld-DataModel.html)

- [CheckDataModel (Method)](pou-Server/DataModel/CheckDataModel.html)

- [InitDataModel (Method)](pou-Server/DataModel/InitDataModel.html)

- [LogDataModel (Method)](pou-Server/DataModel/LogDataModel.html)

- [Log](pou-Server/Log/fld-Log.html)

- [LogStatusInfo (Method)](pou-Server/Log/LogStatusInfo.html)

- [ResetRequestStatistics (Method)](pou-Server/ResetRequestStatistics.html)

- [SupportFc (Method)](pou-Server/SupportFc.html)

- [SupportsFc (Method)](pou-Server/SupportsFc.html)

---

## ServerSerial (FB)

# ServerSerial (FB)

FUNCTION_BLOCK ServerSerial EXTENDS [Server](Server.html#server) IMPLEMENTS ISysComUser

MODBUS serial server (slave).

For details about supported function codes and “data model” see [Server](Server.html#server).

Please note: some input variables related to connection configuration are read when rising edge on xEnable occurs.
To change connection configuration the application needs to
- disconnect (xEnable := FALSE and execute the FB)
- modify the related input variables
- connect (xEnable := TRUE and execute the FB)

The [Server](Server.html#server) provides some statistics of received valid requests messages and sent reply messages.
Invalid messages are dropped at the communication level, so doesnt appear in the statistics.
To analyse situations where invalid reply messages might occur, you can use udiLogOptions with LoggingOptions.WarnOnReceivedInvalidFrames.

The maximum number of serial ports usable with ClientSerial / ServerSerial is limited to MAX_NUM_COMPORTS.
In case there is a need to use more serial ports, anyone can set the library parameter MAX_NUM_COMPORTS within an application - see Library Manager -> ModbusFB -> Parameter -> MAX_NUM_COMPORTS.

Please visit [https://forge.codesys.com/prj/codesys-example/modbus/home](https://forge.codesys.com/prj/codesys-example/modbus/home) to find examples.

**InOut:**

| Scope | Name | Type | Initial | Comment | Inherited from |
|---|---|---|---|---|---|
| Input | `xEnable` | `BOOL` | FALSE | Enables the server, take over the configuration information fcsSupported and dataModel.
If the “data model” (tableDefinitions) contains configuration errors, the Server will not got busy (xBusy = FALSE). | [Server](Server.html#server) |
| `fcsSupported` | [SupportedFcs](../../Structs/SupportedFcs.html#supportedfcs) | Constants.SUPPORTED_FCS_SIMPLE_SERVER | Supported “function codes”, accepted at xEnable FALSE => TRUE.
In case fcsSupported is not assigned by the application it defaults to [Constants.SUPPORTED_FCS_SIMPLE_SERVER](../../GlobalConstants/Constants.html#constants-supported-fcs-simple-server). | [Server](Server.html#server) |
| `dataModel` | [TableDefinitions](../../Structs/TableDefinitions.html#tabledefinitions) |  | “data model”, accepted at xEnable FALSE => TRUE. | [Server](Server.html#server) |
| `tInactivityInfoTime` | `UDINT` | 0 | “inactivity info time” (in milliseconds).
If no valid requests are received in this time xInactive is signaling inactivity - default = 0 -> no “inactivity info”. | [Server](Server.html#server) |
| Output | `xRunning` | `BOOL` |  | Server is up and running, waiting for requests. | [Server](Server.html#server) |
| `xError` | `BOOL` |  | Error | [Server](Server.html#server) |
| `eErrorID` | [Error](../../Enums/Error.html#error) |  | Error status | [Server](Server.html#server) |
| `xInactive` | `BOOL` |  | No valid requests received for tInactivityTimeOut. | [Server](Server.html#server) |
| `udiNumMsgRecv` | `UDINT` |  | Request statistics: number of request messages received
since enabling the Server. | [Server](Server.html#server) |
| `udiNumMsgReply` | `UDINT` |  | Request statistics: number of reply messages send since
enabling the Server. | [Server](Server.html#server) |
| `udiNumMsgExcReply` | `UDINT` |  | Request statistics: number of exception reply messages send
since enabling the Server. | [Server](Server.html#server) |
| `udiNumMsgExcReplyIllFct` | `UDINT` |  | Request statistics: number of exception reply messages send
since enabling the Server, signaling illegal function. | [Server](Server.html#server) |
| `udiNumMsgExcReplyIllDataAdr` | `UDINT` |  | Request statistics: number of exception reply messages send
since enabling the Server, signaling illegal data address. | [Server](Server.html#server) |
| `udiNumMsgExcReplyIllDataValue` | `UDINT` |  | Request statistics: number of exception reply messages send
since enabling the Server, signaling illegal data value. | [Server](Server.html#server) |
| `xReadRequest` | `BOOL` |  | Read request(s) happened since last call, rejected requests
included. | [Server](Server.html#server) |
| `udiNumReadRequests` | `UDINT` |  | Request statistics: read request counter, rejected requests
included. | [Server](Server.html#server) |
| `xWriteRequest` | `BOOL` |  | Write request(s) happened since last call, rejected requests
included. | [Server](Server.html#server) |
| `udiNumWriteRequests` | `UDINT` |  | Request statistics: write request counter, rejected requests
included. | [Server](Server.html#server) |
| Input | `uiUnitId` | `UINT` | 1 | Unit-Id / Slave address. Only read when rising edge on xEnable occurs.
Slave address has to be in range 1 .. 247 according to MODBUS standard. |  |
| `iPort` | `SysCom.SYS_COM_PORTS` | SysCom.SYS_COM_PORTS.SYS_COMPORT_NONE | Serial port. Only read when rising edge on xEnable occurs. |  |
| `dwBaudrate` | `SysCom.SYS_COM_BAUDRATE` | SysCom.SYS_COM_BAUDRATE.SYS_BR_115200 | Baud rate. Only read when rising edge on xEnable occurs. |  |
| `byDataBits` | `BYTE` | 8 | Number of data bits/BYTE, 5-8. Only read when rising edge on
xEnable occurs. |  |
| `eParity` | `SysCom.SYS_COM_PARITY` | SysCom.SYS_COM_PARITY.SYS_NOPARITY | Parity. Only read when rising edge on xEnable occurs. |  |
| `eStopBits` | `SysCom.SYS_COM_STOPBITS` | SysCom.SYS_COM_STOPBITS.SYS_ONESTOPBIT | Stop bits. Only read when rising edge on xEnable occurs. |  |
| `eDTRcontrol` | `SysCom.SYS_COM_DTR_CONTROL` | SysCom.SYS_COM_DTR_CONTROL.SYS_DTR_CONTROL_DISABLE | DTR control. Only read when rising edge on xEnable occurs. |  |
| `eRTScontrol` | `SysCom.SYS_COM_RTS_CONTROL` | SysCom.SYS_COM_RTS_CONTROL.SYS_RTS_CONTROL_DISABLE | RTS control. Only read when rising edge on xEnable occurs. |  |
| `eRtuAscii` | [RtuAscii](../../Enums/RtuAscii.html#rtuascii) | RtuAscii.RTU | RTU / ASCII. Only read when rising edge on xEnable occurs. |  |
| `udiLogOptions` | `UDINT` | LoggingOptions.ServerStartStop | Logging options. |  |

Methods:

[CheckDataModel](pou-Server/DataModel/CheckDataModel.html), inherited from [Server](Server.html#server)

[InitDataModel](pou-Server/DataModel/InitDataModel.html), inherited from [Server](Server.html#server)

[LogDataModel](pou-Server/DataModel/LogDataModel.html), inherited from [Server](Server.html#server)

[LogStatusInfo](pou-ServerSerial/Log/LogStatusInfo.html)

[ResetRequestStatistics](pou-Server/ResetRequestStatistics.html), inherited from [Server](Server.html#server)

[SupportFc](pou-Server/SupportFc.html), inherited from [Server](Server.html#server)

[SupportsFc](pou-Server/SupportsFc.html), inherited from [Server](Server.html#server)

Structure:

- [Log](pou-ServerSerial/Log/fld-Log.html)

- [LogStatusInfo (Method)](pou-ServerSerial/Log/LogStatusInfo.html)

---

## ServerTCP (FB)

# ServerTCP (FB)

FUNCTION_BLOCK ServerTCP EXTENDS [Server](Server.html#server)

MODBUS TCP server (slave).

ServerTCP processes MODBUS TCP requests by up to 64 parallel client connections.

For details about supported function codes and “data model” see [Server](Server.html#server).

Please note: some input variables related to connection configuration are read when rising edge on xEnable occurs.
To change connection configuration the application needs to
- disconnect (xEnable := FALSE and execute the FB)
- modify the related input variables
- connect (xEnable := TRUE and execute the FB)

The [Server](Server.html#server) provides some statistics of received valid requests messages and sent reply messages.
Invalid messages are dropped at the communication level, so doesnt appear in the statistics.
To analyse situations where invalid reply messages might occur, you can use udiLogOptions with LoggingOptions.WarnOnReceivedInvalidFrames.

Please visit [https://forge.codesys.com/prj/codesys-example/modbus/home](https://forge.codesys.com/prj/codesys-example/modbus/home) to find examples.

**InOut:**

| Scope | Name | Type | Initial | Comment | Inherited from |
|---|---|---|---|---|---|
| Input | `xEnable` | `BOOL` | FALSE | Enables the server, take over the configuration information fcsSupported and dataModel.
If the “data model” (tableDefinitions) contains configuration errors, the Server will not got busy (xBusy = FALSE). | [Server](Server.html#server) |
| `fcsSupported` | [SupportedFcs](../../Structs/SupportedFcs.html#supportedfcs) | Constants.SUPPORTED_FCS_SIMPLE_SERVER | Supported “function codes”, accepted at xEnable FALSE => TRUE.
In case fcsSupported is not assigned by the application it defaults to [Constants.SUPPORTED_FCS_SIMPLE_SERVER](../../GlobalConstants/Constants.html#constants-supported-fcs-simple-server). | [Server](Server.html#server) |
| `dataModel` | [TableDefinitions](../../Structs/TableDefinitions.html#tabledefinitions) |  | “data model”, accepted at xEnable FALSE => TRUE. | [Server](Server.html#server) |
| `tInactivityInfoTime` | `UDINT` | 0 | “inactivity info time” (in milliseconds).
If no valid requests are received in this time xInactive is signaling inactivity - default = 0 -> no “inactivity info”. | [Server](Server.html#server) |
| Output | `xRunning` | `BOOL` |  | Server is up and running, waiting for requests. | [Server](Server.html#server) |
| `xError` | `BOOL` |  | Error | [Server](Server.html#server) |
| `eErrorID` | [Error](../../Enums/Error.html#error) |  | Error status | [Server](Server.html#server) |
| `xInactive` | `BOOL` |  | No valid requests received for tInactivityTimeOut. | [Server](Server.html#server) |
| `udiNumMsgRecv` | `UDINT` |  | Request statistics: number of request messages received
since enabling the Server. | [Server](Server.html#server) |
| `udiNumMsgReply` | `UDINT` |  | Request statistics: number of reply messages send since
enabling the Server. | [Server](Server.html#server) |
| `udiNumMsgExcReply` | `UDINT` |  | Request statistics: number of exception reply messages send
since enabling the Server. | [Server](Server.html#server) |
| `udiNumMsgExcReplyIllFct` | `UDINT` |  | Request statistics: number of exception reply messages send
since enabling the Server, signaling illegal function. | [Server](Server.html#server) |
| `udiNumMsgExcReplyIllDataAdr` | `UDINT` |  | Request statistics: number of exception reply messages send
since enabling the Server, signaling illegal data address. | [Server](Server.html#server) |
| `udiNumMsgExcReplyIllDataValue` | `UDINT` |  | Request statistics: number of exception reply messages send
since enabling the Server, signaling illegal data value. | [Server](Server.html#server) |
| `xReadRequest` | `BOOL` |  | Read request(s) happened since last call, rejected requests
included. | [Server](Server.html#server) |
| `udiNumReadRequests` | `UDINT` |  | Request statistics: read request counter, rejected requests
included. | [Server](Server.html#server) |
| `xWriteRequest` | `BOOL` |  | Write request(s) happened since last call, rejected requests
included. | [Server](Server.html#server) |
| `udiNumWriteRequests` | `UDINT` |  | Request statistics: write request counter, rejected requests
included. | [Server](Server.html#server) |
| Input | `wsInterfaceName` | `WSTRING(255)` |  | ETH interface name to bind to, “” to bind to any ETH
interface. Only read when rising edge on xEnable occurs. |  |
| `uiPort` | `UINT` | 502 | ETH port to use. Only read when rising edge on xEnable
occurs. |  |
| `xReset` | `BOOL` | FALSE | Reset the server.
Close the server socket, and open again.
Reset xRunning, xError, eErrorID and xInactive.
Reset the request statistics: udiNumMsgRecv, udiNumMsgReply … udiNumWriteRequests.
Reset xReadRequest and xWriteRequest information. |  |
| `udiLogOptions` | `UDINT` | LoggingOptions.ServerStartStop | Logging options. |  |
| Output | `uiConnectedClients` | `UINT` |  | Number of actually connected clients. |  |

Methods:

[CheckDataModel](pou-Server/DataModel/CheckDataModel.html), inherited from [Server](Server.html#server)

[InitDataModel](pou-Server/DataModel/InitDataModel.html), inherited from [Server](Server.html#server)

[LogDataModel](pou-Server/DataModel/LogDataModel.html), inherited from [Server](Server.html#server)

[LogStatusInfo](pou-ServerTCP/Log/LogStatusInfo.html)

[ResetRequestStatistics](pou-Server/ResetRequestStatistics.html), inherited from [Server](Server.html#server)

[SupportFc](pou-Server/SupportFc.html), inherited from [Server](Server.html#server)

[SupportsFc](pou-Server/SupportsFc.html), inherited from [Server](Server.html#server)

Structure:

- [Log](pou-ServerTCP/Log/fld-Log.html)

- [LogStatusInfo (Method)](pou-ServerTCP/Log/LogStatusInfo.html)

---

## Server

# Server

- [ExampleDataModel (FunctionBlock)](ExampleDataModel.html)

- [Server (FunctionBlock)](Server.html)

- [Supported function codes](Server.html#supported-function-codes)

- [“data model”](Server.html#data-model)

- [“data item” offset / “data item” numbers](Server.html#data-item-offset-data-item-numbers)

- [DataModel](pou-Server/DataModel/fld-DataModel.html)

- [CheckDataModel (Method)](pou-Server/DataModel/CheckDataModel.html)

- [InitDataModel (Method)](pou-Server/DataModel/InitDataModel.html)

- [LogDataModel (Method)](pou-Server/DataModel/LogDataModel.html)

- [Log](pou-Server/Log/fld-Log.html)

- [LogStatusInfo (Method)](pou-Server/Log/LogStatusInfo.html)

- [ResetRequestStatistics (Method)](pou-Server/ResetRequestStatistics.html)

- [SupportFc (Method)](pou-Server/SupportFc.html)

- [SupportsFc (Method)](pou-Server/SupportsFc.html)

- [ServerSerial (FunctionBlock)](ServerSerial.html)

- [Log](pou-ServerSerial/Log/fld-Log.html)

- [LogStatusInfo (Method)](pou-ServerSerial/Log/LogStatusInfo.html)

- [ServerTCP (FunctionBlock)](ServerTCP.html)

- [Log](pou-ServerTCP/Log/fld-Log.html)

- [LogStatusInfo (Method)](pou-ServerTCP/Log/LogStatusInfo.html)

---

# Utility Function Blocks

## ByteBuffer (FB)

# ByteBuffer (FB)

FUNCTION_BLOCK ByteBuffer

Buffer to work with fixed size byte arrays.

ByteBuffer does have a Capacity() fixed during Init().

It could be written to using the Put*() methods, updating Len() and the position (uiPosition).

It could be read using the Get*() methods, updating the position (uiPosition).

Position could be set from begin (0) to end (Len() -1).

Rewind() does set uiPosition to begin.

Freeze() make subsequent Put*() calls be ignored - this is reset at Init().

**InOut:**

| Scope | Name | Type | Initial |
|---|---|---|---|
| Output | `uiPosition` | `UINT` | 0 |

Methods:

[BytesToEnd](pou-ByteBuffer/BytesToEnd.html)

[Capacity](pou-ByteBuffer/Capacity.html)

[CopyContent](pou-ByteBuffer/CopyContent.html)

[Equals](pou-ByteBuffer/Equals.html)

[Freeze](pou-ByteBuffer/Freeze.html)

[GetByte](pou-ByteBuffer/GetByte.html)

[GetData](pou-ByteBuffer/GetData.html)

[GetDataPointerAt](pou-ByteBuffer/GetDataPointerAt.html)

[GetDataPointerAtPosition](pou-ByteBuffer/GetDataPointerAtPosition.html)

[GetNBytes](pou-ByteBuffer/GetNBytes.html)

[GetNBytesReverse](pou-ByteBuffer/GetNBytesReverse.html)

[GetNWords](pou-ByteBuffer/GetNWords.html)

[GetWord](pou-ByteBuffer/GetWord.html)

[Init](pou-ByteBuffer/Init.html)

[Len](pou-ByteBuffer/Len.html)

[PutByte](pou-ByteBuffer/PutByte.html)

[PutNBytes](pou-ByteBuffer/PutNBytes.html)

[PutNBytesReverse](pou-ByteBuffer/PutNBytesReverse.html)

[PutNWords](pou-ByteBuffer/PutNWords.html)

[PutWord](pou-ByteBuffer/PutWord.html)

[PutWordAt](pou-ByteBuffer/PutWordAt.html)

[Rewind](pou-ByteBuffer/Rewind.html)

[SetLen](pou-ByteBuffer/SetLen.html)

[SetPos](pou-ByteBuffer/SetPos.html)

[SetPosToEnd](pou-ByteBuffer/SetPosToEnd.html)

Structure:

- [BytesToEnd (Method)](pou-ByteBuffer/BytesToEnd.html)

- [Capacity (Method)](pou-ByteBuffer/Capacity.html)

- [CopyContent (Method)](pou-ByteBuffer/CopyContent.html)

- [Equals (Method)](pou-ByteBuffer/Equals.html)

- [Freeze (Method)](pou-ByteBuffer/Freeze.html)

- [GetByte (Method)](pou-ByteBuffer/GetByte.html)

- [GetData (Method)](pou-ByteBuffer/GetData.html)

- [GetDataPointerAt (Method)](pou-ByteBuffer/GetDataPointerAt.html)

- [GetDataPointerAtPosition (Method)](pou-ByteBuffer/GetDataPointerAtPosition.html)

- [GetNBytes (Method)](pou-ByteBuffer/GetNBytes.html)

- [GetNBytesReverse (Method)](pou-ByteBuffer/GetNBytesReverse.html)

- [GetNWords (Method)](pou-ByteBuffer/GetNWords.html)

- [GetWord (Method)](pou-ByteBuffer/GetWord.html)

- [Init (Method)](pou-ByteBuffer/Init.html)

- [Len (Method)](pou-ByteBuffer/Len.html)

- [PutByte (Method)](pou-ByteBuffer/PutByte.html)

- [PutNBytes (Method)](pou-ByteBuffer/PutNBytes.html)

- [PutNBytesReverse (Method)](pou-ByteBuffer/PutNBytesReverse.html)

- [PutNWords (Method)](pou-ByteBuffer/PutNWords.html)

- [PutWord (Method)](pou-ByteBuffer/PutWord.html)

- [PutWordAt (Method)](pou-ByteBuffer/PutWordAt.html)

- [Rewind (Method)](pou-ByteBuffer/Rewind.html)

- [SetLen (Method)](pou-ByteBuffer/SetLen.html)

- [SetPos (Method)](pou-ByteBuffer/SetPos.html)

- [SetPosToEnd (Method)](pou-ByteBuffer/SetPosToEnd.html)

---

## Util

# Util

- [ByteBuffer (FunctionBlock)](ByteBuffer.html)

- [BytesToEnd (Method)](pou-ByteBuffer/BytesToEnd.html)

- [Capacity (Method)](pou-ByteBuffer/Capacity.html)

- [CopyContent (Method)](pou-ByteBuffer/CopyContent.html)

- [Equals (Method)](pou-ByteBuffer/Equals.html)

- [Freeze (Method)](pou-ByteBuffer/Freeze.html)

- [GetByte (Method)](pou-ByteBuffer/GetByte.html)

- [GetData (Method)](pou-ByteBuffer/GetData.html)

- [GetDataPointerAt (Method)](pou-ByteBuffer/GetDataPointerAt.html)

- [GetDataPointerAtPosition (Method)](pou-ByteBuffer/GetDataPointerAtPosition.html)

- [GetNBytes (Method)](pou-ByteBuffer/GetNBytes.html)

- [GetNBytesReverse (Method)](pou-ByteBuffer/GetNBytesReverse.html)

- [GetNWords (Method)](pou-ByteBuffer/GetNWords.html)

- [GetWord (Method)](pou-ByteBuffer/GetWord.html)

- [Init (Method)](pou-ByteBuffer/Init.html)

- [Len (Method)](pou-ByteBuffer/Len.html)

- [PutByte (Method)](pou-ByteBuffer/PutByte.html)

- [PutNBytes (Method)](pou-ByteBuffer/PutNBytes.html)

- [PutNBytesReverse (Method)](pou-ByteBuffer/PutNBytesReverse.html)

- [PutNWords (Method)](pou-ByteBuffer/PutNWords.html)

- [PutWord (Method)](pou-ByteBuffer/PutWord.html)

- [PutWordAt (Method)](pou-ByteBuffer/PutWordAt.html)

- [Rewind (Method)](pou-ByteBuffer/Rewind.html)

- [SetLen (Method)](pou-ByteBuffer/SetLen.html)

- [SetPos (Method)](pou-ByteBuffer/SetPos.html)

- [SetPosToEnd (Method)](pou-ByteBuffer/SetPosToEnd.html)

---

# Global Constants

## Constants (GVL)

# Constants (GVL)

**Attributes:**

`qualified_only`

**InOut:**

| Scope | Name | Type | Initial |
|---|---|---|---|
| Constant | SUPPORTED_FCS_SIMPLE_SERVER | [SupportedFcs](../Structs/SupportedFcs.html#supportedfcs) | STRUCT(ReadCoils := TRUE, ReadDiscreteInputs := TRUE, ReadHoldingRegisters := TRUE, ReadInputRegisters := TRUE, WriteSingleCoil := TRUE, WriteSingleRegister := TRUE, ReadExceptionStatus := FALSE, Diagnostics := FALSE, GetCommEventCounter := FALSE, GetCommEventLog := FALSE, WriteMultipleCoils := TRUE, WriteMultipleRegisters := TRUE, ReportServerID := FALSE, ReadFileRecord := FALSE, WriteFileRecord := FALSE, MaskWriteRegister := TRUE, ReadWriteMultipleRegisters := TRUE, ReadFifoQueue := FALSE) |

---

## Parameter (PARAMS)

# Parameter (PARAMS)

**InOut:**

| Scope | Name | Type | Initial | Comment |
|---|---|---|---|---|
| Constant | MAX_NUM_COMPORTS | `UINT` | 10 | Maximum number of COM ports |

---

## GlobalConstants

# GlobalConstants

- [Constants (GVL)](Constants.html)

- [Parameter (ParamList)](Parameter.html)

---

# Structures

## RequestData (STRUCT)

# RequestData (STRUCT)

TYPE RequestData : STRUCT

Represents a MODBUS request data set.
Please note: some “function codes” doesnt involve request data so just the “function code” is used, for example ReadExceptionStatus.

**InOut:**

| Name | Type |
|---|---|
| `fc` | [FunctionCodes](../Enums/FunctionCodes.html#functioncodes) |
| `u` | [RequestUnion](RequestUnion.html#requestunion) |

---

## RequestDataDiagnostics (STRUCT)

# RequestDataDiagnostics (STRUCT)

TYPE RequestDataDiagnostics : STRUCT

Represents a read request for Diagnostics.

**InOut:**

| Name | Type | Initial |
|---|---|---|
| `subFc` | [SerialSubFunctionCodes](../Enums/SerialSubFunctionCodes.html#serialsubfunctioncodes) | SerialSubFunctionCodes.ReturnQueryData |

---

## RequestDataMaskWriteRegister (STRUCT)

# RequestDataMaskWriteRegister (STRUCT)

TYPE RequestDataMaskWriteRegister : STRUCT

Represents a read request for MaskWriteRegister.

**InOut:**

| Name | Type | Initial |
|---|---|---|
| `uiReferenceAddress` | `UINT` | 0 |
| `uiAndMask` | `UINT` | 0 |
| `uiOrMask` | `UINT` | 0 |

---

## RequestDataRead (STRUCT)

# RequestDataRead (STRUCT)

TYPE RequestDataRead : STRUCT

Represents a read request for ReadCoils, ReadDiscreteInputs, ReadHoldingRegisters and ReadInputRegisters.

**InOut:**

| Name | Type | Initial | Comment |
|---|---|---|---|
| `uiStartAddress` | `UINT` | 0 |  |
| `uiQuantity` | `UINT` | 1 | ReadCoils / ReadDiscreteInputs: 1 to 2000
ReadHoldingRegisters / ReadInputRegisters: 1 to 125 |

---

## RequestDataReadWriteMultipleRegisters (STRUCT)

# RequestDataReadWriteMultipleRegisters (STRUCT)

TYPE RequestDataReadWriteMultipleRegisters : STRUCT

Represents a write request for ReadWriteMultipleRegisters.

**InOut:**

| Name | Type | Initial |
|---|---|---|
| `uiReadStartAddress` | `UINT` | 0 |
| `uiQuantityRead` | `UINT` | 1 |
| `uiWriteStartAddress` | `UINT` | 0 |
| `uiQuantityWrite` | `UINT` | 1 |
| `usiWriteByteCount` | `USINT` | 0 |

---

## RequestDataWriteMultiple (STRUCT)

# RequestDataWriteMultiple (STRUCT)

TYPE RequestDataWriteMultiple : STRUCT

Represents a write request for WriteMultipleCoils and WriteMultipleRegisters.

**InOut:**

| Name | Type | Initial |
|---|---|---|
| `uiStartAddress` | `UINT` | 0 |
| `uiQuantity` | `UINT` | 1 |
| `usiByteCount` | `USINT` | 0 |

---

## RequestDataWriteSingle (STRUCT)

# RequestDataWriteSingle (STRUCT)

TYPE RequestDataWriteSingle : STRUCT

Represents a write request for WriteSingleCoil and WriteSingleRegister.

**InOut:**

| Name | Type | Initial |
|---|---|---|
| `uiAddress` | `UINT` | 0 |

---

## RequestUnion (UNION)

# RequestUnion (UNION)

TYPE RequestUnion : UNION

**InOut:**

| Name | Type |
|---|---|
| `read` | [RequestDataRead](RequestDataRead.html#requestdataread) |
| `writeSingle` | [RequestDataWriteSingle](RequestDataWriteSingle.html#requestdatawritesingle) |
| `diagnostics` | [RequestDataDiagnostics](RequestDataDiagnostics.html#requestdatadiagnostics) |
| `writeMultiple` | [RequestDataWriteMultiple](RequestDataWriteMultiple.html#requestdatawritemultiple) |
| `maskWriteRegister` | [RequestDataMaskWriteRegister](RequestDataMaskWriteRegister.html#requestdatamaskwriteregister) |
| `readWriteMultipleRegisters` | [RequestDataReadWriteMultipleRegisters](RequestDataReadWriteMultipleRegisters.html#requestdatareadwritemultipleregisters) |

---

## SupportedFcs (STRUCT)

# SupportedFcs (STRUCT)

TYPE SupportedFcs : STRUCT

Supported function codes

**InOut:**

| Name | Type | Initial | Comment |
|---|---|---|---|
| `ReadCoils` | `BIT` | FALSE | supported functions codes |
| `ReadDiscreteInputs` | `BIT` | FALSE |  |
| `ReadHoldingRegisters` | `BIT` | FALSE |  |
| `ReadInputRegisters` | `BIT` | FALSE |  |
| `WriteSingleCoil` | `BIT` | FALSE |  |
| `WriteSingleRegister` | `BIT` | FALSE |  |
| `ReadExceptionStatus` | `BIT` | FALSE |  |
| `Diagnostics` | `BIT` | FALSE |  |
| `GetCommEventCounter` | `BIT` | FALSE |  |
| `GetCommEventLog` | `BIT` | FALSE |  |
| `WriteMultipleCoils` | `BIT` | FALSE |  |
| `WriteMultipleRegisters` | `BIT` | FALSE |  |
| `ReportServerID` | `BIT` | FALSE |  |
| `ReadFileRecord` | `BIT` | FALSE |  |
| `WriteFileRecord` | `BIT` | FALSE |  |
| `MaskWriteRegister` | `BIT` | FALSE |  |
| `ReadWriteMultipleRegisters` | `BIT` | FALSE |  |
| `ReadFifoQueue` | `BIT` | FALSE |  |
| `EncapsulatedInterfaceTransport` | `BIT` | FALSE |  |
| `DiagnosticsReturnQueryData` | `BIT` | FALSE | supported sub functions codes for FC08 |
| `DiagnosticsRestartCommunicationsOption` | `BIT` | FALSE |  |
| `DiagnosticsReturnDiagnosticRegister` | `BIT` | FALSE |  |
| `DiagnosticsChangeASCIIInputDelimiter` | `BIT` | FALSE |  |
| `DiagnosticsForceListenOnlyMode` | `BIT` | FALSE |  |
| `DiagnosticsClearCountersAndDiagnosticRegister` | `BIT` | FALSE |  |
| `DiagnosticsReturnBusMessageCount` | `BIT` | FALSE |  |
| `DiagnosticsReturnBusCommunicationErrorCount` | `BIT` | FALSE |  |
| `DiagnosticsReturnBusExceptionErrorCount` | `BIT` | FALSE |  |
| `DiagnosticsReturnServerMessageCount` | `BIT` | FALSE |  |
| `DiagnosticsReturnServerNoResponseCount` | `BIT` | FALSE |  |
| `DiagnosticsReturnServerNAKCount` | `BIT` | FALSE |  |
| `DiagnosticsReturnServerBusyCount` | `BIT` | FALSE |  |
| `DiagnosticsReturnBusCharacterOverrunCount` | `BIT` | FALSE |  |
| `DiagnosticsClearOverrunCounterAndFlag` | `BIT` | FALSE |  |

---

## TableDefinition (STRUCT)

# TableDefinition (STRUCT)

TYPE TableDefinition : STRUCT

TableDefinition is used to define one of the “primary tables” as part of the “data model”.

**InOut:**

| Name | Type | Initial | Comment |
|---|---|---|---|
| `uiNumSections` | `UINT` | 0 | Number of sections in table |
| `pSections` | POINTER TO [TableSection](TableSection.html#tablesection) | 0 | sections |

---

## TableDefinitions (STRUCT)

# TableDefinitions (STRUCT)

TYPE TableDefinitions : STRUCT

TableDefinitions represents the “primary tables” (the “data model”).

**InOut:**

| Name | Type |
|---|---|
| `tableDiscreteInputs` | [TableDefinition](TableDefinition.html#tabledefinition) |
| `tableCoils` | [TableDefinition](TableDefinition.html#tabledefinition) |
| `tableInputRegisters` | [TableDefinition](TableDefinition.html#tabledefinition) |
| `tableHoldingRegisters` | [TableDefinition](TableDefinition.html#tabledefinition) |

---

## TableSection (STRUCT)

# TableSection (STRUCT)

TYPE TableSection : STRUCT

TableSection is used to define a section of one of the “primary tables” as part of the “data model”.

**InOut:**

| Name | Type | Initial | Comment |
|---|---|---|---|
| `uiStart` | `UINT` | 0 | The “data item” start index |
| `uiNumDataItems` | `UINT` | 0 | Number of “data items” in section |
| `pStartAddr` | POINTER TO BYTE | 0 | Section start address |
| `uiDataItemSize` | `UINT` | 0 | “data item” size in bit, 1 or 8 for DiscreteInputs and Coils, 16 for InputRegisters and HoldingRegisters.
DiscreteInputs and Coils can be put in memory as ARRAY[] OF BOOL (uiDataItemSize = 8)
or adressed bit-wise (uiDataItemSize = 1). |

---

## Structs

# Structs

- [RequestData (Struct)](RequestData.html)

- [RequestDataDiagnostics (Struct)](RequestDataDiagnostics.html)

- [RequestDataMaskWriteRegister (Struct)](RequestDataMaskWriteRegister.html)

- [RequestDataRead (Struct)](RequestDataRead.html)

- [RequestDataReadWriteMultipleRegisters (Struct)](RequestDataReadWriteMultipleRegisters.html)

- [RequestDataWriteMultiple (Struct)](RequestDataWriteMultiple.html)

- [RequestDataWriteSingle (Struct)](RequestDataWriteSingle.html)

- [RequestUnion (Union)](RequestUnion.html)

- [SupportedFcs (Struct)](SupportedFcs.html)

- [TableDefinition (Struct)](TableDefinition.html)

- [TableDefinitions (Struct)](TableDefinitions.html)

- [TableSection (Struct)](TableSection.html)

---


# CAN Low Level (CL2) API Reference

## CAA Can Low Level Extern Library Documentation

**Version:** 3.5.16.0  
**Source:** CODESYS GmbH / Schneider Electric Machine Expert V2.1  
**Library:** CAA_CanL2_Extern  

---

## Overview

This library contains functions for accessing the CAN field bus. Layer 7 applications (such as CANopen, J1939, DeviceNet and many others) can be realized based on this library.

> **Note:** The library can be used to access the CANbus in parallel to other CAN applications (e.g. CANopenStack), even if they use the same port. All functions are thread-safe and can be used from several tasks in parallel.

> **Note:** A CAN bus application example can be downloaded from the [CODESYS Store](http://store.codesys.com/can-bus-example.html). It contains a library providing an easy-to-use CAN API based on CANL2 which can be used directly in your application. The library source code is provided as well in case you are searching for a CL2 example project.

---


## Table of Contents


- [Enums](#enums)

  - [BUSSTATE (ENUM)](#busstate-enum)

  - [ERROR (ENUM)](#error-enum)



- [Basic Functions](#basic-functions)

  - [CloneMessage (FUN)](#clonemessage-fun)

  - [CreateIdAreaReceiver (FUN)](#createidareareceiver-fun)

  - [CreateMaskReceiver (FUN)](#createmaskreceiver-fun)

  - [CreateMessage (FUN)](#createmessage-fun)

  - [CreateSingleIdReceiver (FUN)](#createsingleidreceiver-fun)

  - [DeleteReceiver (FUN)](#deletereceiver-fun)

  - [DriverClose (FUN)](#driverclose-fun)

  - [DriverGetSize (FUN)](#drivergetsize-fun)

  - [DriverOpenH (FUN)](#driveropenh-fun)

  - [DriverOpenP (FUN)](#driveropenp-fun)

  - [FreeMessage (FUN)](#freemessage-fun)

  - [Read (FUN)](#read-fun)

  - [RegisterIdArea (FUN)](#registeridarea-fun)

  - [UnregisterIdArea (FUN)](#unregisteridarea-fun)

  - [Write (FUN)](#write-fun)



- [Diagnostic Information](#diagnostic-information)

  - [GetBaudrate (FUN)](#getbaudrate-fun)

  - [GetBusAlarm (FUN)](#getbusalarm-fun)

  - [GetBusload (FUN)](#getbusload-fun)

  - [GetBusState (FUN)](#getbusstate-fun)

  - [GetDiagnosis (FUN)](#getdiagnosis-fun)

  - [GetLostCounter (FUN)](#getlostcounter-fun)

  - [GetReceiveCounter (FUN)](#getreceivecounter-fun)

  - [GetReceiveErrorCounter (FUN)](#getreceiveerrorcounter-fun)

  - [GetReceivePoolSize (FUN)](#getreceivepoolsize-fun)

  - [GetReceiveQueueLength (FUN)](#getreceivequeuelength-fun)

  - [GetTransmitCounter (FUN)](#gettransmitcounter-fun)

  - [GetTransmitErrorCounter (FUN)](#gettransmiterrorcounter-fun)

  - [GetTransmitPoolSize (FUN)](#gettransmitpoolsize-fun)

  - [GetTransmitQueueLength (FUN)](#gettransmitqueuelength-fun)

  - [IsSendingActive (FUN)](#issendingactive-fun)

  - [ResetBusAlarm (FUN)](#resetbusalarm-fun)



- [Extended Functionality](#extended-functionality)

  - [DisableSyncService (FUN)](#disablesyncservice-fun)

  - [EnableSyncService (FUN)](#enablesyncservice-fun)



- [Indicator Services](#indicator-services)

  - [GetCiAState (FUN)](#getciastate-fun)

  - [SetCiAState (FUN)](#setciastate-fun)



- [Message Information](#message-information)

  - [GetMessageDataPointer (FUN)](#getmessagedatapointer-fun)

  - [GetMessageId (FUN)](#getmessageid-fun)

  - [GetMessageLength (FUN)](#getmessagelength-fun)

  - [GetMsgCount (FUN)](#getmsgcount-fun)

  - [GetNetId (FUN)](#getnetid-fun)

  - [GetTimeStamp (FUN)](#gettimestamp-fun)

  - [Is29BitIdMessage (FUN)](#is29bitidmessage-fun)

  - [IsRTRMessage (FUN)](#isrtrmessage-fun)

  - [IsTransmitMessage (FUN)](#istransmitmessage-fun)

  - [LostMessages (FUN)](#lostmessages-fun)



- [Structures](#structures)

  - [DIAGNOSIS_INFO (STRUCT)](#diagnosis_info-struct)



- [Global Variables](#global-variables)

  - [IndicatorConstants (GVL)](#indicatorconstants-gvl)



- [Internal - Basic Functions](#internal---basic-functions)

  - [_CloneMessage (FUN)](#_clonemessage-fun)

  - [_CreateArrayReceiver (FUN)](#_createarrayreceiver-fun)

  - [_CreateIdAreaReceiver (FUN)](#_createidareareceiver-fun)

  - [_CreateMaskReceiver (FUN)](#_createmaskreceiver-fun)

  - [_CreateMessage (FUN)](#_createmessage-fun)

  - [_CreateSingleIdReceiver (FUN)](#_createsingleidreceiver-fun)

  - [_DeleteReceiver (FUN)](#_deletereceiver-fun)

  - [_DriverClose (FUN)](#_driverclose-fun)

  - [_DriverGetSize (FUN)](#_drivergetsize-fun)

  - [_DriverOpenH (FUN)](#_driveropenh-fun)

  - [_DriverOpenP (FUN)](#_driveropenp-fun)

  - [_FreeMessage (FUN)](#_freemessage-fun)

  - [_Read (FUN)](#_read-fun)

  - [_ReadArrayReceiver (FUN)](#_readarrayreceiver-fun)

  - [_RegisterIdArea (FUN)](#_registeridarea-fun)

  - [_UnregisterIdArea (FUN)](#_unregisteridarea-fun)

  - [_Write (FUN)](#_write-fun)



- [Internal - Diagnostic Information](#internal---diagnostic-information)

  - [_GetBaudrate (FUN)](#_getbaudrate-fun)

  - [_GetBusAlarm (FUN)](#_getbusalarm-fun)

  - [_GetBusload (FUN)](#_getbusload-fun)

  - [_GetBusState (FUN)](#_getbusstate-fun)

  - [_GetDiagnosis (FUN)](#_getdiagnosis-fun)

  - [_GetLostCounter (FUN)](#_getlostcounter-fun)

  - [_GetReceiveCounter (FUN)](#_getreceivecounter-fun)

  - [_GetReceiveErrorCounter (FUN)](#_getreceiveerrorcounter-fun)

  - [_GetReceivePoolSize (FUN)](#_getreceivepoolsize-fun)

  - [_GetReceiveQueueLength (FUN)](#_getreceivequeuelength-fun)

  - [_GetTransmitCounter (FUN)](#_gettransmitcounter-fun)

  - [_GetTransmitErrorCounter (FUN)](#_gettransmiterrorcounter-fun)

  - [_GetTransmitPoolSize (FUN)](#_gettransmitpoolsize-fun)

  - [_GetTransmitQueueLength (FUN)](#_gettransmitqueuelength-fun)

  - [_IsSendingActive (FUN)](#_issendingactive-fun)

  - [_ResetBusAlarm (FUN)](#_resetbusalarm-fun)



- [Internal - Extended Functionality](#internal---extended-functionality)

  - [_DisableSyncService (FUN)](#_disablesyncservice-fun)

  - [_EnableSyncService (FUN)](#_enablesyncservice-fun)



- [Internal - Indicator Services](#internal---indicator-services)

  - [_GetCiAState (FUN)](#_getciastate-fun)

  - [_SetCiAState (FUN)](#_setciastate-fun)



- [Internal - Message Information](#internal---message-information)

  - [_GetMessageDataPointer (FUN)](#_getmessagedatapointer-fun)

  - [_GetMessageId (FUN)](#_getmessageid-fun)

  - [_GetMessageLength (FUN)](#_getmessagelength-fun)

  - [_GetMsgCount (FUN)](#_getmsgcount-fun)

  - [_GetNetId (FUN)](#_getnetid-fun)

  - [_GetTimeStamp (FUN)](#_gettimestamp-fun)

  - [_Is29BitIdMessage (FUN)](#_is29bitidmessage-fun)

  - [_IsRTRMessage (FUN)](#_isrtrmessage-fun)

  - [_IsTransmitMessage (FUN)](#_istransmitmessage-fun)

  - [_LostMessages (FUN)](#_lostmessages-fun)



---


# Enums


## BUSSTATE (ENUM)


TYPE BUSSTATE :
This data type describes the current state of the CAN network.
Attributes:
qualified_only
InOut:
Name
Comment
UNKNOWN
The state of the network is not known or busstate is not implemented by driver.
ERR_FREE
No occurrence of CAN bus errors so far. The error counters of the chip are zero.
ACTIVE
Only few CAN bus errors so far. The error counters of the chip are below the warning level.
WARNING
Occurence of some CAN bus errors. The error counters are above the warning level.
PASSIVE
Too many CAN bus errors. The error counters are above the error level.
BUSOFF
The node has been separated from the CAN bus. The error counter has exceeded the admissible maximum.


---


## ERROR (ENUM)


TYPE ERROR :
This data type describes all errors that can occur while running CL2 functions:
Attributes:
qualified_only
InOut:
Name
Initial
Comment
NO_ERROR
0
no occurence of errors
NO_29BIT_ID
10202
29Bit identifiers are not supported
WRONG_BAUDRATE
10203
baudrate is not supported
NO_MEMORY
10204
memory space cannot be allocated
INVALID_NETID
10205
invalid Network ID
INVALID_PRIORITY
10206
invalid priority
INVALID_DRIVER_HANDLE
10207
invalid driver handle
INVALID_MESSAGE_HANDLE
10208
invalid message handle
INVALID_ID_HANDLE
10209
invalid identifier handle
NO_DRIVER
10210
no CAN driver available
SENDING_ERROR
10211
message could not be sent
NO_SYNC_SERVICE
10212
SYNC-service is not supported
NO_SYNC_PRODUCER
10213
SYNC-producer is not supported
NO_SYNC_CONSUMER
10214
SYNC-consumer is not supported
NO_SYNC_EVENT
10215
SYNC-event is not supported
NO_SYNC_WINDOW
10216
window length is not supported
NO_SYNC_FOREWARNTIME
10217
forewarn time is not supported
WRONG_PARAM
10224
wrong parameter
INVALID_HANDLE
10249
the handle was invalid


---


# Basic Functions


## CloneMessage (FUN)


FUNCTION CloneMessage : CAA.HANDLE
This function duplicates an existing message. This duplicated message may be modified and sent via Write for example.
## Example

VAR
hReceiver : CAA.HANDLE;
hMsg : CAA.HANDLE;
hMsgCloned : CAA.HANDLE;
ctMsgLeft : CAA.COUNT;
eError : CL2.ERROR;
END_VAR
//receive a message from hReceiver
hMsg := CL2.Read(hReceiverId := hReceiver, pctMsgLeft := ADR(ctMsgLeft), peError := ADR(eError));
IF hMsg <> CAA.gc_hINVALID THEN
//Clone received message
hMsgCloned := CL2.CloneMessage(hMessage := hMsg, peError := ADR(eError));
//free original message
CL2.FreeMessage(hMessage := hMsg);
hMsg := CAA.gc_hINVALID;
//work with hMsgCloned...
END_IF
InOut:
Scope
Name
Type
Comment
Return
CloneMessage
CAA.HANDLE
cloned message handle
Input
hMessage
CAA.HANDLE
handle of message to clone
peError
POINTER TO ERROR
optional pointer to error enum


---


## CreateIdAreaReceiver (FUN)


FUNCTION CreateIdAreaReceiver : CAA.HANDLE
This function creates a receiver to which several identifier areas may be added using the function RegisterIdArea . This receiver type is used if messages within a specific cobID area should be received. For receiving a message use the returned receiver handle for Read function call. There are two kind of receivers:
Always Newest Receivers (xAlwaysNewest := TRUE):  Receiver holds only the last received message.
Receiver with Queue (xAlwaysNewest := FALSE):  Receiver holds messages in chronological order.
> **Note:**

To avoid losing receive messages an application has to read all messages of a receiver each cycle. All messages should be processed and released by FreeMessage afterwards.
> **Note:**

Current implementation of this receiver type does not support 29 bit identifiers.
## Example

VAR
hDriver : CAA.HANDLE;
hReceiver : CAA.HANDLE;
hMsg : CAA.HANDLE;
ctMsgLeft : CAA.COUNT;
eError : CL2.ERROR;
END_VAR
//Create an IdAreaReceiver
hReceiver := CL2.CreateIdAreaReceiver(hDriver := hDriver, //driver handle
xAlwaysNewest := FALSE, //FALSE ==> receiver with queue; TRUE ==> only newest message
eEvent := CB.EVENT.NO_EVENT, //no receive event
xEnableSyncWindow := FALSE, //not implemented
peError := ADR(eError) //optional pointer to error
);
IF hReceiver <> CAA.gc_hINVALID THEN
//Add an area for CANopen Emergency messages (cobId 16#81-16#9F)
CL2.RegisterIdArea(hReceiverId := hReceiver, //receiver
cobIdStart := 16#81, //start cobID
cobIdEnd := 16#9F, //end cobID
xRTRValue := FALSE, //no RTR messages
xRTRMask := TRUE, //activate RTR filter ==> xRTRValue will be checked
x29BitIdValue := FALSE, //no 29 bit CAN messages
x29BitIdMask := TRUE, //activate 29 bit filter ==> x29BitIdValue will be checked
xTransmitValue := FALSE, //only receive messages, no transmit message loopback
xTransmitMask := TRUE //activate transmit mask filter ==> xTransmitValue will be checked
);
END_IF
REPEAT
//receive a message from hReceiver
hMsg := CL2.Read(hReceiverId := hReceiver, pctMsgLeft := ADR(ctMsgLeft), peError := ADR(eError));
IF hMsg <> CAA.gc_hINVALID THEN
//TODO: Process message (CL2.GetMessageDataPointer, CL2.GetMessageId, ...)
CL2.FreeMessage(hMsg); //release message
hMsg := CAA.gc_hINVALID; //to avoid using an already released message
END_IF
UNTIL ctMsgLeft = 0
END_REPEAT
Optionally, an event can be registered which is triggered upon reception of a corresponding message. A callback function can be registerd via  CB.RegisterCallback  (CAA Callback library). Use event class  CB.EVENT_CLASS.FIELDBUS , event source  CB.EVENT_SOURCE.CB_DRIVER  and any unassigned event number (see  CB.EVENT ). Use the same event number for  eEvent  input. Input variable  dwParam  of the registered callback function contains the CAN ID of the received message. See CreateSingleIdReceiver for example code.
> **Note:**

Event mechanism is not supported on all systems. Futhermore it is not possible to register an event for extended identifiers (29bit).
InOut:
Scope
Name
Type
Comment
Return
CreateIdAreaReceiver
CAA.HANDLE
new receiver handle or  CAA.gc_hINVALID  in case of failure
Input
hDriver
CAA.HANDLE
handle of CAN interface
xAlwaysNewest
BOOL
TRUE: returns only the newest message; FALSE: receiver with queue.
eEvent
CB.EVENT
trigger event when message received
xEnableSyncWindow
BOOL
use SYNC window: not implemented ==> do not care
peError
POINTER TO ERROR
optional pointer to error enum


---


## CreateMaskReceiver (FUN)


FUNCTION CreateMaskReceiver : CAA.HANDLE
This function creates a receiver for a specific identifier area. For receiving a message use the returned receiver handle for Read function call. Mask receivers are very similar to Area Receivers (see also RegisterIdArea ). The only difference is that CAN ID filtering is not done by range but by bit mask. Inputs  cobIdValue  and  cobIdMask  are interpreted as follows:
Value
0
1
0
1
x : this bit may be either  TRUE  or  FALSE
0 : this bit has to be  FALSE
1 : this bit hat to be  TRUE
Mask
0
0
1
1
Result
X
X
0
1
In general: The values of the masks activate the evaluation of the value parameters. If the mask value is  FALSE  the value parameter is ignored.
There are two kind of receivers:
Always Newest Receivers (xAlwaysNewest := TRUE):  Receiver holds only the last received message.
Receiver with Queue (xAlwaysNewest := FALSE):  Receiver holds messages in chronological order.
Receivers can be also used for Tx loopback. If  xTransmitMask  is set to  FALSE  or  xTransmitMask  and  xTransmitValue  are set to  TRUE  CAN messages which are sent via Write will be received (applies to all transmit messages on the CAN interface). Use function IsTransmitMessage to distinguish between receive and transmit messages.
> **Note:**

To avoid losing receive messages an application has to read all messages of a receiver each cycle. All messages should be processed and released by FreeMessage afterwards.
## Example

VAR
hDriver : CAA.HANDLE;
hReceiver : CAA.HANDLE;
hMsg : CAA.HANDLE;
ctMsgLeft : CAA.COUNT;
eError : CL2.ERROR;
END_VAR
//Create a MaskReceiver which receives all messages with CAN ID 16#80.
hReceiver := CL2.CreateMaskReceiver(hDriver := hDriver,
cobIdValue := 16#80, //cobID value
cobIdMask := 16#FFFFFFFF, //cobID mask ==> all bits of value are relevant
xRTRValue := FALSE, //no RTR messages
xRTRMask := TRUE, //activate RTR filter ==> xRTRValue will be checked
x29BitIdValue := FALSE, //no 29 bit CAN messages
x29BitIdMask := TRUE, //activate 29 bit filter ==> x29BitIdValue will be checked
xTransmitValue := FALSE, //only receive messages, no transmit message loopback
xTransmitMask := TRUE, //activate transmit mask filter ==> xTransmitValue will be checked
xAlwaysNewest := FALSE, //FALSE := receiver with queue; TRUE: only newest message
eEvent := CB.EVENT.NO_EVENT, //no receive event
xEnableSyncWindow := FALSE, //not implemented
peError := ADR(eError) //optional pointer to error
);
REPEAT
//receive a message from hReceiver
hMsg := CL2.Read(hReceiverId := hReceiver, pctMsgLeft := ADR(ctMsgLeft), peError := ADR(eError));
IF hMsg <> CAA.gc_hINVALID THEN
//TODO: Process message (CL2.GetMessageDataPointer, CL2.GetMessageId, ...)
CL2.FreeMessage(hMsg); //release message
hMsg := CAA.gc_hINVALID; //to avoid using an already released message
END_IF
UNTIL ctMsgLeft = 0
END_REPEAT
Optionally, an event can be registered which is triggered upon reception of a corresponding message. A callback function can be registerd via  CB.RegisterCallback  (CAA Callback library). Use event class  CB.EVENT_CLASS.FIELDBUS , event source  CB.EVENT_SOURCE.CB_DRIVER  and any unassigned event number (see  CB.EVENT ). Use the same event number for  eEvent  input. Input variable  dwParam  of the registered callback function contains the CAN ID of the received message. See CreateSingleIdReceiver for example code.
> **Note:**

Event mechanism is not supported on all systems. Futhermore it is not possible to register an event for extended identifiers (29bit).
InOut:
Scope
Name
Type
Comment
Return
CreateMaskReceiver
CAA.HANDLE
new receiver handle or  CAA.gc_hINVALID  in case of failure
Input
hDriver
CAA.HANDLE
handle of CAN interface
cobIdValue
CL2I.COBID
CobID value
cobIdMask
CL2I.COBID
CobID mask
xRTRValue
BOOL
Value RTR bit; only evaluated if  xRTRMask  is set to  TRUE
xRTRMask
BOOL
Mask RTR bit
x29BitIdValue
BOOL
Value 29 Bit Id; only evaluated if  x29BitIdMask  is set to  TRUE
x29BitIdMask
BOOL
Mask 29 Bit Id
xTransmitValue
BOOL
Value Transmit message; only evaluated if  xTransmitMask  is set to  TRUE
xTransmitMask
BOOL
Mask Transmit message
xAlwaysNewest
BOOL
TRUE : returns only the newest message;  FALSE : receiver with queue.
eEvent
CB.EVENT
trigger event when message received
xEnableSyncWindow
BOOL
use SYNC window: not implemented ==> do not care
peError
POINTER TO ERROR
optional pointer to error enum


---


## CreateMessage (FUN)


FUNCTION CreateMessage : CAA.HANDLE
This function allocates a new message from the data pool of the driver and makes it available via its handle  hMessage . In addition, the function sets the identifier, cobld, data length and RTR flag of the message. Such a message must either be sent with Write or released with FreeMessage . It can also be duplicated by use of CloneMessage .
## Example

See Write .
InOut:
Scope
Name
Type
Comment
Return
CreateMessage
CAA.HANDLE
new message handle or  CAA.gc_hINVALID  if no resources left
Input
hDriver
CAA.HANDLE
handle of CAN interface
cobID
CL2I.COBID
cob ID
usiLength
USINT
length of valid data bytes
xRTR
BOOL
RTR bit
x29BitID
BOOL
29 Bit ID
peError
POINTER TO ERROR
optional pointer to error enum


---


## CreateSingleIdReceiver (FUN)


FUNCTION CreateSingleIdReceiver : CAA.HANDLE
This function creates a receiver for one specific CAN identifier. For receiving a message use the returned receiver handle for Read function call. There are two kind of receivers:
Always Newest Receivers (xAlwaysNewest := TRUE):  Receiver holds only the last received message.
Receiver with Queue (xAlwaysNewest := FALSE):  Receiver holds messages in chronological order.
Receivers can be also used for Tx loopback. If  xTransmit  is set to  TRUE  CAN messages which are sent via Write will be received (applies to all transmit messages on the CAN interface). Use function IsTransmitMessage to distinguish between receive and transmit messages.
> **Note:**

To avoid losing receive messages an application has to read all messages of a receiver each cycle. All messages should be processed and released by FreeMessage afterwards.
## Example

In this example a single ID receiver is created. It receives all RTR messages on CAN ID 16#100.
VAR
hDriver : CAA.HANDLE;
hReceiver : CAA.HANDLE;
hMsg : CAA.HANDLE;
pData : POINTER TO CL2I.DATA;
eError : CL2.ERROR;
ctMsgLeft : CAA.COUNT;
END_VAR
hReceiver := CL2.CreateSingleIdReceiver(hDriver := hDriver,
cobId := 16#100,
xRTR := TRUE,
x29BitId := FALSE,
xTransmit := FALSE,
xAlwaysNewest := FALSE,
eEvent := CB.EVENT.NO_EVENT, //no receive event
xEnableSyncWindow := FALSE, //not implemented
peError := ADR(eError) //optional pointer to error
);
REPEAT
//receive a message from hReceiver
hMsg := CL2.Read(hReceiverId := hReceiver, pctMsgLeft := ADR(ctMsgLeft), peError := ADR(eError));
IF hMsg <> CAA.gc_hINVALID THEN
//TODO: Process message (CL2.GetMessageDataPointer, CL2.GetMessageId, ...)
CL2.FreeMessage(hMsg); //release message
hMsg := CAA.gc_hINVALID; //to avoid using an already released message
END_IF
UNTIL ctMsgLeft = 0
END_REPEAT
Optionally, an event can be registered which is triggered upon reception of a corresponding message. A callback function can be registerd via  CB.RegisterCallback  (CAA Callback library). Use event class  CB.EVENT_CLASS.FIELDBUS , event source  CB.EVENT_SOURCE.CB_DRIVER  and any unassigned event number (see  CB.EVENT ). Use the same event number for  eEvent  input. Input variable  dwParam  of the registered callback function contains the CAN ID of the received message.
> **Note:**

Event mechanism is not supported on all systems. Futhermore it is not possible to register an event for extended identifiers (29bit).
## Example

In this example a single ID receiver with event callback is created.
Step 1:  Define a callback function with following interface (function name can be changed!).
FUNCTION CallbackReceiveCANMessage : DWORD
VAR_INPUT
dwSpec  : DWORD;  (* CB.Event and CB.EventClass *)
dwSource : DWORD; (* CB.EventSource *)
dwParam : DWORD;  (* CAN ID *)
END_VAR
Step 2:  Activate  Enable system call  in build settings of  CallbackReceiveCANMessage .
Step 3:  Register callback and create receiver.
VAR
hDriver : CAA.HANDLE;
hReceiver : CAA.HANDLE;
eError : CL2.ERROR;
callback : CB.CB_CALLBACK;
hEvent : CAA.HANDLE;
eCBError : CB.ERROR;
END_VAR
callBack.eClass := CB.EVENT_CLASS.FIELDBUS;
callback.eSource := CB.EVENT_SOURCE.DRIVER;
callback.eEvent := 10000; //any unassigned event number
callback.pPOUFunc := ADR(CallbackReceiveCANMessage);
hEvent := CB.RegisterCallback(callback, ADR(eCBError));
hReceiver := CL2.CreateSingleIdReceiver(hDriver := hDriver,
cobId := 16#100,
xRTR := FALSE,
x29BitId := FALSE,
xTransmit := FALSE,
xAlwaysNewest := FALSE,
eEvent := 10000, //use the previously registered event number
xEnableSyncWindow := FALSE, //not implemented
peError := ADR(eError) //optional pointer to error
);
InOut:
Scope
Name
Type
Comment
Return
CreateSingleIdReceiver
CAA.HANDLE
new receiver handle or  CAA.gc_hINVALID  in case of failure
Input
hDriver
CAA.HANDLE
handle of CAN interface
cobId
CL2I.COBID
id of message to be received
xRTR
BOOL
TRUE : receive RTR messages,  FALSE : receive no RTR messages
x29BitId
BOOL
TRUE : receive 29 Bit Ids,  FALSE : receive 11 Bid Ids
xTransmit
BOOL
TRUE : receive Tx messages,  FALSE : receive Rx messages
xAlwaysNewest
BOOL
TRUE : returns only the newest message;  FALSE : receiver with queue.
eEvent
CB.EVENT
trigger event when message received
xEnableSyncWindow
BOOL
use SYNC window: not implemented ==> do not care
peError
POINTER TO ERROR
optional pointer to error enum


---


## DeleteReceiver (FUN)


FUNCTION DeleteReceiver : ERROR
This function releases all ressources of a specific receiver.
> **Note:**

When calling DriverClose all receivers connected to this driver are released automatically. Do not call  DeleteReceiver  afterwards!
InOut:
Scope
Name
Type
Comment
Return
DeleteReceiver
ERROR
ERROR.NO_ERROR or appropriate error code
Input
hReceiverId
CAA.HANDLE
handle of receiver


---


## DriverClose (FUN)


FUNCTION DriverClose : ERROR
Closes a CAN interface and frees all resources.
InOut:
Scope
Name
Type
Comment
Return
DriverClose
ERROR
ERROR.NO_ERROR or appropriate error code
Input
hDriver
CAA.HANDLE
handle of CAN interface


---


## DriverGetSize (FUN)


FUNCTION DriverGetSize : CAA.SIZE
Calculates the needed memory size for DriverOpenP .
InOut:
Scope
Name
Type
Comment
Return
DriverGetSize
CAA.SIZE
Required memory size for DriverOpenP
Input
usiNetId
USINT
number of CAN interface [0..n]
xSupport29Bit
BOOL
FALSE : only 11-Bit IDs,  TRUE : support also 29-Bit
ctMessages
CAA.COUNT
number of transmit messages which should be allocated
peError
POINTER TO ERROR
optional pointer to error enum


---


## DriverOpenH (FUN)


FUNCTION DriverOpenH : CAA.HANDLE
Opens a CAN interface and allocates memory from heap. Not every hardware supports each baud rate. If a baud rate is not supported or if the interface cannot be opened due to different reasons, the function returns  CAA.gc_hINVALID . The function can be called several times on the same interface, so that multiple parts of a program can work on it. You can set  uiBaudrate  to 0 if the interface is already opened or if the default baudrate from configuration file should be used. See following section in configuration file:
[CmpCAACanL2]
;If setting PersistentBaudrate is enabled (0: disabled; 1: enabled)
;the baudrate will be stored into Net.X.DefaultBaudrate (where X equals NetId) when opening the driver.
PersistentBaudrate=1
;Default baudrate for CAN network 0. This baudrate will be used when the network is opened (e.g from CmpBlkDrvCan or CANopen) with the baudrate set to 0.
;Net.0.DefaultBaudrate=1000
Net.0.DefaultBaudrate=1000
InOut:
Scope
Name
Type
Comment
Return
DriverOpenH
CAA.HANDLE
handle of CAN interface or  CAA.gc_hINVALID  if failed.
Input
usiNetId
USINT
number of CAN interface [0..n]
uiBaudrate
UINT
Baudrate in kBit/s e.g. 1000 for 1 Mbit
xSupport29Bits
BOOL
FALSE : only 11-Bit IDs,  TRUE : support also 29-Bit
ctMessages
CAA.COUNT
number of transmit messages which should be allocated
peError
POINTER TO ERROR
optional pointer to error enum


---


## DriverOpenP (FUN)


FUNCTION DriverOpenP : CAA.HANDLE
See DriverOpenH for details. In contrast to DriverOpenH no dynamic memory will be allocated. Memory specified by  pMemory  and  szMemSize  is used. Use DriverGetSize to calculate the required memory size. Please note that required memory size can change with new runtime version.
> **Note:**

pMemory should be aligned to a 4 byte address on 32bit systems and 8 byte address on 64bit. To get sure, you can declare the memory with ARRAY [0..n] of __XWORD. Please keep also in mind that required memory size is different for 32 and 64 bit systems.
InOut:
Scope
Name
Type
Comment
Return
DriverOpenP
CAA.HANDLE
handle of CAN interface or  CAA.gc_hINVALID  if failed.
Input
usiNetId
USINT
number of CAN interface [0..n]
uiBaudrate
UINT
Baudrate in kBit/s e.g. 1000 for 1 Mbit
xSupport29Bits
BOOL
FALSE : only 11-Bit IDs,  TRUE : support also 29-Bit
szMemSize
CAA.SIZE
size of allocated memory
pMemory
CAA.PVOID
pointer to aligned memory
peError
POINTER TO ERROR
optional pointer to error enum


---


## FreeMessage (FUN)


FUNCTION FreeMessage : ERROR
This function releases a message that has been created with CreateMessage , read with Read or duplicated with CloneMessage .
> **Note:**

Do not free a message after it has been passed to the CL2 layer.
Example: Creating a message, then passing the message handle to CL2 by calling Write and releasing it afterwards may result in unexpected behaviour.
InOut:
Scope
Name
Type
Comment
Return
FreeMessage
ERROR
ERROR.NO_ERROR or appropriate error code
Input
hMessage
CAA.HANDLE
handle of message to be freed


---


## Read (FUN)


FUNCTION Read : CAA.HANDLE
Receives messages from a receiver.
> **Note:**

To avoid losing receive messages an application has to read all messages of all receivers each cycle. All messages should be processed and released by FreeMessage afterwards.
> **Note:**

Normally a receiver returns  CAA.gc_hINVALID  if all messages are read by application.
But receivers with  xAlwaysNewest  =  TRUE  return always the newest message even if it was already received.
The application has to free the message each time it is returned by CL2.Read!!!
In case of an always newest receiver the data  pctMsgLeft  points to should be interpreted as follows:
0 : old message;  1 : new message;  2 : message overflow
## Example

VAR
hDriver : CAA.HANDLE;
hReceiver : CAA.HANDLE;
hMsg : CAA.HANDLE;
ctMsgLeft : CAA.COUNT;
eError : CL2.ERROR;
END_VAR
//Create a MaskReceiver which receives all messages with CAN ID 16#80.
hReceiver := CL2.CreateMaskReceiver(hDriver := hDriver,
cobIdValue := 16#80, //cobID value
cobIdMask := 16#FFFFFFFF, //cobID mask ==> all bits of value are relevant
xRTRValue := FALSE, //no RTR messages
xRTRMask := TRUE, //activate RTR filter ==> xRTRValue will be checked
x29BitIdValue := FALSE, //no 29 bit CAN messages
x29BitIdMask := TRUE, //activate 29 bit filter ==> x29BitIdValue will be checked
xTransmitValue := FALSE, //only receive messages, no transmit message loopback
xTransmitMask := TRUE, //activate transmit mask filter ==> xTransmitValue will be checked
xAlwaysNewest := FALSE, //FALSE := receiver with queue; TRUE: only newest message
eEvent := CB.EVENT.NO_EVENT, //no receive event
xEnableSyncWindow := FALSE, //not implemented
peError := ADR(eError) //optional pointer to error
);
REPEAT
//receive a message from hReceiver
hMsg := CL2.Read(hReceiverId := hReceiver, pctMsgLeft := ADR(ctMsgLeft), peError := ADR(eError));
IF hMsg <> CAA.gc_hINVALID THEN
//TODO: Process message (CL2.GetMessageDataPointer, CL2.GetMessageId, ...)
CL2.FreeMessage(hMsg); //release message
hMsg := CAA.gc_hINVALID; //to avoid using an already released message
END_IF
UNTIL ctMsgLeft = 0
END_REPEAT
InOut:
Scope
Name
Type
Comment
Return
Read
CAA.HANDLE
handle of received CAN message or  CAA.gc_hINVALID  if receiver is empty.
Input
hReceiverId
CAA.HANDLE
receiver handle
pctMsgLeft
POINTER TO CAA.COUNT
Optional pointer to  ctMsgLeft . After calling  CL2.Read ctMsgLeft  contains the number of remaining messages in receive queue.
peError
POINTER TO ERROR
optional pointer to error enum


---


## RegisterIdArea (FUN)


FUNCTION RegisterIdArea : ERROR
This function registers a CAN identifier area to an IdAreaReceiver created by CreateIdAreaReceiver . If the parameter  cobIdStart  equals  cobIdEnd  only one identifier is registered. The values of the masks activate the evaluation of the value parameters. If the mask value is  FALSE  the value parameter is ignored.
Receivers can be also used for Tx loopback. If  xTransmitMask  is set to  FALSE  or  xTransmitMask  and  xTransmitValue  are set to  TRUE  CAN messages which are sent via Write will be received (applies to all transmit messages on the CAN interface). Use function IsTransmitMessage to distinguish between receive and transmit messages.
> **Note:**

Current implementation of this receiver type does not support 29 bit identifiers. Set  x29BitIdValue  always to  FALSE  and  x29BitIdMask  to  TRUE . Otherwise an error will be returned.
## Example

See CreateIdAreaReceiver .
InOut:
Scope
Name
Type
Comment
Return
RegisterIdArea
ERROR
ERROR.NO_ERROR if area was registered successfully, else appropriate error code
Input
hReceiverId
CAA.HANDLE
Retrun value of CreateIdAreaReceiver
cobIdStart
CL2I.COBID
start id of message to be received
cobIdEnd
CL2I.COBID
end id of message to be received
xRTRValue
BOOL
Value RTR bit; only evaluated if  xRTRMask  is set to  TRUE
xRTRMask
BOOL
Mask RTR bit
x29BitIdValue
BOOL
Value 29 Bit Id; only evaluated if  x29BitIdMask  is set to  TRUE
x29BitIdMask
BOOL
Mask 29 Bit Id
xTransmitValue
BOOL
Value Transmit message; only evaluated if  xTransmitMask  is set to  TRUE
xTransmitMask
BOOL
Mask Transmit message


---


## UnregisterIdArea (FUN)


FUNCTION UnregisterIdArea : ERROR
This function removes a CAN identifier area previously added by RegisterIdArea .
InOut:
Scope
Name
Type
Comment
Return
UnregisterIdArea
ERROR
error
Input
hReceiverId
CAA.HANDLE
Retrun value of CreateIdAreaReceiver
cobIdStart
CL2I.COBID
start id of message to be received
cobIdEnd
CL2I.COBID
end id of message to be received
xRTRValue
BOOL
Value RTR bit; only evaluated if  xRTRMask  is set to  TRUE
xRTRMask
BOOL
Mask RTR bit
x29BitIdValue
BOOL
Value 29 Bit Id; only evaluated if  x29BitIdMask  is set to  TRUE
x29BitIdMask
BOOL
Mask 29 Bit Id
xTransmitValue
BOOL
Value Transmit message; only evaluated if  xTransmitMask  is set to  TRUE
xTransmitMask
BOOL
Mask Transmit message


---


## Write (FUN)


FUNCTION Write : ERROR
This function writes a CAN message (see also CreateMessage ) via a CAN interface specified by  hDriver . If  Write  returns ERROR.NO_ERROR the message was successfully handed over to the lower layers and will be automatically released after successful sending (Note: Do not call FreeMessage on such handles anymore!). If the message cannot be sent the function returns the error code ERROR.SENDING_ERROR and sending process must be repeated later. Otherwise the message handle has to be manually freed by application (see FreeMessage ).
Messages can be sent with different priorities. Messages with the same priority are sent in chronological order. Messages with higher priority (means lower  usiPriority ) are always sent prior to those with lower priority. Priority 0 has a special meaning: messages with priority 0 are sent as soon as possible prior to all other messages waiting for transport. If a priority level not valid for the driver is used the message is not sent and function returns an error code. If the applied coblD is registered for reception and transmit messages are activated for receiving (see  TransmitMask  and  TransmitValue  of Receiver), a message which was sent successfully can be received via Read with a current timestamp (if timestamps are supported by driver). The function IsTransmitMessage returns  TRUE  on such messages.
> **Note:**

Following rules are important when using  CL2.Write :
In case of  CL2.Write  returns ERROR.NO_ERROR the message was successfully handed over to the CL2 layer.
Do not use the message handle anymore! It will be automatically released.
To avoid using such handles it is helpful setting  hMessage  to  CAA.gc_hINVALID  directly after calling  CL2.Write
In case of  CL2.Write  returns any Error, the message still belongs to the application.
Do not forget to release the message!
## Example

In this example a CANopen NMT reset message will be sent.
VAR
hDriver : CAA.HANDLE;
hReceiver : CAA.HANDLE;
hMsg : CAA.HANDLE;
pData : POINTER TO CL2I.DATA;
eError : CL2.ERROR;
END_VAR
//Create message
hMsg := CL2.CreateMessage(hDriver := hDriver,
cobID := 16#0,
usiLength := 2,
xRTR := FALSE,
x29BitID := FALSE,
peError := ADR(eError)
);
IF hMsg <> CAA.gc_hINVALID THEN
//Get message data pointer
pData := CL2.GetMessageDataPointer(hMessage := hMsg, peError := ADR(eError));
IF pData <> CAA.gc_pNULL THEN
//initialize message data
pData^[0] := 16#81;
pData^[1] := 16#0;
END_IF
//send message
eError := CL2.Write(hDriver := hDriver,
hMessage := hMsg,
usiPriority := 1, //highest priority
xEnableSyncWindow := FALSE
);
IF eError <> CL2.ERROR.NO_ERROR THEN
//sending was not successful ==> release the message
CL2.Free_Message(hMsg);
END_IF
END_IF
InOut:
Scope
Name
Type
Comment
Return
Write
ERROR
error
Input
hDriver
CAA.HANDLE
handle of CAN interface
hMessage
CAA.HANDLE
handle of message to be written
usiPriority
USINT
priority of message:
0:  send immediately;
1-n:  priority (1: high, n: low), default is n = 8
xEnableSyncWindow
BOOL
use SYNC window => not implemented; do not care


---


# Diagnostic Information


## GetBaudrate (FUN)


FUNCTION GetBaudrate : UINT
This function returns the current baudrate of the bus. Information can be also read by GetDiagnosis .
InOut:
Scope
Name
Type
Comment
Return
GetBaudrate
UINT
baudrate in kBit/s
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## GetBusAlarm (FUN)


FUNCTION GetBusAlarm : BOOL
This function returns if the CAN chip is in Bus Alarm state. In this state sending and receiving messages is not possible. A Bus Alarm can be reset by ResetBusAlarm which leads to a re-initialization of the CAN chip. Diagnostic Information can be also read by GetDiagnosis .
InOut:
Scope
Name
Type
Comment
Return
GetBusAlarm
BOOL
TRUE  if a bus alarm is pending.
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## GetBusload (FUN)


FUNCTION GetBusload : USINT
This function is not implemented by all drivers. It returns the current busload in percent. Diagnostic Information can be also read by GetDiagnosis .
InOut:
Scope
Name
Type
Comment
Return
GetBusload
USINT
bus load (0..100) in percent
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## GetBusState (FUN)


FUNCTION GetBusState : BUSSTATE
This function return the current state of the bus. Diagnostic Information can be also read by GetDiagnosis .
InOut:
Scope
Name
Type
Comment
Return
GetBusState
BUSSTATE
current bus state
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## GetDiagnosis (FUN)


FUNCTION GetDiagnosis : ERROR
Function returns all relevant diagnostic information for a specific driver.
InOut:
Scope
Name
Type
Comment
Return
GetDiagnosis
ERROR
ERROR.NO_ERROR or appropriate error code
Input
hDriver
CAA.HANDLE
handle of CAN interface
pDiagnosisInfo
POINTER TO DIAGNOSIS_INFO
Pointer to diagnostic information


---


## GetLostCounter (FUN)


FUNCTION GetLostCounter : CAA.COUNT
Returns a counter which is incremented with each lost message. Diagnostic Information can be also read by GetDiagnosis .
InOut:
Scope
Name
Type
Comment
Return
GetLostCounter
CAA.COUNT
number of lost messages
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## GetReceiveCounter (FUN)


FUNCTION GetReceiveCounter : CAA.COUNT
Returns a counter which is incremented with each received message. Diagnostic Information can be also read by GetDiagnosis .
InOut:
Scope
Name
Type
Comment
Return
GetReceiveCounter
CAA.COUNT
number of received messages
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## GetReceiveErrorCounter (FUN)


FUNCTION GetReceiveErrorCounter : CAA.COUNT
Returns a counter which is incremented with each receive error. Diagnostic Information can be also read by GetDiagnosis .
InOut:
Scope
Name
Type
Comment
Return
GetReceiveErrorCounter
CAA.COUNT
number of receive errors
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## GetReceivePoolSize (FUN)


FUNCTION GetReceivePoolSize : CAA.COUNT
Returns the number of free receive messages in global receive pool. Should be greater 0. Otherwise no more messages can be received. Diagnostic Information can be also read by GetDiagnosis .
InOut:
Scope
Name
Type
Comment
Return
GetReceivePoolSize
CAA.COUNT
number of free receive messages in global receive pool
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## GetReceiveQueueLength (FUN)


FUNCTION GetReceiveQueueLength : CAA.COUNT
Returns the number of messages in receive queue waiting for being processed by application or stack. Diagnostic Information can be also read by GetDiagnosis .
InOut:
Scope
Name
Type
Comment
Return
GetReceiveQueueLength
CAA.COUNT
number of messages in receive queue
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## GetTransmitCounter (FUN)


FUNCTION GetTransmitCounter : CAA.COUNT
Returns a counter which is incremented with each sent message. Diagnostic Information can be also read by GetDiagnosis .
InOut:
Scope
Name
Type
Comment
Return
GetTransmitCounter
CAA.COUNT
number of sent messages
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## GetTransmitErrorCounter (FUN)


FUNCTION GetTransmitErrorCounter : CAA.COUNT
Returns a counter which is incremented with each transmit error. Diagnostic Information can be also read by GetDiagnosis .
InOut:
Scope
Name
Type
Comment
Return
GetTransmitErrorCounter
CAA.COUNT
number of transmit errors
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## GetTransmitPoolSize (FUN)


FUNCTION GetTransmitPoolSize : CAA.COUNT
Returns the number of free transmit messages in the transmit message pool of the current driver. Should be greater 0. Otherwise no more messages can be sent. Diagnostic Information can be also read by GetDiagnosis .
InOut:
Scope
Name
Type
Comment
Return
GetTransmitPoolSize
CAA.COUNT
number of free transmit messages in transmit pool.
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## GetTransmitQueueLength (FUN)


FUNCTION GetTransmitQueueLength : CAA.COUNT
Returns number of messages in transmit queue waiting for being processed by CAN Minidriver. Diagnostic Information can be also read by GetDiagnosis .
InOut:
Scope
Name
Type
Comment
Return
GetTransmitQueueLength
CAA.COUNT
number of messages in transmit queue.
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## IsSendingActive (FUN)


FUNCTION IsSendingActive : BOOL
This function specifies whether the CAN hardware is busy sending CAN messages or whether further messages are stored and waiting to be sent.
InOut:
Scope
Name
Type
Comment
Return
IsSendingActive
BOOL
FALSE  if the sending queue is empty and the CAN hardware is actually not transmitting a message.
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## ResetBusAlarm (FUN)


FUNCTION ResetBusAlarm : ERROR
In case of a Bus Alarm ( GetBusAlarm returns  TRUE ) this function can be called to reset the CAN Hardware.
InOut:
Scope
Name
Type
Comment
Return
ResetBusAlarm
ERROR
ERROR.NO_ERROR or appropriate error code
Input
hDriver
CAA.HANDLE
handle of CAN interface


---


# Extended Functionality


## DisableSyncService (FUN)


FUNCTION DisableSyncService : ERROR
Disables the SYNC service for a given driver.
InOut:
Scope
Name
Type
Comment
Return
DisableSyncService
ERROR
ERROR.NO_ERROR or appropriate error code
Input
hDriver
CAA.HANDLE
handle of CAN interface


---


## EnableSyncService (FUN)


FUNCTION EnableSyncService : ERROR
Enables the SYNC service for a given network. The CANopen Stack uses this function for better SYNC accuracy. If service is enabled SYNC message will be sent by the CAN driver implementation.
> **Note:**

Sync Service is not supported by all CAN drivers.
InOut:
Scope
Name
Type
Comment
Return
EnableSyncService
ERROR
ERROR.NO_ERROR or appropriate error code
Input
hDriver
CAA.HANDLE
handle of CAN interface
cobID
CL2I.COBID
id of SYNC message
xSyncProducer
BOOL
TRUE: sync producer; FALSE: consumer
xEnableSyncEvent
BOOL
TRUE: fire event
udiSyncCycle
UDINT
SYNC cycle
udiSyncWindowLength
UDINT
SYNC window
udiSyncForewarnTime
UDINT
SYNC forewarn time in µs


---


# Indicator Services


## GetCiAState (FUN)


FUNCTION GetCiAState : USINT
Returns the current CiA LED state according to CiA 303-3. Interpretation of returned  USINT  see IndicatorConstants .
InOut:
Scope
Name
Type
Comment
Return
GetCiAState
USINT
current CiA state (see IndicatorConstants )
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## SetCiAState (FUN)


FUNCTION SetCiAState : ERROR
Sets the current CiA LED state according to CiA 303-3. Interpretation of  usiState  see IndicatorConstants .
InOut:
Scope
Name
Type
Comment
Return
SetCiAState
ERROR
ERROR.NO_ERROR or appropriate error code
Input
hDriver
CAA.HANDLE
handle of CAN interface
usiState
USINT
new CiA State (see IndicatorConstants )


---


# Message Information


## GetMessageDataPointer (FUN)


FUNCTION GetMessageDataPointer : POINTER TO CL2I.DATA
Returns pointer to the eight data bytes of a message. Number of valid bytes can be retrieved by GetMessageLength .
> **Note:**

The data is organised in the “Network Byte Order“ of the CANbus. The alignment of data types in the RTS memory may differ from the alignment in the data messages.
## Example

VAR
hMsg : CAA.HANDLE;
pData : POINTER TO CL2I.DATA;
usiMsgLen : USINT;
byFirstByte : BYTE;
bySecondByte : BYTE;
eError : CL2.ERROR;
END_VAR
IF hMsg <> CAA.gc_hINVALID THEN
//Get message data pointer
pData := CL2.GetMessageDataPointer(hMessage := hMsg, peError := ADR(eError));
usiMsgLen := CL2.GetMessageLength(hMessage := hMsg, peError := ADR(eError)); //get number of valid bytes
IF pData <> CAA.gc_pNULL THEN
byFirstByte := pData^[0];
bySecondByte := pData^[1];
END_IF
END_IF
InOut:
Scope
Name
Type
Comment
Return
GetMessageDataPointer
POINTER TO CL2I.DATA
Pointer to message data
Input
hMessage
CAA.HANDLE
handle of message
peError
POINTER TO ERROR
optional pointer to error enum


---


## GetMessageId (FUN)


FUNCTION GetMessageId : CL2I.COBID
Returns the COBID of a message
InOut:
Scope
Name
Type
Comment
Return
GetMessageId
CL2I.COBID
COBID of a message
Input
hMessage
CAA.HANDLE
handle of received message
peError
POINTER TO ERROR
optional pointer to error enum


---


## GetMessageLength (FUN)


FUNCTION GetMessageLength : USINT
Returns number of valid bytes in message.
## Example

See GetMessageDataPointer .
InOut:
Scope
Name
Type
Comment
Return
GetMessageLength
USINT
number of valid data bytes in message
Input
hMessage
CAA.HANDLE
handle of message
peError
POINTER TO ERROR
optional pointer to error enum


---


## GetMsgCount (FUN)


FUNCTION GetMsgCount : CAA.COUNT
Returns the number of messages in the receive queue of a given receiver.
InOut:
Scope
Name
Type
Comment
Return
GetMsgCount
CAA.COUNT
number of messages in receive queue of  hReceiverId .
Input
hReceiverId
CAA.HANDLE
receiver handle
peError
POINTER TO ERROR
optional pointer to error enum


---


## GetNetId (FUN)


FUNCTION GetNetId : USINT
Returns the NetID of a given message.
InOut:
Scope
Name
Type
Comment
Return
GetNetId
USINT
NetID of  hMessage .
Input
hMessage
CAA.HANDLE
handle of received message
peError
POINTER TO ERROR
optional pointer to error enum


---


## GetTimeStamp (FUN)


FUNCTION GetTimeStamp : UDINT
Returns the time stamp of a given message (if supported by CAN driver, else 0).
InOut:
Scope
Name
Type
Comment
Return
GetTimeStamp
UDINT
Time Stamp of  hMessage .
Input
hMessage
CAA.HANDLE
handle of received message
peError
POINTER TO ERROR
optional pointer to error enum


---


## Is29BitIdMessage (FUN)


FUNCTION Is29BitIdMessage : BOOL
This function determines if a specified message has an identifier with 11 bits or 29 bits.
InOut:
Scope
Name
Type
Comment
Return
Is29BitIdMessage
BOOL
TRUE  if messages is a 29 bit CAN message.
Input
hMessage
CAA.HANDLE
handle of message
peError
POINTER TO ERROR
optional pointer to error enum


---


## IsRTRMessage (FUN)


FUNCTION IsRTRMessage : BOOL
This function specifies whether a message is an RTR message.
InOut:
Scope
Name
Type
Comment
Return
IsRTRMessage
BOOL
TRUE  if messages is a RTR CAN message.
Input
hMessage
CAA.HANDLE
handle of message
peError
POINTER TO ERROR
optional pointer to error enum


---


## IsTransmitMessage (FUN)


FUNCTION IsTransmitMessage : BOOL
This function specifies whether a message was previously sent with Write .
InOut:
Scope
Name
Type
Comment
Return
IsTransmitMessage
BOOL
TRUE  if messages is a Transmit CAN message.
Input
hMessage
CAA.HANDLE
handle of message
peError
POINTER TO ERROR
optional pointer to error enum


---


## LostMessages (FUN)


FUNCTION LostMessages : UINT
Returns counter, which is incremented with every lost message of  hReceiverId
InOut:
Scope
Name
Type
Comment
Return
LostMessages
UINT
Counter, which is incremented with every lost message of  hReceiverId
Input
hReceiverId
CAA.HANDLE
handle of registered Ids
peError
POINTER TO ERROR
optional pointer to error enum


---


# Structures


## DIAGNOSIS_INFO (STRUCT)


TYPE DIAGNOSIS_INFO : STRUCT
This structure contains all relevant diagnostic information for a CAN network. It can be retrieved by GetDiagnosis .
InOut:
Name
Type
Comment
uiBaudrate
UINT
current Baudrate of CAN driver
usiBusLoad
USINT
current busload calculated by CAN Minidriver. Not all minidrivers implement this feature.
xBusAlarm
BOOL
Shows if CAN Minidriver signals a pending busalarm.
eBusState
BUSSTATE
current bus state signaled by CAN Minidriver
ctTxCounter
CAA.COUNT
transmit counter provided by CAN Minidriver
ctTxErrorCounter
CAA.COUNT
Tx Error Counter provided by CAN Minidriver (Tx Error register); should be always zero (unequal zero means buserror)
ctRxCounter
CAA.COUNT
receive counter provided by CAN Minidriver
ctRxErrorCounter
CAA.COUNT
Rx Error counter provided by CAN Minidriver (Rx Error register); should be always zero (unequal zero means buserror)
ctLostCounter
CAA.COUNT
Rx Lost counter provided by CAN Minidriver; should be always zero (unequal zero means Rx message lost because of overrun or no free message handle)
ctFreeRxMessages
CAA.COUNT
free messages for receiving; should be greater 0
ctMessagesRxQueue
CAA.COUNT
messages in receive queue waiting for being processed by application or stack
ctFreeTxMessages
CAA.COUNT
free messages for transmitting; should be greater zero otherwise no new tx messages possible (=> CreateMessage returns  CAA.gc_hINVALID )
ctMessagesTxQueue
CAA.COUNT
messages in transmit queue waiting for being processed by CAN Minidriver


---


# Global Variables


## IndicatorConstants (GVL)


This GVL defines the states of the two device LEDs according to CiA 303-3. These states are returned by GetCiAState and set by SetCiAState . The Error LED  gc_usiERR_...  (red) is represented by the lower 4 bit of CiA State, the RUN LED  gc_usiRUN_...  (green) by the higher 4 bit.
InOut:
Scope
Name
Type
Initial
Comment
Constant
gc_usiERR_OFF
USINT
16#0
led off = no error
gc_usiERR_ON
USINT
16#1
led on = Bus off
gc_usiERR_FLK
USINT
16#2
flickering = LSS/Auto-bitrate detection
gc_usiERR_BLK
USINT
16#3
blinking = Invalid Configuration
gc_usiERR_SFL
USINT
16#4
single flash = Warning LIMIT reached
gc_usiERR_DFL
USINT
16#5
double flash = Error control event
gc_usiERR_TFL
USINT
16#6
triple flash = Sync error
gc_usiERR_QFL
USINT
16#7
quadruple flash = Event timer error
gc_usiRUN_OFF
USINT
16#0
led off = not running
gc_usiRUN_ON
USINT
16#10
led on = Operational
gc_usiRUN_FLK
USINT
16#20
flickering = LSS/Auto-bitrate detection
gc_usiRUN_BLK
USINT
16#30
blinking = Preoperational
gc_usiRUN_SFL
USINT
16#40
single flash = Stopped
gc_usiRUN_DFL
USINT
16#50
double flash = PROGRAM/Firmeware download
gc_usiRUN_TFL
USINT
16#60
triple flash = reserved
gc_usiRUN_QFL
USINT
16#70
quadruple flash = reserved


---


# Internal - Basic Functions


## _CloneMessage (FUN)


FUNCTION _CloneMessage : CAA.HANDLE
Unmanaged implementation of CloneMessage
InOut:
Scope
Name
Type
Comment
Return
_CloneMessage
CAA.HANDLE
cloned message handle
Input
hMessage
CAA.HANDLE
handle of message to clone
peError
POINTER TO ERROR
optional pointer to error enum


---


## _CreateArrayReceiver (FUN)


FUNCTION _CreateArrayReceiver : CAA.HANDLE
Creates an Array Receiver.
InOut:
Scope
Name
Type
Comment
Return
_CreateArrayReceiver
CAA.HANDLE
new receiver handle or  CAA.gc_hINVALID  in case of failure
Input
hDriver
CAA.HANDLE
handle of CAN interface
paSortedCOBIDs
POINTER TO CL2I.ARRAY_RECV_ENTRY
array filled with COBIDs of interest sorted by COBID
ctCOBIDs
CAA.COUNT
number of COBIDs contained in paSortedCOBIDs
eEvent
CB.EVENT
trigger event when message received
xEnableSyncWindow
BOOL
use SYNC window ==> not implemented
peError
POINTER TO ERROR
optional pointer to error enum


---


## _CreateIdAreaReceiver (FUN)


FUNCTION _CreateIdAreaReceiver : CAA.HANDLE
Unmanaged implementation of CreateIdAreaReceiver
InOut:
Scope
Name
Type
Comment
Return
_CreateIdAreaReceiver
CAA.HANDLE
Input
hDriver
CAA.HANDLE
handle of CAN interface
xAlwaysNewest
BOOL
TRUE: returns only the newest message; FALSE: receiver with queue.
eEvent
CB.EVENT
trigger event when message received
xEnableSyncWindow
BOOL
use SYNC window: not implemented ==> do not care
peError
POINTER TO ERROR
optional pointer to error enum


---


## _CreateMaskReceiver (FUN)


FUNCTION _CreateMaskReceiver : CAA.HANDLE
Unmanaged implementation of CreateMaskReceiver
InOut:
Scope
Name
Type
Comment
Return
_CreateMaskReceiver
CAA.HANDLE
new receiver handle or  CAA.gc_hINVALID  in case of failure
Input
hDriver
CAA.HANDLE
handle of CAN interface
cobIdValue
CL2I.COBID
CobID value
cobIdMask
CL2I.COBID
CobID mask
xRTRValue
BOOL
RTR value
xRTRMask
BOOL
RTR mask
x29BitIdValue
BOOL
29 Bit Id value
x29BitIdMask
BOOL
29 Bit Id mask
xTransmitValue
BOOL
Transmit message value
xTransmitMask
BOOL
Transmit message mask
xAlwaysNewest
BOOL
TRUE: returns only the newest message; FALSE: receiver with queue.
eEvent
CB.EVENT
trigger event when message received
xEnableSyncWindow
BOOL
use SYNC window: not implemented ==> do not care
peError
POINTER TO ERROR
optional pointer to error enum


---


## _CreateMessage (FUN)


FUNCTION _CreateMessage : CAA.HANDLE
Unmanaged implementation of CreateMessage
InOut:
Scope
Name
Type
Comment
Return
_CreateMessage
CAA.HANDLE
new message handle
Input
hDriver
CAA.HANDLE
handle of CAN interface
cobID
CL2I.COBID
cob ID
usiLength
USINT
length of valid data bytes
xRTR
BOOL
RTR bit
x29BitID
BOOL
29 Bit ID
peError
POINTER TO ERROR
optional pointer to error enum


---


## _CreateSingleIdReceiver (FUN)


FUNCTION _CreateSingleIdReceiver : CAA.HANDLE
Unmanaged implementation of CreateSingleIdReceiver
InOut:
Scope
Name
Type
Comment
Return
_CreateSingleIdReceiver
CAA.HANDLE
new receiver handle or  CAA.gc_hINVALID  in case of failure
Input
hDriver
CAA.HANDLE
handle of CAN interface
cobId
CL2I.COBID
id of message to be received
xRTR
BOOL
RTR bit
x29BitId
BOOL
29 Bit Id
xTransmit
BOOL
Transmit message
xAlwaysNewest
BOOL
TRUE: returns only the newest message; FALSE: receiver with queue.
eEvent
CB.EVENT
trigger event when message received
xEnableSyncWindow
BOOL
use SYNC window: not implemented ==> do not care
peError
POINTER TO ERROR
optional pointer to error enum


---


## _DeleteReceiver (FUN)


FUNCTION _DeleteReceiver : ERROR
Unmanaged implementation of DeleteReceiver
InOut:
Scope
Name
Type
Comment
Return
_DeleteReceiver
ERROR
ERROR.NO_ERROR or appropriate error code
Input
hReceiverId
CAA.HANDLE
handle of receiver


---


## _DriverClose (FUN)


FUNCTION _DriverClose : ERROR
Unmanaged implementation of DriverClose
InOut:
Scope
Name
Type
Comment
Return
_DriverClose
ERROR
ERROR.NO_ERROR or appropriate error code
Input
hDriver
CAA.HANDLE
handle of CAN interface


---


## _DriverGetSize (FUN)


FUNCTION _DriverGetSize : CAA.SIZE
See DriverGetSize .
InOut:
Scope
Name
Type
Comment
Return
_DriverGetSize
CAA.SIZE
Required memory size for _DriverOpenP
Input
usiNetId
USINT
xSupport29Bit
BOOL
ctMessages
CAA.COUNT
peError
POINTER TO ERROR


---


## _DriverOpenH (FUN)


FUNCTION _DriverOpenH : CAA.HANDLE
Unmanaged implementation of DriverOpenH
InOut:
Scope
Name
Type
Comment
Return
_DriverOpenH
CAA.HANDLE
handle of CAN interface or  CAA.gc_hINVALID  if failed.
Input
usiNetId
USINT
number of CAN network [0..n]
uiBaudrate
UINT
Baudrate in kBit/s
xSupport29Bits
BOOL
FALSE: only 11-Bit IDs, TRUE: support also 29-Bit
ctMessages
CAA.COUNT
number of transmit messages which should be allocated
peError
POINTER TO ERROR
optional pointer to error enum


---


## _DriverOpenP (FUN)


FUNCTION _DriverOpenP : CAA.HANDLE
Unmanaged implementation of DriverOpenP
InOut:
Scope
Name
Type
Comment
Return
_DriverOpenP
CAA.HANDLE
Input
usiNetId
USINT
number of CAN channel
uiBaudrate
UINT
baudrate in kBit/s
xSupport29Bits
BOOL
FALSE: only 11-Bit IDs, TRUE: support also 29-Bit
szMemSize
CAA.SIZE
size of allocated memory
pMemory
CAA.PVOID
pointer to memory
peError
POINTER TO ERROR


---


## _FreeMessage (FUN)


FUNCTION _FreeMessage : ERROR
Unmanaged implementation of FreeMessage
InOut:
Scope
Name
Type
Comment
Return
_FreeMessage
ERROR
ERROR.NO_ERROR or appropriate error code
Input
hMessage
CAA.HANDLE
handle of message to be freed


---


## _Read (FUN)


FUNCTION _Read : CAA.HANDLE
Unmanaged implementation of Read
InOut:
Scope
Name
Type
Comment
Return
_Read
CAA.HANDLE
handle of received CAN message or  CAA.gc_hINVALID  if receiver is empty.
Input
hReceiverId
CAA.HANDLE
receiver handle
pctMsgLeft
POINTER TO CAA.COUNT
Optional pointer to  ctMsgLeft . After calling  CL2.Read ctMsgLeft  contains the number of remaining messages in receive queue.
peError
POINTER TO ERROR
optional pointer to error enum


---


## _ReadArrayReceiver (FUN)


FUNCTION _ReadArrayReceiver : CAA.HANDLE
Reads messages from an Array Receiver created by _CreateArrayReceiver
InOut:
Scope
Name
Type
Comment
Return
_ReadArrayReceiver
CAA.HANDLE
handle of received CAN message or  CAA.gc_hINVALID  if receiver is empty.
Input
hArrayReceiver
CAA.HANDLE
handle of array receiver
ctIndex
CAA.COUNT
specifies the array entry which should be read
pctMsgLeft
POINTER TO CAA.COUNT
returns number of messages currently in the receiver
peError
POINTER TO ERROR
optional pointer to error enum


---


## _RegisterIdArea (FUN)


FUNCTION _RegisterIdArea : ERROR
Unmanaged implementation of RegisterIdArea
InOut:
Scope
Name
Type
Comment
Return
_RegisterIdArea
ERROR
ERROR.NO_ERROR or appropriate error code
Input
hReceiverId
CAA.HANDLE
Handle from CreateIdAreaReceiver
cobIdStart
CL2I.COBID
start id of message to be received
cobIdEnd
CL2I.COBID
end id of message to be received
xRTRValue
BOOL
Value RTR bit
xRTRMask
BOOL
Mask RTR bit
x29BitIdValue
BOOL
Value 29 Bit Id
x29BitIdMask
BOOL
Mask 29 Bit Id
xTransmitValue
BOOL
Value Transmit message
xTransmitMask
BOOL
Mask Transmit message


---


## _UnregisterIdArea (FUN)


FUNCTION _UnregisterIdArea : ERROR
Unmanaged implementation of UnregisterIdArea
InOut:
Scope
Name
Type
Comment
Return
_UnregisterIdArea
ERROR
ERROR.NO_ERROR or appropriate error code
Input
hReceiverId
CAA.HANDLE
Handle returned by CreateIdAreaReceiver
cobIdStart
CL2I.COBID
start id of message to be received
cobIdEnd
CL2I.COBID
end id of message to be received
xRTRValue
BOOL
Value RTR bit
xRTRMask
BOOL
Mask RTR bit
x29BitIdValue
BOOL
Value 29 Bit Id
x29BitIdMask
BOOL
Mask 29 Bit Id
xTransmitValue
BOOL
Value Transmit Message
xTransmitMask
BOOL
Mask Transmit Message


---


## _Write (FUN)


FUNCTION _Write : ERROR
Unmanaged implementation of Write
InOut:
Scope
Name
Type
Comment
Return
_Write
ERROR
ERROR.NO_ERROR or appropriate error code
Input
hDriver
CAA.HANDLE
handle of CAN interface
hMessage
CAA.HANDLE
handle of message to be written
usiPriority
USINT
priority of message:
0:  send immediately;
1-n:  priority (1: high, n: low), default is n = 8
xEnableSyncWindow
BOOL
use SYNC window => not implemented; do not care


---


# Internal - Diagnostic Information


## _GetBaudrate (FUN)


FUNCTION _GetBaudrate : UINT
Unmanaged implementation of GetBaudrate
InOut:
Scope
Name
Type
Comment
Return
_GetBaudrate
UINT
baudrate in kBit/s
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## _GetBusAlarm (FUN)


FUNCTION _GetBusAlarm : BOOL
Unmanaged implementation of GetBusAlarm
InOut:
Scope
Name
Type
Comment
Return
_GetBusAlarm
BOOL
TRUE  if a bus alarm is pending.
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## _GetBusload (FUN)


FUNCTION _GetBusload : USINT
Unmanaged implementation of GetBusload
InOut:
Scope
Name
Type
Comment
Return
_GetBusload
USINT
bus load (0..100) in percent
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## _GetBusState (FUN)


FUNCTION _GetBusState : BUSSTATE
Unmanaged implementation of GetBusState
InOut:
Scope
Name
Type
Comment
Return
_GetBusState
BUSSTATE
current bus state
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## _GetDiagnosis (FUN)


FUNCTION _GetDiagnosis : ERROR
Unmanaged implementation of GetDiagnosis
InOut:
Scope
Name
Type
Comment
Return
_GetDiagnosis
ERROR
ERROR.NO_ERROR or appropriate error code
Input
hDriver
CAA.HANDLE
handle of CAN interface
pDiagnosisInfo
POINTER TO DIAGNOSIS_INFO
Pointer to diagnostic information


---


## _GetLostCounter (FUN)


FUNCTION _GetLostCounter : CAA.COUNT
Unmanaged implementation of GetLostCounter
InOut:
Scope
Name
Type
Comment
Return
_GetLostCounter
CAA.COUNT
number of lost messages
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## _GetReceiveCounter (FUN)


FUNCTION _GetReceiveCounter : CAA.COUNT
Unmanaged implementation of GetReceiveCounter
InOut:
Scope
Name
Type
Comment
Return
_GetReceiveCounter
CAA.COUNT
number of received messages
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## _GetReceiveErrorCounter (FUN)


FUNCTION _GetReceiveErrorCounter : CAA.COUNT
Unmanaged implementation of GetReceiveErrorCounter
InOut:
Scope
Name
Type
Comment
Return
_GetReceiveErrorCounter
CAA.COUNT
number of receive errors
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## _GetReceivePoolSize (FUN)


FUNCTION _GetReceivePoolSize : CAA.COUNT
Unmanaged implementation of GetReceivePoolSize
InOut:
Scope
Name
Type
Comment
Return
_GetReceivePoolSize
CAA.COUNT
number of free receive messages in global receive pool
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## _GetReceiveQueueLength (FUN)


FUNCTION _GetReceiveQueueLength : CAA.COUNT
Unmanaged implementation of GetReceiveQueueLength
InOut:
Scope
Name
Type
Comment
Return
_GetReceiveQueueLength
CAA.COUNT
number of messages in receive queue
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## _GetTransmitCounter (FUN)


FUNCTION _GetTransmitCounter : CAA.COUNT
Unmanaged implementation of GetTransmitCounter
InOut:
Scope
Name
Type
Comment
Return
_GetTransmitCounter
CAA.COUNT
number of sent messages
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## _GetTransmitErrorCounter (FUN)


FUNCTION _GetTransmitErrorCounter : CAA.COUNT
Unmanaged implementation of GetTransmitErrorCounter
InOut:
Scope
Name
Type
Comment
Return
_GetTransmitErrorCounter
CAA.COUNT
number of transmit errors
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## _GetTransmitPoolSize (FUN)


FUNCTION _GetTransmitPoolSize : CAA.COUNT
Unmanaged implementation of GetTransmitPoolSize
InOut:
Scope
Name
Type
Comment
Return
_GetTransmitPoolSize
CAA.COUNT
number of free transmit messages in transmit pool.
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## _GetTransmitQueueLength (FUN)


FUNCTION _GetTransmitQueueLength : CAA.COUNT
Unmanaged implementation of GetTransmitQueueLength
InOut:
Scope
Name
Type
Comment
Return
_GetTransmitQueueLength
CAA.COUNT
number of messages in transmit queue.
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## _IsSendingActive (FUN)


FUNCTION _IsSendingActive : BOOL
Unmanaged implementation of IsSendingActive
InOut:
Scope
Name
Type
Comment
Return
_IsSendingActive
BOOL
FALSE  if the sending queue is empty and the CAN hardware is actually not transmitting a message.
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## _ResetBusAlarm (FUN)


FUNCTION _ResetBusAlarm : ERROR
Unmanaged implementation of ResetBusAlarm
InOut:
Scope
Name
Type
Comment
Return
_ResetBusAlarm
ERROR
ERROR.NO_ERROR or appropriate error code
Input
hDriver
CAA.HANDLE
handle of CAN interface


---


# Internal - Extended Functionality


## _DisableSyncService (FUN)


FUNCTION _DisableSyncService : ERROR
Unmanaged implementation of DisableSyncService
InOut:
Scope
Name
Type
Comment
Return
_DisableSyncService
ERROR
ERROR.NO_ERROR or appropriate error code
Input
hDriver
CAA.HANDLE
handle of CAN interface


---


## _EnableSyncService (FUN)


FUNCTION _EnableSyncService : ERROR
Unmanaged implementation of EnableSyncService
InOut:
Scope
Name
Type
Comment
Return
_EnableSyncService
ERROR
ERROR.NO_ERROR or appropriate error code
Input
hDriver
CAA.HANDLE
handle of CAN interface
cobID
CL2I.COBID
id of SYNC message
xSyncProducer
BOOL
TRUE: sync producer; FALSE: consumer
xEnableSyncEvent
BOOL
TRUE: fire event
udiSyncCycle
UDINT
SYNC cycle
udiSyncWindowLength
UDINT
SYNC window
udiSyncForewarnTime
UDINT
SYNC forewarn time in µs


---


# Internal - Indicator Services


## _GetCiAState (FUN)


FUNCTION _GetCiAState : USINT
Unmanaged implementation of GetCiAState
InOut:
Scope
Name
Type
Comment
Return
_GetCiAState
USINT
current CiA state (see IndicatorConstants )
Input
hDriver
CAA.HANDLE
handle of CAN interface
peError
POINTER TO ERROR
optional pointer to error enum


---


## _SetCiAState (FUN)


FUNCTION _SetCiAState : ERROR
Unmanaged implementation of SetCiAState
InOut:
Scope
Name
Type
Comment
Return
_SetCiAState
ERROR
ERROR.NO_ERROR or appropriate error code
Input
hDriver
CAA.HANDLE
handle of CAN interface
usiState
USINT
new CiA State (see IndicatorConstants )


---


# Internal - Message Information


## _GetMessageDataPointer (FUN)


FUNCTION _GetMessageDataPointer : POINTER TO CL2I.DATA
Unmanaged implementation of GetMessageDataPointer
InOut:
Scope
Name
Type
Comment
Return
_GetMessageDataPointer
POINTER TO CL2I.DATA
Pointer to message data
Input
hMessage
CAA.HANDLE
handle of message
peError
POINTER TO ERROR
optional pointer to error enum


---


## _GetMessageId (FUN)


FUNCTION _GetMessageId : CL2I.COBID
Unmanaged implementation of GetMessageId
InOut:
Scope
Name
Type
Comment
Return
_GetMessageId
CL2I.COBID
COBID of a message
Input
hMessage
CAA.HANDLE
handle of received message
peError
POINTER TO ERROR
optional pointer to error enum


---


## _GetMessageLength (FUN)


FUNCTION _GetMessageLength : USINT
Unmanaged implementation of GetMessageLength
InOut:
Scope
Name
Type
Comment
Return
_GetMessageLength
USINT
number of valid data bytes in message
Input
hMessage
CAA.HANDLE
handle of received message
peError
POINTER TO ERROR
optional pointer to error enum


---


## _GetMsgCount (FUN)


FUNCTION _GetMsgCount : CAA.COUNT
Unmanaged implementation of GetMsgCount
InOut:
Scope
Name
Type
Comment
Return
_GetMsgCount
CAA.COUNT
number of messages in receive queue of  hReceiverId .
Input
hReceiverId
CAA.HANDLE
receiver handle
peError
POINTER TO ERROR
optional pointer to error enum


---


## _GetNetId (FUN)


FUNCTION _GetNetId : USINT
Unmanaged implementation of GetNetId
InOut:
Scope
Name
Type
Comment
Return
_GetNetId
USINT
NetID of  hMessage .
Input
hMessage
CAA.HANDLE
handle of received message
peError
POINTER TO ERROR
optional pointer to error enum


---


## _GetTimeStamp (FUN)


FUNCTION _GetTimeStamp : UDINT
Unmanaged implementation of GetTimeStamp
InOut:
Scope
Name
Type
Comment
Return
_GetTimeStamp
UDINT
Time Stamp of  hMessage .
Input
hMessage
CAA.HANDLE
handle of received message
peError
POINTER TO ERROR
optional pointer to error enum


---


## _Is29BitIdMessage (FUN)


FUNCTION _Is29BitIdMessage : BOOL
Unmanaged implementation of Is29BitIdMessage
InOut:
Scope
Name
Type
Comment
Return
_Is29BitIdMessage
BOOL
TRUE  if messages is a 29 bit CAN message.
Input
hMessage
CAA.HANDLE
handle of message
peError
POINTER TO ERROR
optional pointer to error enum


---


## _IsRTRMessage (FUN)


FUNCTION _IsRTRMessage : BOOL
Unmanaged implementation of IsRTRMessage
InOut:
Scope
Name
Type
Comment
Return
_IsRTRMessage
BOOL
TRUE  if messages is a RTR CAN message.
Input
hMessage
CAA.HANDLE
handle of message
peError
POINTER TO ERROR
optional pointer to error enum


---


## _IsTransmitMessage (FUN)


FUNCTION _IsTransmitMessage : BOOL
Unmanaged implementation of IsTransmitMessage
InOut:
Scope
Name
Type
Comment
Return
_IsTransmitMessage
BOOL
TRUE  if messages is a Transmit CAN message.
Input
hMessage
CAA.HANDLE
handle of message
peError
POINTER TO ERROR
optional pointer to error enum


---


## _LostMessages (FUN)


FUNCTION _LostMessages : UINT
Unmanaged implementation of LostMessages
InOut:
Scope
Name
Type
Comment
Return
_LostMessages
UINT
Counter, which is incremented with every lost message of  hReceiverId
Input
hReceiverId
CAA.HANDLE
handle of registered Ids
peError
POINTER TO ERROR
optional pointer to error enum


---


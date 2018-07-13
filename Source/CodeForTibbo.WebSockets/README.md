# Tibbo C WebSockets
This is an experimental Proof Of Conecpt Library for implementing WebSocket communications with Tibbo Devices.
This library was designed for the EM2000W but should function on all Tibbo Embedded Modules.

# Set-up
In order to use this library in your own projects, first clone this repo or download all <*.tc> and <*.th> files.

- Now that you have the source files, add them to your project directory.

- Once added, make sure to place a reference to the header with <#include "websocket.th";>, usually in <global.th>.

- Ensure that the SOCK library is added. See http://docs.tibbo.com/taiko/lib_sock_step_by_step.htm for more info.

- Make sure that the <net.ip> value in <main.tc> and the websocket address in <index.html> match and are correct for your environment.

# Use Instructions
First add <ws_assign_socket(sock_get(""))> to your device configuration.

Next add <ws_proc_data()> to your on_sock_data_arrival() event.

Finally create the <callback_websocket_message(string& data)> functon somewhere within your project.

# NOTE
This library is currently in the experimental state. As such the following issues should be noted:

- Continuation Frames are not supported.

- Text frames are the only data type frames currently supported.

- Very rarely, the calculated WebSocket-Accepts header may be incorrect. Refreshing usually solves this.

- Support for sending data greater than 255 characters is not supported.
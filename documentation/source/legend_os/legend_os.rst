LegendOS
================

The LegendOS is the operating system of the legend espresso machine. It consists of an instance of LegendIO (setters and getters for all physical devices), LegendComm (communication interface e.g. to the companion via serial) and a StateMachine.

.. uml:: architecture.puml


LegendIO
---------

The inputs and outputs of the LegendOS are abstracted as components e.g. Motor, FlowMeter, Temperature, etc. These components are all inheriting from the Component base class. 

The physical machine is abstracted as a set of setters and getters which are defined in the LegendIO.hpp. These virtual functions are implemented in 

LegendComm
------------

The data that can be communicated from and to the LegendOS is defined by a protobuf definition. `Protocol buffers <https://developers.google.com/protocol-buffers>`_ are language and platform-neutral mechanism for serializing structured data. The LegendComm component implements methods for handling incoming and sending protobuf-messages. The actual communication interface (e.g. serial, wifi, etc.) is implemented in an inheriting class of LegendComm e.g. SerialComm which implements the pure virtual function ``_sendPacket`` and calls ``_recvPacket`` on receiving data.

StateMachine
-------------

The state machine uses the LegendIO to set outputs, change state depending on specific inputs. 

.. uml:: state-diagram.puml

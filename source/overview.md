# Overview

The state-machine repository contains the operating system for the legend. It currently runs on an ESP32 MCU but has a quite good abstraction layer so probably other MCUs will be supported in the future.

The companion repository contains a python application (companion) which connects to the state-machine. It can monitor inputs and outputs, write data to csvs, run custom macros and provide data for a prometheus server. It can start a TUI (Terminal User Interface) to set outputs, show data and force the state machine to switch to specific states.
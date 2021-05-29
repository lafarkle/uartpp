# uartpp
Various Code to do Packet Processing on UART/Com Port/RS232/RS422/RS485 packets

UARTs provide a cheap and easy methodology for connecting 2 devices.  This used to be a Terminal to a Mainframe or a Terminal to a Modem.  High End Serial Communciations has long ago gone to packet-based communications where Synchronization (Sync) of the **Start Delimiter** or Sync Byte is unique.  Examples of this include USB, Ethernet, HDLC/SDLC, and CANBus.  However, for many embedded hardware applications, UARTs are still commononly used.  Most processing relies on failing a Checksum/CRC error as sufficient to guarantee data communications.  While this is good enough in most cases to verify data integrity, it doesn't guarantee a quick reacquisition of valid packet processing.  This is particuarly the case where the byte chosen to be the Sync Byte appears in the data of the packet frequently.


For the case of GPS Protocol NMEA-0183, the **Start Delimiter** is '$' (0x24).  


So, for the code:
o The data is in a queue
o there is an error byte read from the UART that is in the queue
o Errors are counted
o there is a defined Calculation, use XOR to keep up with the NMEA example, and for simplicity

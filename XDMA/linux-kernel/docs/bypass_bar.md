<!--
Copyright (c) 2025-present,  Helmholtz-Zentrum Berlin
All rights reserved.
Permission is granted to copy, distribute and/or modify this document
under the terms of the GNU Free Documentation License, Version 1.3 or
any later version published by the Free Software Foundation.
-->

Host bypass BAR may be useful for small transfers that require low and stable latency.
However, exact detail may vary between CPU architectures and read and write operation.
For illustration here is transfer write and read of 1024 bytes on bypass BAR on x86-64 
arch.

Write operation is very fast, probably because it simply puts the data onto hardware 
trasfer queue and doesn't wait for the acknowledgement. This behaviour might be, however,
different on another architecture.
![bypass write op](./img/bypass_write.png)

Read operation must, however, wait for the return of data from the FPGA, therefore has
much larger latency
![bypass read op](./img/bypass_read.png)

Thus it is advisable to test, preferably monitored by ILA, whether it suits your
application.
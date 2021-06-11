#  <div align="center"> LSCPU </div>
## Objective
The Objective of the task is to learn about how lscpu command works in linux system and its use cases. 

## Discription
lscpu  gathers  CPU architecture information from sysfs, /proc/cpuinfo and any applicable architecture-specific libraries .The command output can be optimized for parsing or for easy  readability by humans.The information includes, for example, the number of CPUs, threads, cores, sockets etc.There is also information about the CPU caches and cache sharing,family,model,byte order, and stepping.
### Below is the example of command output:-
```Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    1
Core(s) per socket:    4
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 79
Model name:            Intel(R) Xeon(R) CPU E5-2686 v4 @ 2.30GHz
Stepping:              1
CPU MHz:               2300.009
BogoMIPS:              4600.10
Hypervisor vendor:     Xen
Virtualization type:   full
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              46080K
NUMA node0 CPU(s):     0-3
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 h lm constant_tsc rep_good nopl xtopology eagerfpu pni pclmulqdq ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_x f16c rdrand hypervisor lahf_lm abm invpcid_single fsgsbase bmi1 avx2 smep bmi2 erms invpcid xsaveopt 
```

## Features
Options that result in an output table have a list argument.  Use this  argument to  customize  the  command  output. See  COLUMNS  for a list of valid column labels.</br>
The column labels are not case sensitive.Not all columns are supported on all architectures.If an unsupported column is specified, lscpu prints the column but does not provide any data for it.
#### COLUMNS
 Note  that  topology  elements  (core,  socket, etc.) use a sequential unique ID starting from zero, but CPU logical numbers follow the kernel where there is  no guarantee of sequential numbering.
|Colums|Discription|
|:---:|----|
|**CPU**    |The logical CPU number of a CPU as used by the Linux kernel.|
|**CORE**|   The logical core number.  A core can contain several CPUs|.
|**SOCKET** |The logical socket number.  A socket can contain several cores.|
|**BOOK**  | The logical book number.  A book can contain several sockets.|
|**DRAWER** |The logical drawer number.  A drawer can contain several books.|
|**NODE**   |The logical NUMA node number.  A node can contain several drawers.|
|**CACHE**  |Information about how caches are shared between CPUs.|
|**ADDRESS** |The physical address of a CPU.|
|**ONLINE** |Indicator  that  shows  whether the Linux instance currently makes use of the CPU.|
|**CONFIGURED** |Indicator that shows if the hypervisor has allocated the CPU to the  virtual hardware on which the Linux instance runs.  CPUs that are configured can be set online by the Linux instance.|
|**POLARIZATION** |This column contains data for Linux instances that run on  virtual  hardware  with  a hypervisor that can switch the CPU dispatching mode (polarization).**Horizontal** & **Vertical**|
|**MAXMHZ** |Maximum megahertz value for the CPU. Useful when lscpu is used  as  hardware  inventory  information  gathering  tool.  Notice that the megahertz value is dynamic,  and  driven  by  CPU  governor  depending  on  current resource need.|
|**MINMHZ**| Minimum megahertz value for the CPU.|

#### OPTIONS

- **-a,** --all Include lines for online and offline CPUs in the output (default for -e). This option may only specified together with option -e or -p.
- **-b,** --online Limit the output to online CPUs (default for -p). This option may only be specified together with option -e or -p.
- **-c,** --offline Limit the output to offline CPUs. This option may only be specified together with option -e or -p.
- **-e,** --extended [=list] Display the CPU information in human readable format.If the list argument is omitted, all columns for which data is available are included in the command output.
When specifying the list argument, the string of option, equal sign (=), and list must not contain any blanks or other white space. Examples: '-e=cpu,node' or '--extended=cpu,node'.
- **-h,** --help Display help information and exit.
- **-p,** --parse [=list] Optimize the command output for easy parsing.If the list argument is omitted, the command output is compatible with earlier versions of lscpu. In this compatible format, two commas are used to separate CPU cache columns. If no CPU caches are identified the cache column is omitted.
If the list argument is used, cache columns are separated with a colon (:).
When specifying the list argument, the string of option, equal sign (=), and list must not contain any blanks or other white space. Examples: '-p=cpu,node' or '--parse=cpu,node'.
- **-s,** --sysroot directory
Gather CPU data for a Linux instance other than the instance from which the lscpu command is issued. The specified directory is the system root of the Linux instance to be inspected.
- **-x,** --hex Use hexadecimal masks for CPU sets (for example 0x3). The default is to print the sets in list format (for example 0,1).
- **-V,** --version Display version information and exit.


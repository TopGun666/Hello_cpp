# /proc/cpuinfo (查看CPU信息)
/proc/cpuinfo文件分析
　　在Linux系统中，提供了proc文件系统显示系统的软硬件信息。如果想了解系统中CPU的提供商和相关配置信息，则可以通过/proc/cpuinfo文件得到。本文章针对该文件进行简单的总结。

　　基于不同指令集（ISA）的CPU产生的/proc/cpuinfo文件不一样，基于X86指令集CPU的/proc/cpuinfo文件包含如下内容：

```
processor　　： 0
vendor_id　　：GenuineIntel
cpu family　　：6
model　　　　：26
model name　：Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
stepping　　  ：5
cpu MHz　　  ：1600.000
cache size　　： 8192 KB
physical id　　：0
siblings　　　 ：8
core id　　　  ： 0
cpu cores　　 ：4
apicid　　       ：0
fpu　　　　　  ：yes
fpu_exception ：yes
cpuid level　　 ： 11
wp　　　　　　：yes
flags 　　　　　： fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx rdtscp lm constant_tsc ida nonstop_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr popcnt lahf_lm
bogomips　　 ：4522.12
clflush size　　：64
cache_alignment　　： 64
address sizes　　　 ： 40 bits physical, 48 bits virtual
power management ：
```
以上输出项的含义如下：

```
processor　：系统中逻辑处理核的编号。对于单核处理器，则课认为是其CPU编号，对于多核处理器则可以是物理核、或者使用超线程技术虚拟的逻辑核。
vendor_id　：CPU制造商     
cpu family　：CPU产品系列代号
model　　　：CPU属于其系列中的哪一代的代号
model name：CPU属于的名字及其编号、标称主频
stepping　  ：CPU属于制作更新版本
cpu MHz　  ：CPU的实际使用主频
cache size   ：CPU二级缓存大小
physical id   ：单个CPU的标号
siblings       ：单个CPU逻辑物理核数
core id        ：当前物理核在其所处CPU中的编号，这个编号不一定连续
cpu cores    ：该逻辑核所处CPU的物理核数
apicid          ：用来区分不同逻辑核的编号，系统中每个逻辑核的此编号必然不同，此编号不一定连续
fpu             ：是否具有浮点运算单元（Floating Point Unit）
fpu_exception  ：是否支持浮点计算异常
cpuid level   ：执行cpuid指令前，eax寄存器中的值，根据不同的值cpuid指令会返回不同的内容
wp             ：表明当前CPU是否在内核态支持对用户空间的写保护（Write Protection）
flags          ：当前CPU支持的功能
bogomips   ：在系统内核启动时粗略测算的CPU速度（Million Instructions Per Second）
clflush size  ：每次刷新缓存的大小单位
cache_alignment ：缓存地址对齐单位
address sizes     ：可访问地址空间位数
power management ：对能源管理的支持，有以下几个可选支持功能：
```
```
　　ts：　　temperature sensor

　　fid：　  frequency id control

　　vid：　 voltage id control

　　ttp：　 thermal trip

　　tm：

　　stc：

　　100mhzsteps：

　　hwpstate：
```
　　

CPU信息中flags各项含义：

```
fpu： Onboard (x87) Floating Point Unit
vme： Virtual Mode Extension
de： Debugging Extensions
pse： Page Size Extensions
tsc： Time Stamp Counter: support for RDTSC and WRTSC instructions
msr： Model-Specific Registers
pae： Physical Address Extensions: ability to access 64GB of memory; only 4GB can be accessed at a time though
mce： Machine Check Architecture
cx8： CMPXCHG8 instruction
apic： Onboard Advanced Programmable Interrupt Controller
sep： Sysenter/Sysexit Instructions; SYSENTER is used for jumps to kernel memory during system calls, and SYSEXIT is used for jumps： back to the user code
mtrr： Memory Type Range Registers
pge： Page Global Enable
mca： Machine Check Architecture
cmov： CMOV instruction
pat： Page Attribute Table
pse36： 36-bit Page Size Extensions: allows to map 4 MB pages into the first 64GB RAM, used with PSE.
pn： Processor Serial-Number; only available on Pentium 3
clflush： CLFLUSH instruction
dtes： Debug Trace Store
acpi： ACPI via MSR
mmx： MultiMedia Extension
fxsr： FXSAVE and FXSTOR instructions
sse： Streaming SIMD Extensions. Single instruction multiple data. Lets you do a bunch of the same operation on different pieces of input： in a single clock tick.
sse2： Streaming SIMD Extensions-2. More of the same.
selfsnoop： CPU self snoop
acc： Automatic Clock Control
IA64： IA-64 processor Itanium.
ht： HyperThreading. Introduces an imaginary second processor that doesn’t do much but lets you run threads in the same process a  bit quicker.
nx： No Execute bit. Prevents arbitrary code running via buffer overflows.
pni： Prescott New Instructions aka. SSE3
vmx： Intel Vanderpool hardware virtualization technology
svm： AMD “Pacifica” hardware virtualization technology
lm： “Long Mode,” which means the chip supports the AMD64 instruction set
tm： “Thermal Monitor” Thermal throttling with IDLE instructions. Usually hardware controlled in response to CPU temperature.
tm2： “Thermal Monitor 2″ Decrease speed by reducing multipler and vcore.
est： “Enhanced SpeedStep”
```
根据以上内容，我们则可以很方便的知道当前系统关于CPU、CPU的核数、CPU是否启用超线程等信息。

查询系统具有多少个逻辑核：cat /proc/cpuinfo | grep "processor" | wc -l

查询系统CPU的物理核数：cat /proc/cpuinfo | grep "cpu cores" | uniq

查询系统CPU是否启用超线程：cat /proc/cpuinfo | grep -e "cpu cores"  -e "siblings" | sort | uniq

　　输出举例：

```
　　　　cpu cores    : 6
　　　　siblings    　: 6
```
　　如果cpu cores数量和siblings数量一致，则没有启用超线程，否则超线程被启用。

查询系统CPU的个数：cat /proc/cpuinfo | grep "physical id" | sort | uniq | wc -l

查询系统CPU是否支持某项功能，则根以上类似，输出结果进行sort， uniq和grep就可以得到结果。

【/proc/cpuinfo内容举例】

1，Intel(R) Xeon(R) X5355

processor　　: 0
vendor_id　　: GenuineIntel
cpu famil　　: 6
model　　　　 : 15
model name　 : Intel(R) Xeon(R) CPU           X5355  @ 2.66GHz
stepping　　 : 7
cpu MHz　　　: 2666.766
cache size　: 4096 KB
physical id　: 0
siblings　　 : 4
core id　　  : 0
cpu cores　　: 4
fpu　　　　　 : yes
fpu_exception　　: yes
cpuid level　　　: 10
wp　　　　　　: yes
flags　　　　: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr dca lahf_lm
bogomips    : 5338.26
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Xeon(R) CPU           X5355  @ 2.66GHz
stepping    : 7
cpu MHz        : 2666.766
cache size    : 4096 KB
physical id    : 1
siblings    : 4
core id        : 0
cpu cores    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr dca lahf_lm
bogomips    : 5333.75
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Xeon(R) CPU           X5355  @ 2.66GHz
stepping    : 7
cpu MHz        : 2666.766
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr dca lahf_lm
bogomips    : 5333.67
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Xeon(R) CPU           X5355  @ 2.66GHz
stepping    : 7
cpu MHz        : 2666.766
cache size    : 4096 KB
physical id    : 1
siblings    : 4
core id        : 2
cpu cores    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr dca lahf_lm
bogomips    : 5333.68
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 4
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Xeon(R) CPU           X5355  @ 2.66GHz
stepping    : 7
cpu MHz        : 2666.766
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr dca lahf_lm
bogomips    : 5333.67
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 5
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Xeon(R) CPU           X5355  @ 2.66GHz
stepping    : 7
cpu MHz        : 2666.766
cache size    : 4096 KB
physical id    : 1
siblings    : 4
core id        : 1
cpu cores    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr dca lahf_lm
bogomips    : 5333.68
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 6
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Xeon(R) CPU           X5355  @ 2.66GHz
stepping    : 7
cpu MHz        : 2666.766
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 3
cpu cores    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr dca lahf_lm
bogomips    : 5333.69
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 7
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Xeon(R) CPU           X5355  @ 2.66GHz
stepping    : 7
cpu MHz        : 2666.766
cache size    : 4096 KB
physical id    : 1
siblings    : 4
core id        : 3
cpu cores    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr dca lahf_lm
bogomips    : 5333.68
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:
2， Intel(R) Core(TM) i7 930 @ 2.80GHz

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Core(TM) i7 CPU         930  @ 2.80GHz
stepping	: 5
cpu MHz		: 2807.024
cache size	: 8192 KB
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu de tsc msr pae mce cx8 apic sep mtrr mca cmov pat clflush acpi mmx fxsr sse sse2 ss ht syscall nx lm constant_tsc rep_good nonstop_tsc aperfmperf pni est ssse3 cx16 sse4_1 sse4_2 popcnt hypervisor lahf_lm ida
bogomips	: 5614.04
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Core(TM) i7 CPU         930  @ 2.80GHz
stepping	: 5
cpu MHz		: 2807.024
cache size	: 8192 KB
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu de tsc msr pae mce cx8 apic sep mtrr mca cmov pat clflush acpi mmx fxsr sse sse2 ss ht syscall nx lm constant_tsc rep_good nonstop_tsc aperfmperf pni est ssse3 cx16 sse4_1 sse4_2 popcnt hypervisor lahf_lm ida
bogomips	: 5614.04
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Core(TM) i7 CPU         930  @ 2.80GHz
stepping	: 5
cpu MHz		: 2807.024
cache size	: 8192 KB
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu de tsc msr pae mce cx8 apic sep mtrr mca cmov pat clflush acpi mmx fxsr sse sse2 ss ht syscall nx lm constant_tsc rep_good nonstop_tsc aperfmperf pni est ssse3 cx16 sse4_1 sse4_2 popcnt hypervisor lahf_lm ida
bogomips	: 5614.04
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Core(TM) i7 CPU         930  @ 2.80GHz
stepping	: 5
cpu MHz		: 2807.024
cache size	: 8192 KB
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu de tsc msr pae mce cx8 apic sep mtrr mca cmov pat clflush acpi mmx fxsr sse sse2 ss ht syscall nx lm constant_tsc rep_good nonstop_tsc aperfmperf pni est ssse3 cx16 sse4_1 sse4_2 popcnt hypervisor lahf_lm ida
bogomips	: 5614.04
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 4
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Core(TM) i7 CPU         930  @ 2.80GHz
stepping	: 5
cpu MHz		: 2807.024
cache size	: 8192 KB
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu de tsc msr pae mce cx8 apic sep mtrr mca cmov pat clflush acpi mmx fxsr sse sse2 ss ht syscall nx lm constant_tsc rep_good nonstop_tsc aperfmperf pni est ssse3 cx16 sse4_1 sse4_2 popcnt hypervisor lahf_lm ida
bogomips	: 5614.04
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 5
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Core(TM) i7 CPU         930  @ 2.80GHz
stepping	: 5
cpu MHz		: 2807.024
cache size	: 8192 KB
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu de tsc msr pae mce cx8 apic sep mtrr mca cmov pat clflush acpi mmx fxsr sse sse2 ss ht syscall nx lm constant_tsc rep_good nonstop_tsc aperfmperf pni est ssse3 cx16 sse4_1 sse4_2 popcnt hypervisor lahf_lm ida
bogomips	: 5614.04
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 6
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Core(TM) i7 CPU         930  @ 2.80GHz
stepping	: 5
cpu MHz		: 2807.024
cache size	: 8192 KB
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu de tsc msr pae mce cx8 apic sep mtrr mca cmov pat clflush acpi mmx fxsr sse sse2 ss ht syscall nx lm constant_tsc rep_good nonstop_tsc aperfmperf pni est ssse3 cx16 sse4_1 sse4_2 popcnt hypervisor lahf_lm ida
bogomips	: 5614.04
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 7
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Core(TM) i7 CPU         930  @ 2.80GHz
stepping	: 5
cpu MHz		: 2807.024
cache size	: 8192 KB
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu de tsc msr pae mce cx8 apic sep mtrr mca cmov pat clflush acpi mmx fxsr sse sse2 ss ht syscall nx lm constant_tsc rep_good nonstop_tsc aperfmperf pni est ssse3 cx16 sse4_1 sse4_2 popcnt hypervisor lahf_lm ida
bogomips	: 5614.04
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:
【推荐资料】

1，http://www.unixresources.net/linux/clf/program/archive/00/00/66/13/661380.html#article666843

　　该参考资料为使用cpuid指令实际获取CPU信息代码，值得了解技术人士参阅

2，http://www.richweb.com/cpu_info

　　该参考资料列举了单核CPU情况下的cpuinfo文件、多核CPU使用超线程和不使用超线程的cpuinfo文件以及多个多核CPU情况下的cpuinfo文件，值得一看


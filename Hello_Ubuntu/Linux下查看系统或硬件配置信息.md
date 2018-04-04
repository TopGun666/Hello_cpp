#Linux下查看系统或硬件配置信息
## 一、在Linux下查看系统版本号信息命令

```
cat /etc/lsb-release
```
## 二、Linux下查看CPU信息

```
cat /proc/cpuinfo
```

eg:

```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 2
model name	: AMD FX(tm)-8320 Eight-Core Processor
stepping	: 0
microcode	: 0x6000822
cpu MHz		: 1400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 8
core id		: 0
cpu cores	: 4
apicid		: 16
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold bmi1
bogomips	: 7023.59
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 2
model name	: AMD FX(tm)-8320 Eight-Core Processor           
stepping	: 0
microcode	: 0x6000822
cpu MHz		: 1400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 8
core id		: 1
cpu cores	: 4
apicid		: 17
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold bmi1
bogomips	: 7023.59
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

processor	: 2
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 2
model name	: AMD FX(tm)-8320 Eight-Core Processor           
stepping	: 0
microcode	: 0x6000822
cpu MHz		: 1400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 8
core id		: 2
cpu cores	: 4
apicid		: 18
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold bmi1
bogomips	: 7023.59
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

processor	: 3
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 2
model name	: AMD FX(tm)-8320 Eight-Core Processor           
stepping	: 0
microcode	: 0x6000822
cpu MHz		: 3500.000
cache size	: 2048 KB
physical id	: 0
siblings	: 8
core id		: 3
cpu cores	: 4
apicid		: 19
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold bmi1
bogomips	: 7023.59
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

processor	: 4
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 2
model name	: AMD FX(tm)-8320 Eight-Core Processor           
stepping	: 0
microcode	: 0x6000822
cpu MHz		: 1400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 8
core id		: 4
cpu cores	: 4
apicid		: 20
initial apicid	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold bmi1
bogomips	: 7023.59
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

processor	: 5
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 2
model name	: AMD FX(tm)-8320 Eight-Core Processor           
stepping	: 0
microcode	: 0x6000822
cpu MHz		: 1400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 8
core id		: 5
cpu cores	: 4
apicid		: 21
initial apicid	: 5
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold bmi1
bogomips	: 7023.59
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

processor	: 6
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 2
model name	: AMD FX(tm)-8320 Eight-Core Processor           
stepping	: 0
microcode	: 0x6000822
cpu MHz		: 1400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 8
core id		: 6
cpu cores	: 4
apicid		: 22
initial apicid	: 6
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold bmi1
bogomips	: 7023.59
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

processor	: 7
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 2
model name	: AMD FX(tm)-8320 Eight-Core Processor           
stepping	: 0
microcode	: 0x6000822
cpu MHz		: 1400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 8
core id		: 7
cpu cores	: 4
apicid		: 23
initial apicid	: 7
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold bmi1
bogomips	: 7023.59
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

```

## 三、linux 下查看机器是cpu是几核的
1）几个cpu

```
more /proc/cpuinfo |grep "physical id"|uniq|wc -l
```
2）每个cpu是几核（假设cpu配置相同）

```
more /proc/cpuinfo |grep "physical id"|grep "0"|wc -l
cat /proc/cpuinfo | grep processor
```
3) 查看物理CPU的个数

 ```
cat /proc/cpuinfo |grep "physical id"|sort |uniq|wc -l
 ```
4) 查看逻辑CPU的个数

```
cat /proc/cpuinfo |grep "processor"|wc -l
```
5) 查看CPU是几核

```
cat /proc/cpuinfo |grep "cores"|uniq 
```
6) 查看CPU的主频

```
cat /proc/cpuinfo |grep MHz|uniq
```
 
## 查看当前操作系统内

```
uname -a
```
Result：

```
Linux euis1 2.6.9-55.ELsmp #1 SMP Fri Apr 20 17:03:35 EDT 2007 i686 i686 i386 GNU/Linux
```

Result：
```
cat /etc/issue | grep Linux
```

Result：

```
Red Hat Enterprise Linux AS release 4 (Nahant Update 5)
```
(查看当前操作系统发行版信息)

```
cat /proc/cpuinfo | grep name | cut -f2 -d: | uniq -c
```
Result：

```
8  Intel(R) Xeon(R) CPU            E5410   @ 2.33GHz
```
(看到有8个逻辑CPU, 也知道了CPU型号)

```
cat /proc/cpuinfo | grep physical | uniq -c
```
Result：

```
      4 physical id      : 0
      4 physical id      : 1
```
(说明实际上是两颗4核的CPU)

# getconf LONG_BIT
32
(说明当前CPU运行在32bit模式下, 但不代表CPU不支持64bit)

# cat /proc/cpuinfo | grep flags | grep ' lm ' | wc -l
8
(结果大于0, 说明支持64bit计算. lm指long mode, 支持lm则是64bit)
 
 
 
 
 
如何获得CPU的详细信息：
linux命令：cat /proc/cpuinfo
用命令判断几个物理CPU，几个核等：
逻辑CPU个数：
# cat /proc/cpuinfo | grep "processor" | wc -l
物理CPU个数：
# cat /proc/cpuinfo | grep "physical id" | sort | uniq | wc -l
每个物理CPU中Core的个数：
# cat /proc/cpuinfo | grep "cpu cores" | wc -l
是否为超线程？
如果有两个逻辑CPU具有相同的”core id”，那么超线程是打开的。
每个物理CPU中逻辑CPU(可能是core, threads或both)的个数：
# cat /proc/cpuinfo | grep "siblings"


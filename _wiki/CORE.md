---
layout: simple
title: CORE
revisions:
- author: Cuu 
  date: 2024-02-22
  comment: First version
---
## Core Modules

<table>
<thead>
<tr class="header">
<th><p>Model</p></th>
<th><p>CPU Microarchitecture</p></th>
<th><p>Frequency</p></th>
<th><p>Cores</p></th>
<th><p>GPU</p></th>
<th><p>RAM</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>A-0401</p></td>
<td><p>ARM64-bit Quad-core Cortex-A53</p></td>
<td><p>1.8GHz</p></td>
<td><p>4</p></td>
<td><p>Mali-T720</p></td>
<td><p>1GB LPDDR3</p></td>
</tr>
<tr class="even">
<td><p>A-0402</p></td>
<td><p>ARM64-bit Quad-core Cortex-A53</p></td>
<td><p>1.8GHz</p></td>
<td><p>4</p></td>
<td><p>Mali-T720</p></td>
<td><p>2GB LPDDR3</p></td>
</tr>
<tr class="odd">
<td><p>A-0602</p></td>
<td><p>ARM64-bit Dual-core Cortex-A72<br />
ARM64-bit Quad-core Cortex-A53</p></td>
<td><p>1.8GHz<br />
1.4GHz</p></td>
<td><p>6</p></td>
<td><p>Mali-T864</p></td>
<td><p>2GB LPDDR3</p></td>
</tr>
<tr class="even">
<td><p>A-0604</p></td>
<td><p>ARM64-bit Dual-core Cortex-A72<br />
ARM64-bit Quad-core Cortex-A53</p></td>
<td><p>1.8GHz<br />
1.4GHz</p></td>
<td><p>6</p></td>
<td><p>Mali-T864</p></td>
<td><p>4GB LPDDR3</p></td>
</tr>
<tr class="odd">
<td><p>RPI-CM3</p></td>
<td><p>ARM64-bit Quad-Core Cortex-A53<br />
(Raspberry PI CM3+ LITE)</p></td>
<td><p>1.2GHz</p></td>
<td><p>4</p></td>
<td><p>VideoCore 4</p></td>
<td><p>1GB LPDDR3</p></td>
</tr>
</tbody>
</table>

## DevTerm A-06 core CPU frequency scaling

*from yong on the [clockwork
forums](https://forum.clockworkpi.com/t/devterm-a-06-core-cpu-frequency-scaling/7135)*

The DevTerm A-06 core modules have 6 processor cores, arranged in ARM
big.LITTLE 3 heterogeneous computing architecture, combining relatively
battery-saving and slower processor ( LITTLE : \#0, \#1, \#2, \#3 )
cores with relatively more powerful and power-hungry ( big : \#4, \#5)
ones. You could have to option to turn on or off any core at any time
according to your own computing needs.

For example, the command to turn on core \#5 is:

`   sudo sh -c "echo 1 > /sys/devices/system/cpu/cpu5/online"`

the command to turn off core \#0 is:

`   sudo sh -c "echo 0 > /sys/devices/system/cpu/cpu0/online"`

The result could be verified with htop command.

In addition, user could simply use a tool called cpupower-gui to
configure core frequency and CPU scheduling governor: performance,
powersave, or schedutil and conservative. While powersave mode
aggressively keeps CPU cores running at the lowest frequency, the
performance mode always run in highest frequency. schedutil and
conservative will automatically adjust CPU frequency according to
application requirement, to achieve the balance between power-saving and
performance. That means, if you like, under extreme situations, the A-06
core module could be run either with only one LITTLE core at 408MHz, or
with all six cores at 1416MHz. There is ample room in between for
fine-tuning and dynamic controls. e.g. Android users love schedutil mode
for its efficiency, for details about scaling and different scaling
governors, please refer to:
<https://wiki.archlinux.org/title/CPU_frequency_scaling>

Similarly, A-06 GPU frequency and scheduling could be configured by
setting: /sys/devices/platform/ff9a0000.gpu/devfreq/ff9a0000.gpu/

By default, the A-06 core modules are set to run on 4 cores, with
conservative scaling governor, at 408-1000MHz.

You could play with these frequency scaling parameters according to your
specific application needs. For example, with these following commands,
the A-06 core could achieve potentially better power management than
CM3.

`   echo schedutil > /sys/devices/system/cpu/cpufreq/policy0/scaling_governor`

`   echo 800000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq`
`   echo 800000 > /sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq`

`   echo 0 > /sys/devices/system/cpu/cpu2/online`
`   echo 0 > /sys/devices/system/cpu/cpu3/online`

`   echo simple_ondemand > /sys/devices/platform/ff9a0000.gpu/devfreq/ff9a0000.gpu/governor`
`   echo 400000000 > /sys/devices/platform/ff9a0000.gpu/devfreq/ff9a0000.gpu/max_freq`
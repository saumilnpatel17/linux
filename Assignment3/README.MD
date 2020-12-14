<h1>Questions-Answers</h1><br/>
<b>For each member in your team, provide 1 paragraph detailing what parts of the lab that member implemented / researched. (You may skip this question if you are doing the lab by yourself).</b><br/><br/>

<b>Saumil (013829270)</b> - I have used vm environment from Assignment 2 where I had created Outer vm and Inner vm with ubuntu system installed on both of them. Then I also built the kernel using linux repo. Build steps: 1> make 2> make modules 3> make modules_install 4> make install. For all make commands, I used -j4 to use 4 cpus as my box has 8 cores. After this, we both have completed the assignment pretty much together going back and forth with each other on areas where we need to change the code, how to change the code and how to handle various scenarios such as multi-VCPU VM.

<br/>

<b>Namratha (014597258)</b> - I used the VM environment from Assignment 2 where on VMware Workstation I created an Ubuntu machine and built inner VM . I then made the changes on the cpuid.c and vmx.c and ran make, make modules, make modules_install, make install. After this, we collaborated together to complete the assignment going back and forth with each other on areas where we need to change the code, how to change the code and how to handle various scenarios such as multi-VCPU VM.

<br/>
<br/>

We both then modified the code for vmx.c and cpuid.c and test2.c.
<br/>
<br/>

<b>Describe in detail the steps you used to complete the assignment. Consider your reader to be someone skilled in software development but otherwise unfamiliar with the assignment. Good answers to this question will be recipes that someone can follow to reproduce your development steps.</b>

<br/>

- Create ubuntu box on external ssd of 1 TB. Call this box as Outer VM.<br/>
- Create ubuntu vm of 100 GB inside of Outer VM. Call this vm as Inner VM.<br/>
- Go to Outer VM.<br/>
- Fork linux repository.<br/>
- Clone forked linux repository in Outer VM using https://github.com/saumilnpatel17/linux.git<br/>
- Follow the following commands to build the linux kernel:<br/>
  - sudo apt install gcc make<br/>
  - sudo bash<br/>
  - apt-get install build-essential kernel-package fakeroot libncurses5-dev libssl-dev ccache bison flex libelf-dev<br/>
  - uname -a (It gives me kernel version 5.4.0-52-generic)<br/>
  - cp /boot/config-5.4.0.-52-generic ./.config<br/>
  - make oldconfig<br/>
  - make -j4<br/>
  - make modules -j4<br/>
  - make modules_install -j4<br/>
  - make install -j4<br/>
- After kernel build, reboot the computer and check kernel version. It's 5.9.0+<br/>
- Make modifications on vmx.c (vmx_handle_exit function to be modified, If the exit is valid and enabled increment the counter for that exit)<br/>
- Make modifications on cpuid.c (kvm_emulate_cpuid function to be modified, add a condition to check if eax=0x4ffffffe and check if th exit number is valid/disabled/invalid. If valid)<br/>
- Now build the kernel again using same make, make modules, make modules_install and make install sequence.<br/>
- Then remove kvm-intel and kvm kernel objects using -> sudo rmmod kvm-intel.ko and sudo rmmod kvm.ko command<br/>
- Now add new kvm-intel and kvm kernel objects from linux repo. Path is /arch/x86/kvm/<br/>
  - sudo insmod kvm.ko<br/>
  - sudo insmod kvm-intel.ko<br/>
- Reboot<br/>
-Run the test case. It should give the desired output.<br/>

<br/>

<b>Comment on the frequency of exits – does the number of exits increase at a stable rate? Or are there more exits performed during certain VM operations? Approximately how many exits does a full VM boot entail?</b>

<br/>
<br/>

<b>Of the exit types defined in the SDM, which are the most frequent? Least?</b>
<br />
Among the exit types defined in the SDM the following exits are some of the exits that occur more frequently than the others:
<br /><br />
0	Exception or non-maskable interrupt (NMI)<br />
1	External interrupt<br />
7	Interrupt window.<br />
10	CPUID<br />
12	HLT<br />
30	I/O instruction<br />
31	RDMSR<br />
32	WRMSR<br />
40	PAUSE<br />
<br />
Among the exit types defined in the SDM the following exits are some of the exits that occur less frequently than the others:<br />
6	Other SMI<br />
8	NMI window<br />
17	RSM<br />
26	VMXOFF<br />
45	Virtualized EOI<br />
51	RDTSCP<br />
58	INVPCID<br />
68	TPAUSE<br />

<br/>
<br/>

<h1>Output</h1><br/>

<b>Declare and export Atomic Variables in cpuid.c</b><br/>
![Alt text](ScreenShots/atomic_variables.png?raw=true "")<br/><br/>

<b>Changes to kvm_emulate_cpuid function in cpuid.c</b><br/>
![Alt text](ScreenShots/cpuid_leaf.png?raw=true "")<br/><br/>

<b>Use atomic variables in vmx_handle_exit.c</b><br/>
![Alt text](ScreenShots/vmx_atomic.png?raw=true "")<br/><br/>

<b>Declare and initialize start time in vm exit and increment exit counter</b><br/>
![Alt text](ScreenShots/vmx_changes.png?raw=true "")<br/><br/>

<b>Exit number 1 - Valid and Enabled Exit</b><br/>
![Alt text](ScreenShots/exit1.JPG?raw=true "")<br/><br/>

<b>Exit number 13 - Disabled Exit</b><br/>
![Alt text](ScreenShots/exit13.JPG?raw=true "")<br/><br/>

<b>Exit number 35 - Invalid Exit (Not listed in SDM)</b><br/>
![Alt text](ScreenShots/exit35.JPG?raw=true "")<br/><br/><br/>

<h1>All Exits from 0 to 68</h1><br/><br/>

![Alt text](ScreenShots/1.jpeg?raw=true "")<br/><br/><br/>

![Alt text](ScreenShots/2.jpeg?raw=true "")<br/><br/><br/>

![Alt text](ScreenShots/3.jpeg?raw=true "")<br/><br/><br/>

![Alt text](ScreenShots/4.jpeg?raw=true "")<br/><br/><br/>

![Alt text](ScreenShots/5.jpeg?raw=true "")<br/><br/><br/>

![Alt text](ScreenShots/6.jpeg?raw=true "")<br/><br/><br/>

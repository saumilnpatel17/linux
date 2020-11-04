
<h1>Questions-Answers</h1><br/>
<b>For each member in your team, provide 1 paragraph detailing what parts of the lab that member implemented / researched. (You may skip this question if you are doing the lab by yourself).</b><br/><br/>

<b>Saumil (013829270)</b> - I have used vm environment from 1st assignment that is I have created linux box on external ssd and created a linux vm inside that box. Then I have done research on how to build linux kernel. I had initially found difficulty as I mistakenly executed make install before make modules_install. So I corrected the make sequence which is 1> make 2> make modules 3> make modules_install 4> make install. For all make commands, I used -j4 to use 4 cpus as my box has 8 cores. After this, we both have completed the assignment pretty much together going back and forth with each other on areas where we need to change the code, how to change the code and how to handle various scenarios such as multi-VCPU VM.

- Researched on how atomic variables work in C
- How to share atomic variables between various modules of C
- How to increment atomic variable
- How to read time stamp counter using RDTSC()
- How to add values in atomic variable
- Made code changes in cpuid.c and vmx.c

<br/>

<b>Namratha (014597258)</b> -On VMware Workstation I created an Ubuntu machine with 200GB hard disk capacity. To build the linux kernel, I faced issues using the make command provided and changed the order to make, make modules, make modules_install, make install.I then researched and found information on changes to be made on vmx.c and cpuid.c and to create test2.c, involving creation and incrementing atomic variable for the counter and read timestamps. After this, we collaborated together to complete the assignment going back and forth with each other on areas where we need to change the code, how to change the code and how to handle various scenarios such as multi-VCPU VM.
<br/>
<br/>
<br/>


We both then modified the code for vmx.c and cpuid.c and test2.c.
<br/>
<br/>
<br/>
<b>Describe in detail the steps you used to complete the assignment. Consider your reader to be someone skilled in software development but otherwise unfamiliar with the assignment. Good answers to this question will be recipes that someone can follow to reproduce your development steps.</b><br/><br/><br/>

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
- Make modifications on vmx.c (vmx_handle_exit function to be modified, initiate the timer and increment the counter at the beginning of vmx_handle_exit. Before performing the return operation from the function calculate the difference of current time and inital time to get the total time taken<br/>
- Make modifications on cpuid.c (kvm_emulate_cpuid function to be modified, add a condition to check if eax=0x4fffffff and if so update the eax value with total number of exits and the ebx and ecx values with the top and bottom 32 bits of the total time taken processing exits<br/>
- Now build the kernel again using same make, make modules, make modules_install and make install sequence.<br/>
- Then remove kvm-intel and kvm kernel objects using -> sudo rmmod kvm-intel.ko and sudo rmmod kvm.ko command<br/>
- Now add new kvm-intel and kvm kernel objects from linux repo. Path is /arch/x86/kvm/<br/>
  - sudo insmod kvm.ko<br/>
  - sudo insmod kvm-intel.ko<br/>
- Reboot<br/>
-Run the test case. It should give the desired output.<br/>

<b>Comment on the frequency of exits – does the number of exits increase at a stable rate? Or are there more exits performed during certain VM operations? Approximately how many exits does a full VM boot entail?</b><br/>

By looking at the following screenshots, it appears that number exits does not increase at a stable rate. The number of exits is very high just after boot up. It is 0x80CE8 (Int: 527592) right after boot up and it increased with over a period of time but the rate at which number of exits occured slowed down but soon after performing some operations, number of exits again increased drastically. So no conclusion can be made for the rate at which exits will happen.
<br/><br/>

<b>Just After Boot Up</b><br/>
![Alt text](Screenshots/AfterBoot.png?raw=true "AfterBoot")<br/><br/>

<b>Few Minutes After Boot Up</b><br/>
![Alt text](Screenshots/FewMinsAfterBoot.png?raw=true "FewMinsAfterBoot")<br/><br/>

<b>Long Time After Boot Up</b><br/>
![Alt text](Screenshots/LongTimeAfterBoot.png?raw=true "LongTimeAfterBoot")<br/><br/>

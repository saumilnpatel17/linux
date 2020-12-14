<h1>Questions-Answers</h1><br/>
<b>For each member in your team, provide 1 paragraph detailing what parts of the lab that member implemented / researched. (You may skip this question if you are doing the lab by yourself).</b><br/><br/>

<b>Saumil (013829270)</b> - I have used vm environment from Assignment 2 where I had created Outer vm and Inner vm with ubuntu system installed on both of them. Then I also built the kernel using linux repo. Build steps: 1> make 2> make modules 3> make modules_install 4> make install. For all make commands, I used -j4 to use 4 cpus as my box has 8 cores. After this, we both have completed the assignment pretty much together going back and forth with each other on areas where we need to change the code, how to change the code and how to handle various scenarios such as multi-VCPU VM.

- Made code changes in cpuid.c and vmx.c
<br/>

<b>Namratha (014597258)</b> - 

<br/>
<br/>

We both then modified the code for vmx.c and cpuid.c and test2.c.
<br/>
<br/>

<b>Describe in detail the steps you used to complete the assignment. Consider your reader to be someone skilled in software development but otherwise unfamiliar with the assignment. Good answers to this question will be recipes that someone can follow to reproduce your development steps.</b>

<br/>
<br/>

<b>Comment on the frequency of exits – does the number of exits increase at a stable rate? Or are there more exits performed during certain VM operations? Approximately how many exits does a full VM boot entail?</b>

<br/>
<br/>

<b>Of the exit types defined in the SDM, which are the most frequent? Least?</b>

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

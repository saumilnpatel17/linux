
<h1>Questions-Answers</h1><br/>
<b>For each member in your team, provide 1 paragraph detailing what parts of the lab that member implemented / researched. (You may skip this question if you are doing the lab by yourself).</b><br/><br/>

<b>Saumil (013829270)</b> - I have used vm environment from 1st assignment that is I have created linux box on external ssd and created a linux vm inside that box. Then I have done research on how to build linux kernel. I had initially found difficulty as I mistakenly executed make install before make modules_install. So I corrected the make sequence which is 1> make 2> make modules 3> make modules_install 4> make install. For all make commands, I used -j4 to use 4 cpus as my box has 8 cores. After this, we both have completed the assignment pretty much together going back and forth with each other on areas where we need to change the code, how to change the code and how to handle various scenarios such as multi-VCPU VM.

- Researched on how atomic variables work in C
- How to share atomic variables between various modules of C
- How to increament atomic variable
- How to read time stamp counter using RDTSC()
- How to add values in atomic variable
- Made code changes in cpuid.c and vmx.c

<br/>

<b>Namratha (014597258)</b> - On VMware Workstation I created an Ubuntu machine with 200GB hard disk capacity and built another Linux VM within this Ubuntu create the setup for assignment 2. I then researched and found information on changes to be made on vmx.c and cpuid.c and to create test2.c .
<br/>
<br/>


We both then modified the code for vmx.c and cpuid.c and test2.c.
<br/>
<br/>
<br/>
<b>Describe in detail the steps you used to complete the assignment. Consider your reader to be someone skilled in software development but otherwise unfamiliar with the assignment. Good answers to this question will be recipes that someone can follow to reproduce your development steps.</b>

<br/>
<br/>
<br/>
<b>Comment on the frequency of exits – does the number of exits increase at a stable rate? Or are there more exits performed during certain VM operations? Approximately how many exits does a full VM boot entail?</b>

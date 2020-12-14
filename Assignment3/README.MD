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

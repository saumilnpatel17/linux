<h1>Questions-Answers</h1><br/>
<b>For each member in your team, provide 1 paragraph detailing what parts of the lab that member implemented / researched. (You may skip this question if you are doing the lab by yourself).</b><br/><br/>

<b>Saumil (013829270)</b> - 

<br/>

<b>Namratha (014597258)</b> - 

<br/>
<br/>

<b>Include a sample of your print of exit count output from dmesg from “with ept” and “without ept”.</b>

<br/>
<br/>

<b>What did you learn from the count of exits? Was the count what you expected? If not, why not?</b>

<br/>
<br/>

It is clearly seen from the booting process that with ept=0, it took way more time to boot up the vm than without ept=0. This is mainly because by using ept=0, we are forcing vm to use shadow paging which clearly made more exits (way more exits) than without ept=0 which lets vm to use nested paging. After booting up, it is clearly seen in the above screenshots that with ept=0, the number of exits were very high due to control registers access exits and page fault exits. Therefore, it took too much time in processing VM exits with ept=0 than without ept=0.

The count was very much expected because with ept=0, we are forcing vm to use shadow paging which causes more exits logically as well as mentioned in intel sdm due to control registes access exits and page fault exits.

<b>What changed between the two runs (ept vs no-ept)?</b>

Between two runs (ept vs no-ept):
- With ept, vm was forced to used shadow paging.
- With shadow paging as screenshots provided in the ouput section, it is clearly seen that number of exits in shadow paging has increaded dramatically.
- It is also clear that Exception or Non-maskable interrupt number also increased with ept=0.
- Also, External interrupt exits were also increased with ept.
- Moreover, INVLPG exits were also dramatically increased which flushes TLB entries which explains that more CR3 access caused more TLB flushes.
- With no-ept, there were no exit 58 which is INVPCID. On the other hand with ept, there was high number of INVPCID exits.

Therefore, it is clearly seen that exits with shadow paging (with ept=0) was very high than no ept.
Moreover, the time spent in hypervisor was also very high with ept compared to no-ept because there were more exits which makes to spent more time in hypervisor.
<br/>
<br/>

<h1>Output</h1><br/><br/>

<h3>Using Nested Paging, Before doing sudo insmod kvm.intel.ko ept=0</h3><br/><br/>

![Alt text](ScreenShots/NestedPaging1.jpeg?raw=true "")<br/><br/>

![Alt text](ScreenShots/NestedPaging2.jpeg?raw=true "")<br/><br/>

![Alt text](ScreenShots/NestedPaging3.jpeg?raw=true "")<br/><br/>

![Alt text](ScreenShots/NestedPaging4.jpeg?raw=true "")<br/><br/>

![Alt text](ScreenShots/NestedPaging5.jpeg?raw=true "")<br/><br/>

![Alt text](ScreenShots/NestedPaging6.jpeg?raw=true "")<br/><br/>

<h3>Using Shadow Paging, After doing sudo insmod kvm-intel.ko ept=0</h3><br/><br/>

![Alt text](ScreenShots/1.png?raw=true "")<br/><br/>

![Alt text](ScreenShots/2.png?raw=true "")<br/><br/>

![Alt text](ScreenShots/3.png?raw=true "")<br/><br/>

![Alt text](ScreenShots/4.png?raw=true "")<br/><br/>

![Alt text](ScreenShots/5.png?raw=true "")<br/><br/>

![Alt text](ScreenShots/6.png?raw=true "")<br/><br/>

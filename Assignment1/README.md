<h1>Questions-Answers</h1><br/>
<b>For each member in your team, provide 1 paragraph detailing what parts of the lab that member implemented / researched. (You may skip this question if you are doing the lab by yourself).</b><br/><br/>

<b>Saumil (013829270)</b> - I researched on how to setup the environment to complete the assignment. First, I chose to create an outer vm on Google cloud but since assignment requirement is to create an outer vm of 160 GB to 200 GB, it is too expensive to such vm on Google cloud. Then I chose to move forward with setting up the environment on my laptop but I found it complicated to install vmware workstation on my laptop and then create outer vm on it and then create inner vm inside it. Finally, I moved forward with installing linux on external SSD. I installed linux on external SSD of 1 TB and created inner vm of 100 GB with linux installed on it. Now that environment is up and running, I successfully ran the demo for assignment 1 which was shown in video. My teammate did the research on tables of different control fields in SDM. Then we both prepared the code and implemented it in kernel module. Then we have compiled it and inserted the module in kernel and stored the result.


<b>Describe in detail the steps you used to complete the assignment. Consider your reader to be someone skilled in software development but otherwise unfamiliar with the assignment. Good answers to this question will be recipes that someone can follow to reproduce your development steps.</b>

Step 1: Get USB of 64 GB.<br/>
Step 2: Download ubuntu desktop from https://ubuntu.com/download/desktop.<br/>
Step 3: Create bootable USB from Ubuntu Desktop ISO image from Step 2. https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview<br/>
Step 4: Get external SSD of 1 TB.<br/>
Step 5: Install ubuntu desktop from bootable usb to external SSD. https://www.youtube.com/watch?v=YIhYitXwJfE<br/>
https://askubuntu.com/questions/1131051/install-ubuntu-on-external-ssd-without-dual-boot<br/>
Step 6: Ubuntu desktop installed in Step 4 will serve the purpose of outer vm.<br/>
Step 7: Once logged in into newly installed ubuntu desktop, create a vm of 100 GB in it with linux installed on it. https://medium.com/@DrewViles/using-libvirtd-kvm-qemu-to-create-vms-2eaafa70a592<br/>
Step 8: VM in Step 7 will serve the purpose of inner vm.<br/>
Step 9: Now login into outer vm.<br/>
Step 10: Download cmpe283-1.c and Makefile from Canvas.<br/>
Step 11: Compile cmpe283-1.c file using make command. If make command does not run successfully, make sure it is installed. In order to do that, run following commands:<br/>
Sudo apt install gcc make<br/>
Step 12: Once compiled successfully, it will create kernel module file cmpe283-1.ko.<br/>
Step 13: Insert kernel module file in Kernel by using following command:<br/>
Sudo insmod cmpe283-1.ko<br/>
Step 14: Run “dmesg” command to see the output. Command “dmesg” prints the message buffer of Kernel.<br/>
Step 15: Now run “sudo rmmod cmpe283-1.ko” to remove kernel module.<br/>
Step 16: Make changes to the cmpe283-1.c to fulfill assignment requirements.<br/>
Step 17: Run “make” command to compile which will generate cmpe283-1.ko file<br/>
Step 18: Run “sudo insmod cmpe283-1.ko” command to insert kernel module into kernel.<br/>
Step 19: Run “dmesg” command to see output for all controls’ capabilities.<br/>
<br/><br/><br/>
<h1>Output</h1><br/>

<b>Pinbased</b><br/>
![Alt text](Screenshots/Pinbased.png?raw=true "Pinbased")<br/><br/>

<b>Procbased</b><br/>
![Alt text](Screenshots/Procbased.png?raw=true "Procbased")<br/><br/>

<b>Secondary Procbased</b><br/>
![Alt text](Screenshots/SecondaryProcbased.png?raw=true "Secondary Procbased")<br/><br/>

<b>Exitbased</b><br/>
![Alt text](Screenshots/Exitbased.png?raw=true "Exitbased")<br/><br/>

<b>Entrybased</b><br/>
![Alt text](Screenshots/Entrybased.png?raw=true "Entrybased")<br/>




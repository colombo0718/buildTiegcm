# Build up TIEGCM system  
### `I.` Install Ubuntu 
**make USB bootable drive in Windows**  
download [Ubuntu 64-bit] IOS file   
`http://www.ubuntu.com/download/desktop`  
download and install  [win32DiscImager]  
`http://sourceforge.net/projects/win32diskimager/`  
write IOS file into USB by win32DiscImager,   
make as bootable driver.  

**Boot computer with USB**   
**and Start the installation process** 

- Step1. welcome [Install Ubuntu]   
- Step2. Prepare to Install Ubuntu [Continue]  
- Step3. Install type [somthing else]  
`1TB--500G-> use as 'swap area'`  
`...\-500G-> use as 'Ext4', mount point:'/'`  
`2TB --> use as 'Ext4', mount point:'/home'`   
- Step4. where are you ? [Taipei]
- Step5. Keyboard layout [Continue]
- Step6.   
`Your name : suproject01`    
`Your computer's name : project01`  
`Pick a user name : suproject01`  
`Choose a passward : ********`

### `II.` Install PGI Fortran comiler   
**Download and Install**  
sing up or sign in PGI official website  
`http://www.pgroup.com`  
click [download] and select as below:  
>`Product : PGI Fortran server`  
>`Target : 64-bit only`  
>`Platform : Linux`  
>`Package : full`  

files are download in directory `/home/$USer/Downloads`  
decompresse the files in graphic interface,  
enter the path of decompressed file by terminal  
and input command `$ sudo ./instll` to install  
press 'q' to skip the discription file  
select single system install  
and install into default directory (/opt/pgi)  
Install every package, especially MPICH.

**取得 linence.dat**


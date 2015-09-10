# 建立 TIEGCM 系統 SOP  
### 一、安裝 Ubuntu 作業系統 
**在Windows電腦中製作USB啟動碟**  
下載 Ubuntu 64-bit 安裝檔   
`http://www.ubuntu.com/download/desktop`  
下載並安裝 win32DiscImager  
`http://sourceforge.net/projects/win32diskimager/`  
以 win32DiscImager 將 Ubuntu 安裝檔寫入USB,   
做成啟動碟。

**以USB開機進入安裝流程**   

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

### 二、安裝 PGI Fortran comiler   
**下載與安裝**  
登入或申請PGI官方網站帳號   
`http://www.pgroup.com`  
點選 [download] 進入下載選單:  
> `Product : PGI Fortran server`  
> `Target : 64-bit only`  
> `Platform : Linux`  
> `Package : full`  

Ubuntu中 網路上下載的檔案自動放入路徑  
`/home/$USer/Downloads`  
於視窗環境將檔案解壓縮後，以terminal進入安裝檔  
輸入指令`$ sudo ./instll` 即進行安裝   
遇長篇說明文件可按'q'跳過   
選擇 single system install  
Install directory: /opt/pgi (預設)  
所有周邊套件皆按'y'安裝，mpich尤為重要。

**取得 lincense.dat**  
進入PGI官網，點擊 Download 的 Free Trial Software 子選項，  
在文章中點選 generate 15 day PGI trial license key，  
輸入網卡卡號後方可取得 licnese.dat 。  
> 查看網卡卡號，於terminal中輸入`$ ifconfig`，  
>`HWaddr`後的字串即為網卡卡號

### 三、安裝netcdf  
從網路上下載netcdf-4.1.1版(版本限定)  
安裝前須先完成以下指令：  
`$ sudo apt-get update`  
`$ sudo apt-get upgrade`  
`$　sudo apt-get install g++`  
於視窗環境將檔案解壓縮後，以terminal進入安裝檔，  
輸入以下指令進行安裝:  
`$ ./configure`  
`$ make check`  
`$ sudo make install`  
預設安裝路徑為`/usr/local/`

### 四、設定環境與安裝TIEGCM
**安裝周邊套件**  
輸入下列指令以預先安裝周邊套件：  
`$ sudo apt-get install csh`  
`$ sudo apt-get install vim`  
`$ sudo apt-get install libhdf5-serial-dev`  
`$ sudo apt-get install svnversion`
  
**設定$PATH路徑變數**  
以管理者權限編輯`/etc/bash.bashrc`  
`$ sudo vi bash.bashrc`  
於檔案最末端加入以下設定：  
`PATH=/opt/pgi/linux86-64/15.7/bin`  
將路徑指向 pgi fortran 執行檔，  
變數名稱 PATH 必須為大寫。

**安裝TIEGCM**  
於TIEGCM官網下載主程式，  
視窗環境解壓縮後 terminal 進入安裝檔  
修改下列兩份檔案:  
1.修改tiegcm-linux.job
> `$ vi script/tiegcm-linux.job`   
> `set modeldir=安裝檔路徑`  
> `set make=Make.pgi_hao64` 或 `=Make.intel_hao64`  
> 將所有'gmake'改為'make'

2.修改Make.pgi_hao64  
> `$ vi script/Make.pgi_hao64`  
> `F90=pgi compiler 路徑/pgf90`  
> `MPIF90=pgi MPI 路徑/mpif90`  
> `MPIRUN=pgi MPI 路徑/mpirun`  
> `LIBS=移除 -lsz`  
> `LIB_NETCDF=netcdf路徑/lib`  
> `INC_NETCDF=netcdf路徑/include`  

修改完畢執行 tiegcm-linux.job   
`$ ./tiegcm-linux.job`  
到此TIEGCM安裝完成!!!

### 五、安裝繪圖軟體
**下載並安裝 octave**  
此軟體為免費版 matlab，語法完全相同  
`$ sudo apt-get install octave`  
`$ sudo apt-get install octave-octcdf`

**光碟安裝IDL**  
進入光碟路徑 `/media/$USER/光碟名稱`  
輸入指令 `$ sudo ./install-unix.sh` 即開始安裝  
安裝路徑為 `/usr/local/exelis`  

註：電腦室給的license設定變數`LM_LICENSE_PILE`  
與 pgi fortran compiler 衝突，  
欲重新 complie TIEGCM 時須注意。

### 六、系統測試  




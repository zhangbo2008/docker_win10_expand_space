# docker_win10_expand_space


2020-07-17,9点43
docker reset to default: 点开setting后点右上角的虫子.里面有reset.



2020-07-17,10点25 
	添加docker 磁盘空间的方法: 亲测完美.但是一定要要注意,#6里面的步奏,其实需要修改很多个
	VhdSize需要都改成240即可.
	
	https://forums.docker.com/t/manage-host-disk-volume-size/37438/2

	#1) Stop Docker
	#2) Start Powershell ISE as Administrator
	#3) Using the Powershell command prompt, make a backup of the file to be edited: cp C:\Program Files\Docker\Docker\Resources\MobyLinux.ps1 C:\Program Files\Docker\Docker\Resources\MobyLinux.bak
	#4) In Powershell ISE, open the file C:\Program Files\Docker\Docker\Resources\MobyLinux.ps1
	#5) Find the entry $global:VhdSize (Line 86 in version 17.06.1-ce-win24 (13025))
	#6) Change the first number in this line $global:VhdSize = 60*1024*1024*1024 # 60GB from 60 to the size you want in GB. For example, to create a 120GB volume, change the line to $global:VhdSize = 120*1024*1024*1024 # 120GB
	#7) In Powershell ISE, click File… Save to save the updated file.
	#8) In Powershell ISE, click File… Save As… and save a backup of the modified file. This file can be used to restore the customization after a re-install. To be safe, the file should not be used to re-apply the customization after an upgrade, since the file could have been changed as part of the upgrade. After upgrades, follow the steps above to re-apply customizations as necessary.
	#9) Restart Docker
	#10) From the Docker UI, select Reset… Reset to Factory Defaults. This action will rebuild your MobyLinuxVM with the new custom volume size. WARNING: this step wipes out all Images and Containers stored on the MobyLinuxVM!!!


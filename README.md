# zfs-autosna  

ZFS auto snapshot service. Designed to run out of cron  

Will automatically create and manage snapshots based on the following custom zfs properties  

	- autosnap_yearl  
	- autosnap_monthl  
	- autosnap_weekl  
	- autosnap_dail  
	- autosnap_hourl  

If set to 1, then snapshots will be created, e.g.  
NAME                PROPERTY              VALUE                  SOURC  
[...  
bootpool/testzfs    svm:autosnap_monthly  1                      loca  
bootpool/testzfs    svm:autosnap_weekly   1                      loca  
bootpool/testzfs    svm:autosnap_yearly   1                      loca  
bootpool/testzfs    svm:autosnap_hourly   1                      loca  
bootpool/testzfs    svm:autosnap_daily    1                      loca  


#Example crontab entries  
0 0 1 1 * /usr/local/bin/zfs_autosnap -t yearl  
0 0 1 * * /usr/local/bin/zfs_autosnap -t monthl  
0 0 * * 0 /usr/local/bin/zfs_autosnap -t weekl  
0 0 * * * /usr/local/bin/zfs_autosnap -t dail  
0 * * * * /usr/local/bin/zfs_autosnap -t hourl  


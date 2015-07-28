# zfs-autosnap  

ZFS auto snapshot service. Designed to run out of cron.  

Will automatically create and manage snapshots based on the following custom zfs properties:  

	- autosnap_yearly  
	- autosnap_monthly  
	- autosnap_weekly  
	- autosnap_daily  
	- autosnap_hourly  

If set to 1, then snapshots will be created, e.g.:  
````
NAME                PROPERTY              VALUE                  SOURCE  
[...]  
bootpool/testzfs    svm:autosnap_monthly  1                      local  
bootpool/testzfs    svm:autosnap_weekly   1                      local  
bootpool/testzfs    svm:autosnap_yearly   1                      local  
bootpool/testzfs    svm:autosnap_hourly   1                      local  
bootpool/testzfs    svm:autosnap_daily    1                      local  
````

###Example crontab entries:  
````
0 0 1 1 * /usr/local/bin/zfs_autosnap -t yearly  
0 0 1 * * /usr/local/bin/zfs_autosnap -t monthly  
0 0 * * 0 /usr/local/bin/zfs_autosnap -t weekly  
0 0 * * * /usr/local/bin/zfs_autosnap -t daily  
0 * * * * /usr/local/bin/zfs_autosnap -t hourly  
````

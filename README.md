We are experiencing a performance issue with the OPAC search functionality on our server. Despite enabling memcached and Apache2 cache services, the OPAC search is extremely slow and consumes excessive CPU resources, leading to server downtime.

Here are the details of our server:

- Operating System: Ubuntu 20.04 LTS
- CPU: 4 cores
- RAM: 8GB
- Storage: 200GB SSD

When monitoring the server using the 'top' command, we observe that only a few OPAC search requests are being processed. However, these requests are utilizing nearly all of the available CPU resources, leaving no CPU capacity for other tasks and causing the server to go down.

We have already implemented memcached and Apache2 cache services to optimize performance, but the OPAC searches are still not functioning as expected.

It's worth mentioning that we did not utilize the 'koha-common' command for the Koha installation and setup. Instead, we downloaded the Koha tar file and performed the installation using the 'perl Makefile.PL' command.

We kindly request your assistance in improving the speed and performance of our server. Any suggestions or guidance on optimizing the OPAC search functionality would be greatly appreciated. Thank you in advance for your support.

`top command output`

```
top - 15:47:28 up 560 days, 15:00,  1 user,  load average: 13.45, 12.64, 10.70
Tasks: 183 total,   6 running, 176 sleeping,   0 stopped,   1 zombie
%Cpu0  : 91.3 us,  8.4 sy,  0.0 ni,  0.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.3 st
%Cpu1  : 90.3 us,  9.7 sy,  0.0 ni,  0.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu2  : 92.7 us,  7.0 sy,  0.0 ni,  0.3 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu3  : 91.3 us,  8.7 sy,  0.0 ni,  0.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :   7961.6 total,   3044.0 free,   3027.7 used,   1889.9 buff/cache
MiB Swap:      0.0 total,      0.0 free,      0.0 used.   4637.8 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                        
2989144 www-data  20   0  263820 206912  21532 R  48.5   2.5   0:06.61 opac-search.pl                                                                 
2989220 www-data  20   0  252356 195340  21448 R  46.5   2.4   0:01.76 opac-search.pl                                                                 
2989219 www-data  20   0  260696 203384  21108 R  41.9   2.5   0:01.71 opac-detail.pl                                                                 
2989206 www-data  20   0  263796 206628  21420 R  40.9   2.5   0:02.35 opac-search.pl                                                                 
2989213 www-data  20   0  252672 195876  21576 R  35.2   2.4   0:01.92 opac-search.pl                                                                 
2989232 kohauser  20   0   62148  18488   8584 S  16.6   0.2   0:00.50 zebrasrv                                                                       
2884128 mysql     20   0 6038592   1.5g  13456 S  12.6  19.0  39:05.87 mysqld                                                                         
2989231 kohauser  20   0   62156  18424   8392 S  10.3   0.2   0:00.31 zebrasrv                                                                       
2989233 kohauser  20   0   61936  18412   8584 S   2.7   0.2   0:00.08 zebrasrv                                                                       
2988271 www-data  20   0  211308  13852   6936 S   0.7   0.2   0:00.08 apache2                                                                        
     11 root      20   0       0      0      0 I   0.3   0.0   1292:55 rcu_sched                                                                      
    218 root       0 -20       0      0      0 I   0.3   0.0 181:48.18 kworker/3:1H-kblockd                                                           
    602 nydus     20   0  931648  29536      0 S   0.3   0.4   1975:12 nydus-ex-api                                                                   
2800275 root      20   0  254720 177396   5656 S   0.3   2.2   0:06.23 perl                                                                           
2981488 satpura   20   0   13952   6108   4636 S   0.3   0.1   0:00.37 sshd                                                                           
2988239 www-data  20   0  211308  13740   6800 S   0.3   0.2   0:00.09 apache2                                                                        
2988918 www-data  20   0  211308  13732   6800 S   0.3   0.2   0:00.03 apache2                                                                        
2989146 root      20   0   11104   3968   3196 R   0.3   0.0   0:00.03 top                                                                            
      1 root      20   0  172288  11036   5340 S   0.0   0.1  80:08.73 systemd                                                                        
      2 root      20   0       0      0      0 S   0.0   0.0   0:09.37 kthreadd                                                                       
      3 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_gp                                                                         
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_par_gp                                                                     
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/0:0H-kblockd                                                           
      9 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 mm_percpu_wq                                                                   
     10 root      20   0       0      0      0 S   0.0   0.0  30:58.37 ksoftirqd/0                                                                    
     12 root      rt   0       0      0      0 S   0.0   0.0   7:17.24 migration/0                                                                    
     13 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/0                                                                  
     14 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/0                                                                        
     15 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/1                                                                        
 
```

## Please let me know if you require any additional information or if there are specific details you would like me to provide.

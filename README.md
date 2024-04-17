
# Welcome to **Linux**!
Описание на русском [тут](./README_RUS.md)

1. [Part 1. OS installation](#part-1-installing-the-osn)
2. [Part 2. Creating a user](#part-2-creating-a-user)
3. [Part 3. OS Network Setup](#part-3-configuring-the-os-network)
4. [Part 4. OS Update](#part-4-os-update)
5. [Part 5. Using the sudo command](#part-5-using-the-sudo-command)
6. [Part 6. Installing and configuring the Time Service](#part-6-installing-and-configuring-the-time-service)
7. [Part 7. Installing and using text editors](#part-7-installing-and-using-text-editors-vim-nano-mcedit)
8. [Part 8. Installation and basic configuration of the SSHD service](#part-8-installation-and-basic-configuration-of-the-sshd-service)
9. [Part 9. Installing and using top, htop utilities](#part-9-installing-and-using-the-top-htop-utilities)
10. [Part 10. Using the fdisk utility](#part-10-using-the-fdisk-utility)
11. [Part 11. Using the df utility](#part-11-using-the-df-utility)
12. [Part 12. Using the du utility](#part-12-using-the-du-utility)
13. [Part 13. Installing and using the ncdu utility](#part-13-installing-and-using-the-ncdu-utility)
14. [Part 14. Working with system logs](#part-14-working-with-system-logs)
15. [Part 15. Using the CRON Task Scheduler](#part-15-using-the-task-scheduler-cron)


##  Part 1. Installing the OS
* Installing Ubuntu 20.04 Server LTS.
* Output of the Ubuntu version using the `cat /etc/issue` command : 

![pic_part1_1](./misc/images/1_1.png)

## Part 2. Creating a user
* Create a new user `admin`:

![pic_part2_1](./misc/images/2_1.png)

* Adding the user `admin` to the 'adm` group

* We output users with the command `cat /etc/passwd`, look at the presence of the user `admin` there:

![pic_part2_2](./misc/images/2_2.png)

## Part 3. Configuring the OS network
* `lo` is an interface that allows programs to access through a local host or send data to themselves. This is useful for testing and setting up network functions.
* `DHCP` is a network protocol for dynamically configuring network parameters. It was created so that you do not have to manually set IP, DNS, and so on for each device.
* First, go to the *** superuser*** so as not to type `sudo` every time and use it further in all tasks. 
* Use `ip route` to get the gateway address, set static parameters in the file `/etc/netplan/*.yaml`, apply the changes `netplan apply`, reboot the machine `reboot`, check that the specified parameters are preserved.
* Ping 1.1.1.1 and ya.ru: 

![pic_part3_1](./misc/images/3_1.png)
![pic_part3_2](./misc/images/3_2.png)

## Part 4. OS Update
* Check for `apt update' updates, install `apt upgrade`: 

![pic_part4_1](./misc/images/4_1.png)

## Part 5. Using the **sudo command**
* `sudo` is used to execute commands on behalf of the superuser. The superuser has full control over the system.   
* Add the user `admin` to the `sudo' group and switch to it, change the hostname. Result:

![pic_part5_1](./misc/images/5_1.png)

## Part 6. Installing and configuring the Time service
* If auto-synchronization of time is not enabled, turn it on. Result: 

![pic_part6_1](./misc/images/6_1.png)

## Part 7. Installing and using text editors VIM, NANO, MCEDIT
* VIM, to exit with saving :wq

![pic_part7_1](./misc/images/7_1.png)
* NANO, to exit with saving `Ctrl + O`

![pic_part7_2](./misc/images/7_2.png)
* MCEDIT, to exit with saving `Esc + 0` , `Y`

![pic_part7_3](./misc/images/7_3.png)


* VIM, to exit without saving `:q!`

![pic_part7_4](./misc/images/7_4.png)
* NANO, to exit without saving `Ctrl + X` , `N`

![pic_part7_5](./misc/images/7_5.png)
* MCEDIT, to exit without saving `Esc + 0` , `N`

![pic_part7_6](./misc/images/7_6.png)


* VIM, search for `/jenniffr` and replace `:s/jenniffr/21 School 21/g`

![pic_part7_7](./misc/images/7_7.png)
![pic_part7_8](./misc/images/7_8.png)

* NANO, search for `Ctrl + W` and replace `Ctrl +\`

![pic_part7_9](./misc/images/7_9.png)
![pic_part7_10](./misc/images/7_10.png)

* MCEDIT, search for `Esc + 7` and replace `Esc + 4`

![pic_part7_11](./misc/images/7_11.png)
![pic_part7_12](./misc/images/7_12.png)


## Part 8. Installation and basic configuration of the SSHD service  
* Install ssh, add it to autorun, look at running processes using `ps -ef` 
    - ps: running processes
- -e: processes of all users
- -f: complete information about each process

![pic_part8_1](./misc/images/8_1.png)

* Using `netstat -tan`
    - `netstat` - disables network connections
- `-t` - TCP connections only
- `-a` - display all connections
    - `-n` - display addresses and addresses in numerical representation, without converting to names

![pic_part8_2](./misc/images/8_2.png)

* Command output:
- `Proto` - Connection protocol.
    - `Recv-Q` - The number of bytes waiting to be read from the socket.
    - `Send-Q` - The number of bytes waiting to be sent over the socket.
    - `Local Address' - The local IP address and port.
    - `Foreign Address' - Local IP address and port.
    - `State' - The state of the connection.
    - The address `0.0.0.0` means "all addresses on this device".

## Part 9. Installing and using the **top**, **htop utilities**
* Output `top`:
- uptime = 46 min
- number of authorized users = 1 
  - total system load = 0.00
- total number of processes = 95
  - CPU usage = 0.00
- memory usage = 146.9
- pid of the process taking up the most memory = 657
- pid of the process taking up the most CPU time = 1559

* 'htop` screenshots: 

  - sorted by PID, PERCENT_CPU, PERCENT_MEM, TIME

![pic_part9_1](./misc/images/9_1.png)
![pic_part9_2](./misc/images/9_2.png)
![pic_part9_3](./misc/images/9_3.png)
![pic_part9_4](./misc/images/9_4.png)

  - filtered for the sshd process

![pic_part9_5](./misc/images/9_5.png)
- with the syslog process found using the search 

![pic_part9_6](./misc/images/9_6.png)
- with added output of hostname, clock and uptime  

![pic_part9_7](./misc/images/9_7.png)

## Part 10. Using the fdisk utility
* Using the `fdisk -l` command, we will find out: 
    - Disk name = /dev/sda
- Size = 10GiB
    - SECTORS = 20971520

![pic_part10_1](./misc/images/10_1.png)

## Part 11. Using the df utility
* Using the `df` command, we find out the data about the root partition (measured in kilobytes (K))
- partition size = 8408452
  - the size of the OCCUPIED SPACE = 2594036
  - free space size = 5365700
- percentage of usage = 33% 
* Using the `df -Th` command, we find out the data about the root partition (measured in gigabytes (G))
- partition size = 8.1
- occupied space size = 2.5
- free space size = 5.2
- percentage of usage = 33%
- file system type = ext4"

![pic_part11_1](./misc/images/11_1.png)
  
## Part 12. Using the du utility
* Output of `du` commands:

![pic_part12_1](./misc/images/12_1.png)
* Output the contents of `/var/log/*`

![pic_part12_2](./misc/images/12_2.png)


## Part 13. Installing and using the ncdu utility
* Output folder sizes using `ncdu`
- `/home`

![pic_part13_1](./misc/images/13_1.png)
- `/var`

![pic_part13_1](./misc/images/13_2.png)
- `/var/log`

![pic_part13_1](./misc/images/13_3.png)
## Part 14. Working with system logs
* Last login = Jan 25 07:04 , user = jenniffr, login method = tty1

* Restart SSHd: 

![pic_part14_1](./misc/images/14_1.png)


## Part 15. Using the Task Scheduler **CRON**

* Add uptime to the task list every 2 minutes. Log output + cron task list: 

![pic_part15_1](./misc/images/15_1.png)

* Deleting all tasks from cron: 

![pic_part15_2](./misc/images/15_2.png)

If you're reading this, know this: you're doing great)


----------------------------------------------
***Thank you for your time.***
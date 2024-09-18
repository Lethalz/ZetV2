2409171936
	Status: #Exam 
		Tags: [[linux]] [[RHCSA]]

# RHCSA Objectives

# **RHCSA Exam Topics Summary**

| Topic Number | Topic                                   | Subtopic                                                                                                      | Resource | Lab | Level 1-3 | Notes |     |
| ------------ | --------------------------------------- | ------------------------------------------------------------------------------------------------------------- | -------- | --- | --------- | ----- | --- |
| 1.1          | Understand and Use Essential Tools      | Access a shell prompt and issue commands with correct syntax                                                  |          |     |           |       |     |
| 1.1          | Understand and Use Essential Tools      | Use input-output redirection (`>`, `>>`, `, `2>`, etc.)`                                                      |          |     |           |       |     |
| 1.1          | Understand and Use Essential Tools      | Use `grep` and regular expressions to analyze text                                                            |          |     |           |       |     |
| 1.1          | Understand and Use Essential Tools      | Access remote systems using SSH                                                                               |          |     |           |       |     |
| 1.1          | Understand and Use Essential Tools      | Log in and switch users in multiuser targets                                                                  |          |     |           |       |     |
| 1.1          | Understand and Use Essential Tools      | Archive, compress, unpack, and uncompress files using `tar`, `gzip`, and `bzip2`                              |          |     |           |       |     |
| 1.1          | Understand and Use Essential Tools      | Create and edit text files                                                                                    |          |     |           |       |     |
| 1.1          | Understand and Use Essential Tools      | Create, delete, copy, and move files and directories                                                          |          |     |           |       |     |
| 1.1          | Understand and Use Essential Tools      | Create hard and soft links                                                                                    |          |     |           |       |     |
| 1.1          | Understand and Use Essential Tools      | List, set, and change standard `ugo/rwx` permissions                                                          |          |     |           |       |     |
| 1.1          | Understand and Use Essential Tools      | Locate, read, and use system documentation including `man`, `info`, and files in `/usr/share/doc`             |          |     |           |       |     |
| 1.2          | Create Simple Shell Scripts             | Conditionally execute code (use of `if`, `test`, `[]`, etc.)                                                  |          |     |           |       |     |
| 1.2          | Create Simple Shell Scripts             | Use looping constructs (`for`, etc.) to process file and command line input                                   |          |     |           |       |     |
| 1.2          | Create Simple Shell Scripts             | Process script inputs (`$1`, `$2`, etc.)                                                                      |          |     |           |       |     |
| 1.2          | Create Simple Shell Scripts             | Process output of shell commands within a script                                                              |          |     |           |       |     |
| 1.3          | Operate Running Systems                 | Boot, reboot, and shut down a system normally                                                                 |          |     |           |       |     |
| 1.3          | Operate Running Systems                 | Boot systems into different targets manually                                                                  |          |     |           |       |     |
| 1.3          | Operate Running Systems                 | Interrupt the boot process in order to gain access to a system                                                |          |     |           |       |     |
| 1.3          | Operate Running Systems                 | Identify CPU/memory intensive processes and kill processes                                                    |          |     |           |       |     |
| 1.3          | Operate Running Systems                 | Adjust process scheduling                                                                                     |          |     |           |       |     |
| 1.3          | Operate Running Systems                 | Manage tuning profiles                                                                                        |          |     |           |       |     |
| 1.3          | Operate Running Systems                 | Locate and interpret system log files and journals                                                            |          |     |           |       |     |
| 1.3          | Operate Running Systems                 | Preserve system journals                                                                                      |          |     |           |       |     |
| 1.3          | Operate Running Systems                 | Start, stop, and check the status of network services                                                         |          |     |           |       |     |
| 1.3          | Operate Running Systems                 | Securely transfer files between systems                                                                       |          |     |           |       |     |
| 1.4          | Configure Local Storage                 | List, create, and delete partitions on MBR and GPT disks                                                      |          |     |           |       |     |
| 1.4          | Configure Local Storage                 | Create and remove physical volumes                                                                            |          |     |           |       |     |
| 1.4          | Configure Local Storage                 | Assign physical volumes to volume groups                                                                      |          |     |           |       |     |
| 1.4          | Configure Local Storage                 | Create and delete logical volumes                                                                             |          |     |           |       |     |
| 1.4          | Configure Local Storage                 | Configure systems to mount file systems at boot by universally unique ID (UUID) or label                      |          |     |           |       |     |
| 1.4          | Configure Local Storage                 | Add new partitions and logical volumes, and swap to a system non-destructively                                |          |     |           |       |     |
| 1.5          | Create and Configure File Systems       | Create, mount, unmount, and use `vfat`, `ext4`, and `xfs` file systems                                        |          |     |           |       |     |
| 1.5          | Create and Configure File Systems       | Mount and unmount network file systems using NFS                                                              |          |     |           |       |     |
| 1.5          | Create and Configure File Systems       | Configure `autofs`                                                                                            |          |     |           |       |     |
| 1.5          | Create and Configure File Systems       | Extend existing logical volumes                                                                               |          |     |           |       |     |
| 1.5          | Create and Configure File Systems       | Create and configure set-GID directories for collaboration                                                    |          |     |           |       |     |
| 1.5          | Create and Configure File Systems       | Diagnose and correct file permission problems                                                                 |          |     |           |       |     |
| 1.6          | Deploy, Configure, and Maintain Systems | Schedule tasks using `at` and `cron`                                                                          |          |     |           |       |     |
| 1.6          | Deploy, Configure, and Maintain Systems | Start and stop services and configure services to start automatically at boot                                 |          |     |           |       |     |
| 1.6          | Deploy, Configure, and Maintain Systems | Configure systems to boot into a specific target automatically                                                |          |     |           |       |     |
| 1.6          | Deploy, Configure, and Maintain Systems | Configure time service clients                                                                                |          |     |           |       |     |
| 1.6          | Deploy, Configure, and Maintain Systems | Install and update software packages from Red Hat Network, a remote repository, or from the local file system |          |     |           |       |     |
| 1.6          | Deploy, Configure, and Maintain Systems | Modify the system bootloader                                                                                  |          |     |           |       |     |
| 1.7          | Manage Basic Networking                 | Configure IPv4 and IPv6 addresses                                                                             |          |     |           |       |     |
| 1.7          | Manage Basic Networking                 | Configure hostname resolution                                                                                 |          |     |           |       |     |
| 1.7          | Manage Basic Networking                 | Configure network services to start automatically at boot                                                     |          |     |           |       |     |
| 1.7          | Manage Basic Networking                 | Restrict network access using `firewall-cmd`/`firewalld`                                                      |          |     |           |       |     |
| 1.8          | Manage Users and Groups                 | Create, delete, and modify local user accounts                                                                |          |     |           |       |     |
| 1.8          | Manage Users and Groups                 | Change passwords and adjust password aging for local user accounts                                            |          |     |           |       |     |
| 1.8          | Manage Users and Groups                 | Create, delete, and modify local groups and group memberships                                                 |          |     |           |       |     |
| 1.8          | Manage Users and Groups                 | Configure superuser access                                                                                    |          |     |           |       |     |
| 1.9          | Manage Security                         | Configure firewall settings using `firewall-cmd`/`firewalld`                                                  |          |     |           |       |     |
| 1.9          | Manage Security                         | Manage default file permissions                                                                               |          |     |           |       |     |
| 1.9          | Manage Security                         | Configure key-based authentication for SSH                                                                    |          |     |           |       |     |
| 1.9          | Manage Security                         | Set enforcing and permissive modes for SELinux                                                                |          |     |           |       |     |
| 1.9          | Manage Security                         | List and identify SELinux file and process context                                                            |          |     |           |       |     |
| 1.9          | Manage Security                         | Restore default file contexts                                                                                 |          |     |           |       |     |
| 1.9          | Manage Security                         | Manage SELinux port labels                                                                                    |          |     |           |       |     |
| 1.9          | Manage Security                         | Use boolean settings to modify system SELinux settings                                                        |          |     |           |       |     |
| 1.9          | Manage Security                         | Diagnose and address routine SELinux policy violations                                                        |          |     |           |       |     |
| 1.10         | Manage Containers                       | Find and retrieve container images from a remote registry                                                     |          |     |           |       |     |
| 1.10         | Manage Containers                       | Inspect container images                                                                                      |          |     |           |       |     |
| 1.10         | Manage Containers                       | Perform container management using commands such as `podman` and `skopeo`                                     |          |     |           |       |     |
| 1.10         | Manage Containers                       | Perform basic container management such as running, starting, stopping, and listing running containers        |          |     |           |       |     |
| 1.10         | Manage Containers                       | Run a service inside a container                                                                              |          |     |           |       |     |
| 1.10         | Manage Containers                       | Configure a container to start automatically as a systemd service                                             |          |     |           |       |     |
| 1.10         | Manage Containers                       | Attach persistent storage to a container                                                                      |          |     |           |       |     |



- **Resource**: You can fill this column with study materials such as official Red Hat documentation, books, online courses, or specific tutorials relevant to each subtopic.
- **Lab**: Indicate whether a hands-on lab exercise is available or needed for the subtopic.
- **Level 1-3**: Assign a difficulty or priority level to each subtopic based on your familiarity or the importance of the topic.
    - **Level 1**: Fundamental concepts; must know thoroughly.
    - **Level 2**: Intermediate topics; important but may require less focus.
    - **Level 3**: Advanced or niche topics; good to know but lower priority.
- **Notes**: Use this column for any additional comments, such as areas you find challenging or need to revisit.
---
# Reference
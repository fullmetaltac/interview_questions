
# Table of Contents
- [Table of Contents](#table-of-contents)
    - [shell](#shell)
    - [Docker](#docker)
    - [References:](#references)


### shell

>🔹***Explain pipes and redirections***

Both pipes and redirections redirect streams (file descriptor) of process being executed. The main difference is that redirections deal with files stream, sending the output stream to a file or sending the content of a given file to the input stream of the process.

On the other hand a pipe connects two commands by sending the output stream of the first one to the input stream of the second one. without any redirections specified.

```shell
arr=(cat dog horse cow) && (IFS=$'\n'; echo "${arr[*]}") > list.txt
sort < list.txt | tee list.txt

# output
cat
cow
dog
horse
```

---

>🔹***Explain chmod and chown***

Both chown and chmod are pillars of Linux Access Control and Linux Security. While chmod is designed to manage what actions can be performed on a file or directory (Read, Write, Execute Permissions), chown is engineered to control who can perform those actions (User and Group Ownership).

*chmod:*

```shell
-rw-r--r-- 1 cooluser cooluser 0 Jan  9 12:08 sample.txt
```

|  `-`  | `rw-` | `r--` | `r--` |  `1`  | `cooluser` | `cooluser` |  `0`  | `Jan  9 12:08` | `sample.txt` |
| :---: | :---: | :---: | :---: | :---: | :--------: | :--------: | :---: | :------------: | :----------: |
|   1   |   2   |   3   |   4   |   5   |     6      |     7      |   8   |       9        |      10      |

1. The `-` tells us the file is a regular file type. Other common types include: `d` for directories and `l`` for symlinks.
2. User permissions to the file - read and write.
3. Group permissions to the file - read only.
4. All users & groups permissions to the file - read only.
5. Number of links to the file.
6. Name of the user that owns the file.
7. Name of the group that owns the file
8. The size of the file in bytes.
9. The date and time that the file was created or last modified.
10. File name.


| Permission                     | Binary value | Decimal value |
| ------------------------------ | ------------ | ------------- |
| No permission (—)              | 000          | 0             |
| ***Execute*** only (–x)        | 001          | **1**         |
| ***Write*** only (-w-)         | 010          | **2**         |
| ***Read*** only (r–)           | 100          | **4**         |
| Write and execute (-wx)        | 011          | 3             |
| Read and execute (r-x)         | 101          | 5             |
| Read and write (rw-)           | 110          | 6             |
| Read, write, and execute (rwx) | 111          | 7             |

```shell
touch sample.txt
ls -l sample.txt
# output
-rw-r--r-- 1 cooluser cooluser 0 Jan  9 12:08 sample.txt

chmod 664 sample.txt
ls -l sample.txt
# output
-rw-rw-r-– 1 cooluser cooluser 0 Jan  9 12:08 sample.txt

```

| Character | Explanation                   |
| --------- | ----------------------------- |
| u         | User that owns the file       |
| g         | Group that owns the file      |
| o         | All other users and groups    |
| a         | All users and groups          |
| r         | Read permission               |
| w         | Write permission              |
| x         | Execute permission            |
| –         | Remove permission             |
| +         | Add permission                |
| =         | Make permissions exactly this |


```shell
chmod o+w sample.txt
ls -l sample.txt
# output
-rw-rw-rw- 1 cooluser cooluser 0 Jan  9 12:08 sample.txt
```

*chown:*

| sudo  | chown | someotheruser | sample.txt |
| :---: | :---: | :-----------: | :--------: |
|   1   |   2   |       3       |     4      |

1. sudo allows you to access the file by entering a password.   
2. chown command
3. The username of the new file owner, which is represented as user, user:, user:group, or :group.
4. Path to the file.

| Format for new owner | Explanation                                                                     |
| -------------------- | ------------------------------------------------------------------------------- |
| user                 | Changes only the user that owns the file.                                       |
| user:                | Changes the user that owns the file and changes the group to that user's group. |
| user:group           | Changes both the user and group that own the file.                              |
| :group               | Changes only the group that owns the file.                                      |


```shell
sudo chown someotheruser sample.txt
ls-l
# output
-rw-rw-rw- 1 someotheruser cooluser 0 Jan  9 12:10 sample.txt
```

---

### Docker

```shell
# stop all containers
docker stop $(docker ps -a -q)
# delete all
docker system prune -af
```


### References:

- https://www.cbtnuggets.com/blog/technology/system-admin/when-to-use-chmod-vs-chown
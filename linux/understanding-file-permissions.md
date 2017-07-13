# UNDERSTANDING FILE PERMISSIONS
Unix systems come with a file control mechanism to determine who can access a particular file or folder and what actions they can do to it. The file control mechanism consists of two parts; **classes** and **permissions**. Classes determine who can access the file while the permissions determine what actions the user can do to the file.  

Classes:  

1. Owner
2. Group
3. Other  

Permissions:  

1. Read
2. write
3. Execute

The number is an 8-bit data that controls the permissions.  


## Different permutations of the numbers
```
0 - no permission
1 - execute
2 - write
3 - write and execute
4 - read
5 - read and execute
6 - read and write
7 - read, write and execute  
```

For, example to set permissions to read and write use `'6' (4+2)` for the permission. For read, write and execute use `'7' (4+2+1)` for the permission.  

In the case for the 3 digits `777?`, the first digit is assigned to the Owner, the second the Group and the third digit is assigned to others.  

### Examples

```
755 - Commonly used in web servers. The Owner has permision to read, write and execute. Everyone else can only read and execute but not make changes to the file.
777 - Everyone can read, write and execute.
644 - Only the owner can read and write. Everyone else can only read.
655 - Only the owner can read and write, but not execute.Everyone else can read and execute, but cannot modify the file.
```

## Setting permission in CLI
`chmod 775 /path/to/file`  

## Changing Group Membership with usermod
Adding a user to a specific group:  
```bash
$ sudo usermod -a -G new-group noel
```
This command tells us to add the user noel to the `new-group`. The `a` options means **append** without which `usermod`
will overwrite the existing group membership(s) for noel. The option `-G` specifies the group to add the user to. Removing a user can be done by using the `gpasswd` command:
```
$ sudo gpasswd -d noel new-group
```

[source](https://www.maketecheasier.com/file-permissions-what-does-chmod-777-means/)

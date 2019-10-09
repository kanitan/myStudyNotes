linux提权初探

## linux权限划分

参考[https://www.cnblogs.com/kumata/p/8967744.html](https://www.cnblogs.com/kumata/p/8967744.html)

**Linux 里面一切皆文件**

一个目录要同时具有读权限和执行权限才可以打开，而一个目录要有写权限才允许在其中创建其它文件。

- 查看文件属性

```shell
ll
ls -a
```

- 查看文件夹属性

```shell
ls -dl <dirname>
```

### 文件权限表示

![filePrivilege.png](/Users/reyiko/Documents/notes/linux提权/img/filePrivilege.png)

- `Type`: 很多种 (最常见的是 `-` 为文件, `d` 为文件夹, 其他的还有`l`, `n` … 这种东西, 真正自己遇到了, 网上再搜就好, 一次性说太多记不住的).
- `User`: 后面跟着的三个空是使用 User 的身份能对这个做什么处理 (`r` 能读; `w` 能写; `x`能执行; `-` 不能完成某个操作).
- `Group`: 一个 Group 里可能有一个或多个 user, 这些权限的样式和 User 一样.
- `Others`: 除了 User 和 Group 以外人的权限.

特殊权限—SUID

强制位（s权限）和粘滞位（t权限）

修改权限

- 二进制形式操作

每个文件的三组权限（拥有者，所属用户组，其他用户,记住这个顺序是一定的）就对应这一个 "rwx"，也就是一个 '7' 

```
r=4, w=2 , x=1
```

如果要变更权限，使用命令``chmod`` 

```shell
chmod 740 <filename> 
```

- 加减赋值操作

``g`` 、``o``、``u``和``a``，分别表示group、others、user和所有人，'+'，'-' 就分别表示增加和去掉相应的权限。

```shell
chmod [谁][+/-][权限] [哪个文件]
chmod u+r <filename>
```

## 提权操作

参考[https://www.freebuf.com/articles/system/173903.html](https://www.freebuf.com/articles/system/173903.html)

- 查找具有SUID或者4000权限的文件

s权限和t权限[https://www.cnblogs.com/yiyide266/p/10047340.html](https://www.cnblogs.com/yiyide266/p/10047340.html)

权限掩码umask[https://www.cnblogs.com/MrListening/p/5821296.html](https://www.cnblogs.com/MrListening/p/5821296.html)

**s权限**

设置使文件在执行阶段具有文件所有者的权限



```shell
find / -perm -u=s -type f 2>/dev/null
```


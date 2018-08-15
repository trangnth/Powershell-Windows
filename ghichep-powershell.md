---
layout: post
title: Ghi chép PowerShell
author: trangnth

"editor.insertSpaces": true,
"editor.tabSize": 4,
"editor.detectIndentation": true
---


## Một số lệnh cần biết

Di chuyển để thư mục home của user hiện tại: 

```sh
PS C:\> cd ~
PS C:\Users\Bosua>
```

Di chuyển sang disk khác, ví dụ sang ổ D:

	D:

Quay lại disk vừa di chuyển đi thì sẽ về thư mục cuối cùng khi bạn rời đi. Ví dụ đang ở `C:\User` di chuyển sang ổ D thì vị trí sẽ là `D:` và di chuyển lại ổ `C:` thì vị trí sẽ là `C:\User`

Copy file:

	copy <file-src> <file-dest>

Xóa file:

	rm <file name>
	

### Với lệnh dir

Liệt kê các file và thư mục con có trong thư mục hiện tại:

```sh
PS C:\Users\Bosua> dir

    Directory: C:\Users\Bosua

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----       08/01/2018   5:11 PM                .idlerc
d-----       08/01/2018   2:45 PM                .ipython
d-r---       08/02/2018   1:54 PM                3D Objects
```

`Mode` thể hiện cho các thuộc tính của file hoặc folder đó.

```sh
d - Directory
a - Archive
r - Read-only
h - Hidden
s - System
l - Reparse point, symlink, etc.
```

Sử dụng lệnh sau để xem các mode của các file, thư mục con có trong thư mục hiện tại:
```sh
PS C:\Users\Bosua> gci|select mode,attributes -u

Mode                                   Attributes
----                                   ----------
d-----                                  Directory
d-r---                        ReadOnly, Directory
dar--l ReadOnly, Directory, Archive, ReparsePoint
-a----                                    Archive
```

Nếu muốn xem tất cả các thuộc tính của hệ điều hành, gõ lệnh như dưới đây:

```sh
PS C:\Users\Bosua> [enum]::GetNames("system.io.fileattributes")
ReadOnly
Hidden
System
Directory
Archive
Device
Normal
Temporary
SparseFile
ReparsePoint
Compressed
Offline
NotContentIndexed
Encrypted
IntegrityStream
NoScrubData
```

Xem thêm [ở đây](https://msdn.microsoft.com/en-us/library/system.io.fileattributes(v=vs.110).aspx)


### File

#### Tạo file

Tạo file sử dụng `echo`

```sh
PS C:\> echo some-text  > filename.txt
PS C:\> type sample.txt
This is a sample text file
```

Tạo file sử dụng `fsutil`, yêu cầu sử dụng lệnh với administrative privileges:

```sh
fsutil file createnew filename number_of_bytes

PS C:\data> fsutil file createnew sample2.txt 2000
File C:\sample2.txt is created
PS C:\data> dir
01/23/2016  09:34 PM     2,000 sample2.txt
```

Một cách đơn giản hơn với `New-Item`, tôi thường sử dụng cách này hơn

```sh
New-Item <Path to file> -type file
```

với `<Path to file>` là đường dẫn của file muốn tạo, có thể là tên file mới nếu muốn tạo ngay tại thư mục hiện tại, hoặc đường dẫn tuyệt đối của file để chỉ định rõ nơi muốn tạo file. Ví dụ: 

```sh
New-Item c:\test.txt -type file

hoặc

New-Item -path "c:\" -type file -name "test.txt"
```

#### Xóa file

	PS C:\> Remove-Item C:\Test\*.*


### icacls

https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/icacls


## Tham khảo thêm

https://vinasupport.com/cai-dat-va-kich-hoat-linux-subsystem-tren-windows-10/
## 1. Một số lệnh cần biết

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
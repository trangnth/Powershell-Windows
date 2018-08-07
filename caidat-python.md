# Python 3 on windows

Cài đặt và sử dụng python 3 bằng dòng lệnh trên windows 10

1. [Cài đặt](#install)
2. []


## Cài đặt

### Bước 1: Mở và cấu hình PowerShell

Di chuyển vào thư mục user hiện hành:

```sh
cd ~
```

Thiết lập policy `RemoteSigned` cấp quyền cho người dùng hiện tại  cho phép powershell downloaded

```sh
Set-ExecutionPolicy -Scope CurrentUser
```

Nhập `RemoteSigned` vào. Sau đó kiểm tra xem đã thiết lập thành công chưa:

```sh
PS C:\Users\Bosua> Get-ExecutionPolicy -List

        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine       Undefined
```

### Bước 2: Cài đặt Chocolatey quản lý gói

Trình quản lý gói là một tập hợp các công cụ phần mềm hoạt động để tự động hóa các quá trình cài đặt, gồm: cài đặt ban đầu, upgrading, configuring của phần mềm, và xóa nó nếu cần.

Chúng giữ các cài đặt tập trung một chỗ và có thể duy trì tất cả các gói trên hệ thống theo các định dạng thường được sử dụng.

Chocolatey là một trình quản lý gói bằng dòng lệnh được xây dựng cho windows, nó tương tự như `apt-get` trong Linux. Có sẵn trong các phiên bản open-source, `Chocolatey` sẽ giúp bạn cài đặt nhanh chóng các ứng dụng và tool và sự dụng nó để tải xuống những gì cần thiết cho development environment của chúng ta.


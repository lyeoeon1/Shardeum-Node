# Hướng dẫn chạy Shardeum Node
# Shardeum-Node

## PHẦN 1: Thuê VPS (trên Contabo)

Liên kết : https://contabo.com/en/vps/

Chọn gói : CLOUD VPS M

![image](https://github.com/TongThenHung/Shardeum-Node/assets/99159962/21d5cd9b-f68c-4313-a0da-7db2ddd7c70a)


## PHẦN 2: Cách kết nối với VPS của bạn

Với Windows:
Tải Putty ( Bạn có thể cài đặt bằng liên kết này "https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html" ).

Sau khi tải xong:

1. Bây giờ khởi chạy Putty
2. Nhập địa chỉ IP mà Contabo đã gửi qua Email vào ô (Host Name (or IP address)) -> Nhấn "Open"
3. Giao diện máy chủ sẽ mở ra và yêu cầu bạn cung cấp thông tin đăng nhập:
    1. Tại dòng login as:. Nhập "root" nhấn Enter
    2. Tại dòng root@xxx.xx.xx.xx's password. Nhập mật khẩu đã được Contabo gửi qua Email
    

![image](https://github.com/TongThenHung/Shardeum-Node/assets/99159962/d399e338-40dc-4eb9-8cd3-7360feecf4c6)
Giao diện đăng nhập thành công

## PHẦN 3: Cài đặt

### Tiến hành cập nhật các gói

```powershell
sudo apt-get install curl
```

```powershell
sudo apt update && sudo apt upgrade -y
```

```powershell
sudo apt install docker.io
```

```powershell
docker --version
```

Kiểm tra xem docker có đang hoạt động không (nên trả về phiên bản 20.10.12 trở lên)

### Cài đặt docker-compose

```powershell
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

```powershell
sudo chmod +x /usr/local/bin/docker-compose
```

```powershell
docker-compose --version
```

Kiểm tra xem docker-compose có hoạt động không (nên trả về phiên bản 1.29.2 trở lên)

### Cài đặt Tmux

Để có thể quản lý nhiều nodes trên một vps

```powershell
apt install tmux
```

```powershell
tmux
```

### Tải xuống và cài đặt validator

(Bên trong tmux được định danh bằng số : 0,1,2,.. Nằm ở thành màu xanh dưới màn hình)

```powershell
curl -O https://gitlab.com/shardeum/validator/dashboard/-/raw/main/installer.sh && chmod +x installer.sh && ./installer.sh
```

```powershell
By running this installer, you agree to allow the Shardeum team to collect this data. (y/n)?:
```

**Nhập : y, sau đó nhấn Enter**

```powershell
Do you want to run the web based Dashboard? (y/n):
```

**Nhập : y, sau đó nhấn Enter**

```powershell
Set the password to access the Dashboard:
```

**Nhập mật khẩu do bạn đặt (nhớ lưu lại), sau đó nhấn Enter**

```powershell
Enter the port (1025-65536) to access the web based Dashboard (default 8080):
```

**Nhập 8080, sau đó nhấn Enter**

```powershell
If you wish to set an explicit external IP, enter an IPv4 address (default=auto):
```

**Nhấn Enter**

```powershell
If you wish to set an explicit internal IP, enter an IPv4 address (default=auto):
```

**Nhấn Enter**

```powershell
To run a validator on the Sphinx Validator 1.X network, you will need to open two ports in your firewall.
This allows p2p communication between nodes.
Enter the first port (1025-65536) for p2p communication (default 9001):
```

**Nhấn Enter**

```powershell
Enter the second port (1025-65536) for p2p communication (default 10001):
```

**Nhấn Enter**

```powershell
What base directory should the node use (defaults to ~/.shardeum):
```

**Nhấn Enter**

![image](https://github.com/TongThenHung/Shardeum-Node/assets/99159962/4ef69cf0-a94e-40e9-b676-cc31ffce36bc)
Đợi vài phút

![image](https://github.com/TongThenHung/Shardeum-Node/assets/99159962/25ea227a-61e9-49df-9d06-7a39674cfe46)
Bây giờ bạn có thể thực bước tiếp theo

### Mở validator CLI

```powershell
cd .shardeum
```

```powershell
./shell.sh
```

### Mở validator **GUI**

```powershell
operator-cli gui start
```

```powershell
operator-cli gui start
```

Truy cập trình duyệt web và truy cập theo đường dẫn sau

```powershell
https://localhost:8080/
```

Thay “localhost” bằng địa chỉ IP VPS

![image](https://github.com/TongThenHung/Shardeum-Node/assets/99159962/8ee4060b-445a-456b-ab8c-5d01900b26ec)

Sau đo nhập mật khẩu ở trên mà mình đã đặt ở bước trên

![image](https://github.com/TongThenHung/Shardeum-Node/assets/99159962/5a937689-31c2-4185-b723-0e1756ec777c)
Giao diện sau khi đăng nhập thành công

Chuyển sang tab : Maintenance

![image](https://github.com/TongThenHung/Shardeum-Node/assets/99159962/b33af139-7276-4e0a-96e0-0ae289e5434f)
Giao diện trang Maintenance

Nhấn Start Node (đợi một chút)

Làm theo hướng dẫn sau để có thể nhận SHM :

liên kết : 

[Claim Testnet SHM | Shardeum Docs](https://docs.shardeum.org/faucet/claim#shardeum-faucet-website)

Tiếp theo kết nối với ví của bạn đã có SHM, nhấn vào Connect Wallet (Hoàn thành các bước xác thực với ví)

![image](https://github.com/TongThenHung/Shardeum-Node/assets/99159962/d5502efb-49f1-4546-9948-30f745abde68)

Sau khi đã kết nối với ví của mình

Sau đó bạn nhấp vào "Add Stake", bạn sẽ thấy như sau:

![hiha](https://github.com/TongThenHung/Shardeum-Node/assets/99159962/63bc25a0-fccf-405c-95ff-e928a7a294e0)

Nhập 10 và Nhấn “Stake”

Tham khảo:

Hướng dẫn từ trang chính thức từ Shardeum : https://docs.shardeum.org/node/run/validator

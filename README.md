# Bài 3: Cấu hình tường lửa UFW và chuẩn đoán cổng mạng

## 1. Mục tiêu

* Cấu hình UFW trên Ubuntu Server.
* Chặn toàn bộ kết nối đi vào mặc định.
* Cho phép kết nối đi ra.
* Mở SSH port 22.
* Mở Web Application port 8080.
* Kiểm tra trạng thái UFW và các port đang lắng nghe.

## 2. Cấu hình UFW

### Thiết lập chính sách mặc định

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

### Cho phép SSH

```bash
sudo ufw allow 22/tcp
```

### Cho phép Web Application

```bash
sudo ufw allow 8080/tcp
```

### Kích hoạt UFW

```bash
sudo ufw enable
```

## 3. Kiểm tra trạng thái UFW

Lệnh:

```bash
sudo ufw status verbose
```

Kết quả:

```text
Status: active

Default: deny (incoming), allow (outgoing), disabled (routed)

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW IN    Anywhere
8080/tcp                   ALLOW IN    Anywhere
```

## 4. Kiểm tra các port đang lắng nghe

Lệnh:

```bash
ss -tlnp
```

Port 8080 xuất hiện khi ứng dụng Web đang thực sự chạy và lắng nghe trên port này.

## 5. Kết luận

Đã hoàn thành cấu hình UFW với:

* Incoming: DENY mặc định.
* Outgoing: ALLOW mặc định.
* SSH port 22: ALLOW.
* Web Application port 8080/tcp: ALLOW.
* UFW: ACTIVE.

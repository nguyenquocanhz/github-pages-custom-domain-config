# Hướng dẫn cấu hình Custom Domain cho GitHub Pages qua Cloudflare

## 1. Giới thiệu

GitHub Pages là dịch vụ miễn phí của GitHub cho phép triển khai website
tĩnh trực tiếp từ repository. Để sử dụng tên miền riêng (custom domain),
cần cấu hình DNS chính xác. Cloudflare thường được chọn vì khả năng tăng
tốc và bảo mật website.

Tài liệu này cung cấp quy trình từng bước để trỏ domain từ Cloudflare về
GitHub Pages.

![Minh họa GitHub
Pages](https://docs.github.com/assets/cb-23923/mw-1440/images/help/pages/pages-overview.webp)

------------------------------------------------------------------------

## 2. Yêu cầu chuẩn bị

Trước khi bắt đầu, cần có:

-   **Tài khoản Cloudflare**: quản lý DNS của domain.\
-   **Domain hợp lệ**: đã mua và có quyền quản trị DNS.\
-   **Tài khoản GitHub**: để triển khai dự án.\
-   **Project GitHub Pages**: repository đã bật tính năng GitHub Pages.

![Cloudflare
Dashboard](cloudflare.jpg)

------------------------------------------------------------------------

## 3. Địa chỉ IP của GitHub Pages

Cloudflare cần cấu hình các bản ghi A (IPv4) và AAAA (IPv6) để trỏ về hạ
tầng GitHub Pages.\
Danh sách IP chính thức của GitHub:

**IPv4**

    185.199.108.153
    185.199.109.153
    185.199.110.153
    185.199.111.153

**IPv6**

    2606:50c0:8000::153
    2606:50c0:8001::153
    2606:50c0:8002::153
    2606:50c0:8003::153

![Cấu hình DNS trong
Cloudflare](https://developers.cloudflare.com/dns/static/dns-records-ui.png)

------------------------------------------------------------------------

## 4. Các bước cấu hình

### 4.1. Bước 1: Thêm domain vào Cloudflare

1.  Đăng nhập Cloudflare.\
2.  Thêm domain vào tài khoản Cloudflare.\
3.  Đổi nameserver tại nơi mua domain sang nameserver Cloudflare cung
    cấp.

### 4.2. Bước 2: Cấu hình DNS

Trong phần **DNS Management** của domain, thêm các bản ghi sau:

-   **A records**: 4 bản ghi, trỏ tới từng địa chỉ IPv4.\
-   **AAAA records**: 4 bản ghi, trỏ tới từng địa chỉ IPv6.

### 4.3. Bước 3: Cấu hình GitHub Pages

1.  Vào repository → **Settings** → **Pages**.\
2.  Trong mục **Custom domain**, nhập domain của bạn (ví dụ:
    `www.example.com`).\
3.  GitHub sẽ tạo file `CNAME` tự động trong repository.

![Cấu hình GitHub
Pages](https://docs.github.com/assets/cb-33537/mw-1440/images/help/pages/pages-custom-domain.webp)

### 4.4. Bước 4: Kiểm tra hoạt động

-   Truy cập domain để kiểm tra website đã chạy.\
-   Dùng lệnh `dig` hoặc `nslookup` để kiểm tra DNS đã trỏ đúng.\
-   Nếu gặp lỗi HTTPS, bật **"Always Use HTTPS"** trong Cloudflare.

------------------------------------------------------------------------

## 5. Kết luận

Sau khi hoàn thành, website tĩnh triển khai trên GitHub Pages có thể
truy cập bằng domain riêng thông qua Cloudflare, hưởng lợi từ: - DNS tốc
độ cao, phân giải toàn cầu.\
- Tích hợp HTTPS miễn phí qua Cloudflare.\
- Tăng cường bảo mật và tối ưu hiệu năng.

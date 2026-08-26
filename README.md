# VNmap

Bản đồ Việt Nam chạy trực tiếp trên GitHub Pages.

## Mục tiêu kỹ thuật

- Static HTML/CSS/JS, không cần backend.
- Nền chính dùng raster tile để giảm lỗi CORS của các nguồn vector.
- Tự động chuyển sang nền dự phòng nếu nguồn tile chính không khả dụng.
- Giao diện icon-only cho: Standard, Light, Dark, Raster, Satellite, Dev Light, Việt Nam, Cấu hình.
- Tìm kiếm địa điểm tại Việt Nam.
- URL camera dạng `#zoom/lat/lon`.

## GitHub Pages

Workflow `.github/workflows/pages.yml` tự triển khai khi có thay đổi trên nhánh `main`.

> API key phía client luôn có thể quan sát trong mã hoặc Network của trình duyệt. Hãy giới hạn origin/domain/quota ở nhà cung cấp dịch vụ trước khi sử dụng công khai.

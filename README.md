# VNmap

Bản đồ Việt Nam chạy trực tiếp trên GitHub Pages, sử dụng **Vietflex 1.0.0** làm lõi bản đồ và **VNPT GoMaps** làm nền mặc định.

## CDN đang dùng

```html
<link rel="stylesheet"
  href="https://cdn.jsdelivr.net/gh/Vietflexmap/VN@6144d565fcf236727577ab3c4471bbe49f86892f/dist/vietflex.css">
<script src="https://cdn.jsdelivr.net/gh/Vietflexmap/VN@6144d565fcf236727577ab3c4471bbe49f86892f/dist/vietflex.js"></script>
```

Commit SHA được pin cố định để tránh thay đổi ngoài dự kiến khi deploy production.

## Kiến trúc

- `Vietflex.vietflexMap(...)` khởi tạo bản đồ với `googleMaps: false`.
- `Vietflex.ZoomControl` và `Vietflex.AttributionControl` thay control Leaflet trực tiếp.
- Attribution giao diện hiển thị **Vietflex | VNPT GoMaps**, không hiển thị liên kết Leaflet.
- Standard / Light / Dark / Raster / Dev Light đều dùng `Vietflex.TileLayer` với nền VNPT GoMaps; Light/Dark/Dev Light chỉ thay đổi CSS filter.
- Satellite là lớp tùy chọn riêng dùng `Vietflex.legacyGoogleTiles({ mapType: 'satellite' })`.
- Nền dự phòng dùng `Vietflex.TileLayer` với OpenStreetMap nếu VNPT lỗi nhiều lần.
- Không sử dụng MapLibre vector/PBF nên tránh nhóm lỗi `.vector.pbf` trước đây.
- Giao diện icon-only cho Standard, Light, Dark, Raster, Satellite, Dev Light, Việt Nam và Cấu hình.
- Tìm kiếm địa điểm tại Việt Nam và URL camera dạng `#zoom/lat/lon`.

## GitHub Pages

Workflow `.github/workflows/pages.yml` xuất bản nội dung từ `main` sang nhánh `gh-pages`.

> API key phía client luôn có thể quan sát trong source hoặc Network của trình duyệt. Khi triển khai công khai, cần giới hạn origin/domain/quota tại nhà cung cấp dịch vụ.

# Bài 5: Nối Job tự động Build & Push Docker Image sau khi Test Gradle xanh

## Giới thiệu
Tệp cấu hình GitHub Actions (`.github/workflows/ci.yml`) tách quy trình CI thành 2 Job độc lập nhưng có liên kết:
1. **test**: Chạy Gradle test và đóng gói tệp JAR.
2. **docker-build**: Đăng nhập vào GHCR và đóng gói/đẩy Docker Image lên registry chỉ khi job `test` thành công (nhờ sử dụng `needs: test`).

## Cấu trúc thư mục
- `.github/workflows/ci.yml`: Tệp kịch bản GitHub Actions.
- `README.md`: Hướng dẫn chi tiết.

## Hướng dẫn chạy và kiểm tra
1. Đẩy mã nguồn kèm tệp cấu hình này lên nhánh `main` của repository GitHub.
2. Truy cập tab **Actions** trên GitHub để quan sát sơ đồ trực quan của workflow.
3. Thử sửa đổi mã nguồn để test Gradle bị lỗi, xác nhận job `docker-build` sẽ tự động chuyển sang trạng thái `Skipped`.
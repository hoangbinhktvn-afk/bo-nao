# Bộ não thứ hai

Ứng dụng ghi chú cá nhân chạy trên trình duyệt (iPhone, máy tính), dùng được khi không có mạng. Ghi chú lưu trên máy và đồng bộ với một kho GitHub riêng tư.

## Chức năng

- **Ghi nhanh** vào Hộp thư đến; ghi theo mẫu (cuộc họp, ý tưởng, tài liệu đã đọc, văn bản, dự án).
- **Sắp xếp theo PARA**: Dự án, Lĩnh vực, Tài nguyên, Lưu trữ.
- **Liên kết** `[[Tên ghi chú]]`, thẻ `#thẻ`, danh sách "Được nhắc đến ở", gợi ý ghi chú có nội dung gần, sơ đồ liên kết.
- **Việc cần làm**: dòng `- [ ] Nội dung @20/11` được gom về một trang, chia Quá hạn, Hôm nay, Sắp tới.
- **Nhật ký ngày** (nút Hôm nay) và **Ôn lại** ghi chú cũ theo chu kỳ 1, 3, 7, 14, 30, 60, 120 ngày.
- **Tìm kiếm** toàn văn, gõ có dấu hoặc không dấu.
- **Khoá bằng mật khẩu**: AES-256-GCM, khoá dẫn xuất bằng PBKDF2 600.000 vòng. Khi bật, dữ liệu trên máy, mã truy cập GitHub và các tệp gửi lên GitHub đều được mã hoá.
- **Đồng bộ GitHub**: mỗi ghi chú là một tệp `notes/<mã>.md`. Sửa ở hai máy cùng lúc thì bản cũ hơn được giữ thành "bản xung đột".
- **Xuất, nhập**: ZIP Markdown (mở được bằng Obsidian), JSON.

## Cài đặt (làm một lần)

1. **Đưa ứng dụng lên GitHub Pages**: tạo kho (ví dụ `bo-nao`), đưa các tệp trong thư mục này lên, vào Settings > Pages, chọn nhánh `main`, thư mục `/ (root)`. Địa chỉ ứng dụng có dạng `https://<tài-khoản>.github.io/bo-nao/`. Với tài khoản miễn phí, GitHub Pages yêu cầu kho mã công khai; kho này chỉ chứa mã ứng dụng, không chứa ghi chú.
2. **Tạo kho dữ liệu riêng tư** (ví dụ `bo-nao-du-lieu`), để trống cũng được.
3. **Tạo mã truy cập**: GitHub > Settings > Developer settings > Personal access tokens > Fine-grained tokens. Chọn "Only select repositories" và chỉ chọn kho dữ liệu; quyền Repository permissions > Contents: Read and write.
4. Mở ứng dụng > Cài đặt và đồng bộ: nhập `tài-khoản/bo-nao-du-lieu` và mã truy cập, bấm Kết nối và đồng bộ. Nên đặt mật khẩu khoá ngay sau đó.
5. **Trên iPhone**: mở địa chỉ ứng dụng bằng Safari > Chia sẻ > Thêm vào Màn hình chính. Trên máy thứ hai, lặp lại bước 4 và nhập đúng mật khẩu đã đặt.

## Ghi nhanh bằng Phím tắt iPhone

Tạo phím tắt gồm hai bước: "Đọc chính tả văn bản" (hoặc "Yêu cầu nhập"), rồi "Mở URL" với địa chỉ `https://<tài-khoản>.github.io/bo-nao/?ghi=<Văn bản>`. Nội dung được lưu vào Hộp thư đến.

## Lưu ý an toàn

- Quên mật khẩu khoá thì không khôi phục được dữ liệu. Nên xuất JSON định kỳ và cất ở nơi an toàn.
- Mã truy cập chỉ lưu trên thiết bị. Đặt thời hạn cho mã và thu hồi trên GitHub khi mất máy.
- Ứng dụng không gửi dữ liệu đi đâu ngoài `api.github.com`.

# Hướng dẫn cài đặt

## 1. Tạo repo
Vào GitHub → New repository → đặt tên **chính xác** là: `ducmanh-jr`
(trùng với username của bạn — bắt buộc để GitHub nhận diện là Profile README)

Chọn **Public**, không cần thêm README/gitignore lúc tạo (vì mình đã có sẵn).

## 2. Upload toàn bộ nội dung thư mục này
Upload đúng cấu trúc:
```
ducmanh-jr/
├── README.md
├── SETUP.md
└── .github/
    └── workflows/
        ├── snake.yml
        └── metrics.yml
```

## 3. Bật quyền ghi cho GitHub Actions (bắt buộc cho snake.yml)
Vào repo → **Settings → Actions → General → Workflow permissions**
→ chọn **"Read and write permissions"** → Save.

## 4. Tạo Personal Access Token cho metrics.yml (bắt buộc)
`GITHUB_TOKEN` mặc định không đủ quyền đọc dữ liệu thống kê (issues, PR, community...).

1. Vào **Settings (tài khoản, góc trên phải) → Developer settings → Personal access tokens → Tokens (classic)**
2. Generate new token → tick quyền: `repo`, `read:user`
3. Copy token vừa tạo
4. Vào repo `ducmanh-jr` → **Settings → Secrets and variables → Actions → New repository secret**
5. Name: `METRICS_TOKEN`, Value: dán token vừa copy → Add secret

## 5. Chạy Actions lần đầu
Vào tab **Actions** của repo → chọn workflow **"Generate Snake Animation"** → **Run workflow**.
Làm tương tự với **"Generate Metrics Dashboard"**.

Sau khi chạy xong (vài phút):
- `snake.yml` sẽ tạo nhánh `output` chứa file SVG con rắn
- `metrics.yml` sẽ commit file `metrics.svg` vào nhánh `main`

Từ hôm sau, cả 2 sẽ tự động cập nhật mỗi ngày (00:00 UTC) mà không cần làm gì thêm.

## 6. Kiểm tra
Vào `https://github.com/ducmanh-jr` — README sẽ hiển thị ngay đầu trang profile,
kèm hiệu ứng typing, snake animation và metrics dashboard đầy đủ.

## Lưu ý
- Ảnh **GitHub Stats / Streak stats** dùng service ngoài (vercel.app, herokuapp.com) — không cần setup, tự chạy.
- Nếu snake/metrics chưa hiện ảnh ngay, đợi 5–10 phút để GitHub cache lại raw content.
- Muốn đổi theme màu: sửa `theme=tokyonight` trong README.md thành `dark`, `radical`, `merko`, `gruvbox`...

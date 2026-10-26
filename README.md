# Cổng Bình Chọn Sinh Viên Tiêu Biểu 2026 — FPT Polytechnic Đồng Nai

Ứng dụng bình chọn trực tuyến thời gian thực kèm Cổng Quản Trị CMS (`/admin`) xây dựng cho **Cao đẳng FPT Polytechnic — Cơ sở Đồng Nai**.

## Công nghệ sử dụng
- **Framework**: Next.js 16 (App Router, TypeScript, Cache Components + Streaming)
- **Giao diện & Nhận diện**: Tailwind CSS v4 (Tông Trắng `#FFFFFF` & Cam chuẩn FPT `#F26F21`), Framer Motion, `canvas-confetti`, `lucide-react`
- **Cơ sở dữ liệu**: PostgreSQL + Drizzle ORM (ACID Transaction Lock chống gian lận, giới hạn 03 lượt vote/ngày reset lúc `00:00:00`)
- **Xác thực người bình chọn**: Auth.js / NextAuth v5 với **Google OAuth 2.0**
- **Quản trị nội dung (`/admin`)**: Quản lý thêm/sửa/xóa thí sinh, bài viết tin tức, tải ảnh lên máy chủ, phiên đăng nhập bảo mật HMAC-SHA256 `HttpOnly` cookie
- **Đồng bộ tức thì**: Server-Sent Events (`/api/stream`) + SWR

## Hướng dẫn cài đặt & Chạy dự án

### 1. Cài đặt thư viện
```bash
npm install
```

### 2. Cấu hình biến môi trường (`.env`)
Sao chép `.env.example` sang `.env` (hoặc chỉnh trực tiếp file `.env` có sẵn):
```env
DATABASE_URL="postgresql://postgres:220206@localhost:5432/fpt_voting"
AUTH_SECRET="fpt-inspiring-youth-voting-2026-super-secret-key-9f8e7d6c5b4a"
AUTH_TRUST_HOST="true"
GOOGLE_CLIENT_ID="your-google-client-id.apps.googleusercontent.com"
GOOGLE_CLIENT_SECRET="your-google-client-secret"
APP_TIMEZONE="Asia/Ho_Chi_Minh"
ADMIN_USERNAME="admin"
ADMIN_PASSWORD="fpoly2026"
```

### 3. Khởi tạo bảng & Dữ liệu mẫu PostgreSQL
```bash
npm run db:seed
```

### 4. Khởi chạy ứng dụng
```bash
# Chạy môi trường phát triển (cổng 3000 hoặc 3005)
npm run dev

# Hoặc build bản Production
npm run build
npm run start
```

- **Trang bình chọn công khai**: `http://localhost:3000` (hoặc `http://localhost:3005`)
- **Cổng quản trị CMS**: `http://localhost:3000/admin` (Tài khoản mặc định: `admin` / `fpoly2026`)

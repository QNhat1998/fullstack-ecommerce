# Context: Food Page Project (Starbucks Style)

Tài liệu này dùng để cung cấp ngữ cảnh cho AI mỗi khi bạn bắt đầu một phiên làm việc mới. Hãy copy nội dung này gửi cho AI để nó nắm bắt chính xác những gì bạn đang triển khai.

---

## 1. Mục tiêu dự án

- Xây dựng trang web/fanpage về thực phẩm (Food Page).
- Phong cách thiết kế: Lấy cảm hứng từ hệ thống thiết kế của **Starbucks** (Warm, Confident, Retail Flagship).

## 2. Cấu hình kỹ thuật hiện tại (globals.css)

Hệ thống đang sử dụng mã màu Hex trực tiếp và Tailwind CSS:

- **Nền (Background):** `#f2f0eb` (Light) | `#1E3932` (Dark).
- **Màu chủ đạo (Primary):** `#006241` (Starbucks Green).
- **Màu hành động (Accent):** `#00754A` (Green Accent).
- **Bo góc (Radius):** `50px` (Full-pill cho nút bấm).
- **Typography:** `letter-spacing: -0.01em` (Tight tracking).

## 3. Danh sách Class Tailwind quy ước

Khi yêu cầu AI viết code, hãy yêu cầu tuân thủ các class sau:

- **Nền trang:** `bg-background`
- **Tiêu đề:** `text-primary`
- **Nút bấm:** `bg-accent text-accent-foreground rounded-full btn-active-click`
- **Thẻ món ăn:** `bg-card shadow-brand rounded-[12px]`
- **Văn bản phụ:** `text-muted-foreground`

## 4. Các Utility Custom (Đã định nghĩa trong CSS)

- `btn-active-click`: Hiệu ứng `scale(0.95)` khi nhấn nút.
- `shadow-brand`: Đổ bóng 2 lớp siêu mịn.
- `shadow-float`: Đổ bóng mạnh cho các thành phần nổi.

## 5. Lưu ý quan trọng cho AI

- Không sử dụng mã màu Hex thủ công trong file component.
- Luôn ưu tiên bố cục hình ảnh lớn (visual-heavy).
- Luôn đảm bảo hỗ trợ cả Light Mode và Dark Mode (House Green).

## 6. Thiết lập CSS cốt lõi (globals.css)

Hệ thống sử dụng mã Hex chính xác và các biến CSS đã được cấu hình như sau:

```css
@layer base {
  :root {
    /* --- LIGHT MODE (Mã Hex từ DESIGN.md) --- */
    /* Nền Neutral Warm - Tạo cảm giác ấm áp, ngon mắt */
    --background: #f2f0eb;
    --foreground: rgba(0, 0, 0, 0.87);

    --card: #ffffff;
    --card-foreground: rgba(0, 0, 0, 0.87);
    --popover: #ffffff;
    --popover-foreground: rgba(0, 0, 0, 0.87);

    /* Primary: Starbucks Green (#006241) - Dùng cho tiêu đề/Brand */
    --primary: #006241;
    --primary-foreground: #ffffff;

    /* Accent: Green Accent (#00754A) - Dành cho CTA/Nút bấm */
    --accent: #00754A;
    --accent-foreground: #ffffff;

    /* Muted: House Green (#1E3932) */
    --muted: #1E3932;
    --muted-foreground: rgba(255, 255, 255, 0.70);

    --secondary: #edebe9; /* Ceramic */
    --secondary-foreground: rgba(0, 0, 0, 0.87);

    /* Màu trạng thái */
    --warning: #cba258; /* Gold */
    --warning-foreground: #ffffff;
    --destructive: #c82014; /* Red */
    --destructive-foreground: #ffffff;
    --success: #00754A; /* Tái sử dụng Green Accent cho Success */
    --success-foreground: #ffffff;

    /* Border & Inputs */
    --border: #edebe9;
    --input: #d6dbde;
    --ring: #006241;

    /* Radius: 50px Full-pill đặc trưng */
    --radius: 50px;

    /* Chart colors (Giữ nguyên cấu trúc nhưng có thể tinh chỉnh sau) */
    --chart-1: 12 76% 61%;
    --chart-2: 173 58% 39%;
    --chart-3: 197 37% 24%;
    --chart-4: 43 74% 66%;
    --chart-5: 27 87% 67%;
  }

  .dark {
    /* --- DARK MODE (Sử dụng House Green làm chủ đạo) --- */
    --background: #1E3932;
    --foreground: rgba(255, 255, 255, 0.87);

    --card: #2b5148; /* Green Uplift */
    --card-foreground: rgba(255, 255, 255, 0.87);
    --popover: #1E3932;
    --popover-foreground: rgba(255, 255, 255, 0.87);

    --primary: #008248; /* Sáng hơn một chút trên nền tối */
    --primary-foreground: #ffffff;

    --secondary: #2b5148;
    --secondary-foreground: #ffffff;

    --muted: #2b5148;
    --muted-foreground: rgba(255, 255, 255, 0.7);

    --accent: #00754A;
    --accent-foreground: #ffffff;

    --border: rgba(255, 255, 255, 0.1);
    --input: rgba(255, 255, 255, 0.1);
    --ring: #008248;
  }
}

@layer base {
  * {
    @apply border-border;
  }
  body {
    @apply bg-background text-foreground;
    /* Typography đặc trưng: Giãn chữ sát nhau -0.01em */
    letter-spacing: -0.01em;
    font-family: var(--font-geist-sans), Arial, Helvetica, sans-serif;
  }

  h1, h2, h3, h4, h5, h6 {
    @apply text-primary;
    letter-spacing: -0.16px;
    font-weight: 600;
  }
}

@layer utilities {
  /* Hiệu ứng nhấn nút scale(0.95) đặc trưng */
  .btn-active-click:active {
    transform: scale(0.95);
    transition: transform 0.2s ease;
  }

  /* Đổ bóng 2 lớp siêu mịn của Starbucks */
  .shadow-brand {
    box-shadow: 0 0 0.5px rgba(0,0,0,0.14), 0 1px 1px rgba(0,0,0,0.24);
  }

  /* Shadow cho các thành phần nổi (Floating) */
  .shadow-float {
    box-shadow: 0 0 6px rgba(0,0,0,0.24), 0 8px 12px rgba(0,0,0,0.14);
  }
}

src/
└── app/
    ├── (shop)/                 # Nhóm có Header/Footer bán hàng
    │   ├── layout.tsx          # Layout chung (Menu, Logo, Giỏ hàng, Footer)
    │   ├── page.tsx            # [/home] - Static/ISR (Trang chủ)
    │   ├── products/           # [/product-list]
    │   │   ├── page.tsx        # SSR (Danh sách sản phẩm, lọc theo category)
    │   │   └── [slug]/         # [/product-detail] - ISR (Chi tiết sản phẩm)
    │   ├── search/             # [/search] - SSR (Kết quả tìm kiếm)
    │   ├── cart/               # [/cart] - Client Component
    │   ├── contact/            # [/contact] - Static
    │   └── about-us/           # [/about-us] - Static
    │
    ├── (auth)/                 # Nhóm layout riêng cho đăng ký/đăng nhập
    │   ├── layout.tsx          # Layout tối giản (Form giữa màn hình)
    │   ├── sign-in/            # [/sign-in]
    │   └── sign-up/            # [/sign-up]
    │
    ├── (customer)/             # Nhóm cho khách hàng đã đăng nhập
    │   ├── layout.tsx          # Layout có thêm Sidebar quản lý tài khoản
    │   ├── my-account/         # [/my-account] - Thông tin cá nhân
    │   ├── my-list/            # [/my-list] - Danh sách yêu thích
    │   └── order/              # [/order] - Lịch sử đơn hàng
    │
    └── layout.tsx              # Root Layout (Chứa HTML, Body, Providers)
```

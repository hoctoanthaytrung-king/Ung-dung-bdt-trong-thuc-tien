
```markdown:PLAN.md
# Kế hoạch thực hiện: Ứng dụng Bất đẳng thức bậc hai trong bài toán thực tiễn

## Định dạng kỹ thuật

Dự án được biên soạn bằng **LaTeX** (cụ thể là trình biên dịch `pdfLaTeX`), vì:

-   Khả năng hiển thị công thức, ký hiệu toán học ở mức độ chuyên nghiệp và chuẩn xác tuyệt đối.
-   Tích hợp mạnh mẽ thư viện `TikZ` và `PGFPlots` để vẽ đồ thị chính xác theo hàm số toán học, tô màu vùng nghiệm trực tiếp trong mã nguồn mà không cần dùng phần mềm đồ họa bên ngoài.
-   Tự động hóa hoàn toàn việc căn lề, giãn dòng, đánh số trang và định dạng các khối lý thuyết (thông qua `tcolorbox`).
-   Mã nguồn dạng text thuần, dễ dàng quản lý phiên bản, lưu trữ và tái sử dụng cho các giáo trình sau này.

## Cấu trúc thư mục dự kiến

Mặc dù dự án hiện tại có thể gộp trong một file `main.tex` duy nhất để tiện biên dịch, thư mục tổng thể được quy hoạch như sau để dễ dàng quản lý và mở rộng:


```

project/
├── main.tex                 # File gốc, chứa khai báo thư viện và gom nội dung
├── sections/                # (Tùy chọn) Thư mục chứa các file con nếu muốn tách file
│   ├── 00-mo-dau.tex
│   ├── 01-chuong1-ly-thuyet.tex
│   ├── 02-chuong2-kinh-te.tex
│   ├── 03-chuong3-giao-thong.tex
│   ├── 04-chuong4-kien-truc.tex
│   └── 05-ket-luan.tex
├── images/                  # Nơi lưu trữ ảnh tĩnh (ví dụ: logo trường)
├── README.md                # Giới thiệu tổng quan dự án
└── PLAN.md                  # Kế hoạch chi tiết này

```

## Quy ước kỹ thuật trong LaTeX

-   **Hộp lý thuyết và định lý**: Sử dụng gói `tcolorbox` với tông màu chủ đạo là xanh dương (`blue!5!white` cho nền, `blue!60!black` cho viền) để làm nổi bật các công thức tổng quát và tính chất hình học.
-   **Trình bày Toán học**: 
    - Dùng ký hiệu `$` cho các công thức ngắn nội tuyến (inline).
    - Dùng môi trường `\[ ... \]` hoặc `align*` cho các phương trình, bất phương trình dài cần biểu diễn từng bước giải.
-   **Đồ họa và Trực quan hóa**: Mọi biểu đồ (quỹ đạo, mặt cắt kiến trúc, hàm lợi nhuận) **bắt buộc** phải dựng bằng lệnh `PGFPlots` (với `compat=1.18`) thay vì chèn ảnh chụp màn hình, nhằm đảm bảo file PDF xuất ra có thể zoom không vỡ nét (chuẩn vector).

## Cài đặt & Biên dịch

Dự án sử dụng trình biên dịch **pdfLaTeX**.
- **Viết trực tuyến (Khuyên dùng)**: Sử dụng [Overleaf](https://www.overleaf.com/). Chỉ cần tạo project mới, copy mã nguồn vào là có thể biên dịch ngay lập tức mà không cần cài đặt môi trường.
- **Cài đặt cục bộ**: Tải bản phân phối LaTeX (TeX Live cho Windows/Linux hoặc MacTeX cho macOS).
- **Biên dịch cục bộ**: Tại thư mục gốc của dự án, mở terminal chạy lệnh:
  
```bash
  pdflatex main.tex
  

```

## Các giai đoạn thực hiện (Khung thời gian: 2 Tuần)

### Giai đoạn 0 — Chuẩn bị hạ tầng (Ngày 1-2)

* [x] Khởi tạo dự án trên Overleaf hoặc môi trường cục bộ.
* [x] Khai báo các gói thư viện cần thiết (`vietnam`, `amsmath`, `geometry`, `tikz`, `pgfplots`, `tcolorbox`).
* [x] Thiết kế layout cơ bản: font size (14pt), khổ giấy (A4), lề chuẩn (trên/dưới 2cm, trái 3cm, phải 2cm).
* [x] Tạo cấu trúc trang bìa với đầy đủ thông tin sinh viên, lớp, tên đề tài.

### Giai đoạn 1 — Soạn thảo Khung lý thuyết nền (Ngày 3-5)

* [x] Viết **Phần Mở đầu**: Xác định tính cấp thiết, mục tiêu và phương pháp nghiên cứu.
* [x] Viết **Chương 1**: Hệ thống hóa lý thuyết về tam thức bậc hai, đồ thị Parabol và định lý xét dấu.
* [x] Áp dụng thử hộp `tcolorbox` cho các định lý và vẽ các Parabol cơ bản minh họa cho các trường hợp $\Delta < 0$, $\Delta = 0$, $\Delta > 0$.

### Giai đoạn 2 — Mô hình hóa & Viết đại trà (Ngày 6-10)

* [x] **Chương 2**: Thiết lập phương trình kinh doanh trà sữa và giải bất phương trình lợi nhuận mục tiêu.
* [x] **Chương 3**: Phân tích bài toán vật lý/giao thông (quỹ đạo cầu lông và khoảng cách phanh xe).
* [x] **Chương 4**: Xử lý bài toán không gian kiến trúc (quy hoạch sân vườn, mái che vòm parabol).
* [x] Đảm bảo logic toán học chặt chẽ: khai báo biến, điều kiện biến, tính Delta, lập bảng/xét dấu, kết luận nghiệm thực tế.

### Giai đoạn 3 — Lập trình đồ họa đồ thị (Ngày 11-12)

* [x] Viết code `PGFPlots` cho đồ thị lợi nhuận kinh doanh, tô màu vùng giá bán an toàn.
* [x] Viết code mô phỏng đường bay của quả cầu qua lưới và biểu đồ ranh giới phanh xe an toàn.
* [x] Vẽ mặt bằng sân vườn và mặt cắt mái che chứa xe tải bằng `TikZ`.

### Giai đoạn 4 — Hoàn thiện & Đóng gói (Ngày 13-14)

* [ ] Rà soát lại lỗi chính tả tiếng Việt.
* [ ] Kiểm tra lỗi tràn lề (overfull hbox) của các công thức toán học dài.
* [ ] (Tùy chọn) Chèn logo trường vào trang bìa nếu có file ảnh.
* [ ] Biên dịch bản PDF cuối cùng và lưu trữ mã nguồn.

## Theo dõi tiến độ từng phần

| # | Nội dung | Trạng thái | Yếu tố đồ họa (TikZ/PGFPlots) |
| --- | --- | --- | --- |
| 0 | Trang bìa & Mở đầu | Hoàn thành | - |
| 1 | Cơ sở lý thuyết | Hoàn thành | ✓ (6 đồ thị nhỏ xét dấu) |
| 2 | Ứng dụng Kinh tế & Tài chính | Hoàn thành | ✓ (1 đồ thị lợi nhuận) |
| 3 | Ứng dụng Thể thao & Giao thông | Hoàn thành | ✓ (2 đồ thị quỹ đạo & phanh xe) |
| 4 | Ứng dụng Kiến trúc & Cảnh quan | Hoàn thành | ✓ (2 sơ đồ mặt bằng & mặt cắt) |
| 5 | Kết luận | Hoàn thành | - |

**Tổng kết:**

* Nội dung: **Trang bìa + Mở đầu + 4 Chương + Kết luận** (Hoàn thành 100%)
* Đồ họa: **11 hình vẽ/đồ thị** được code trực tiếp bằng LaTeX.
* Tiến độ thời gian: Đi đúng lộ trình **2 tuần**.

Trạng thái sử dụng: `Chưa bắt đầu` → `Đang soạn thảo` → `Đang code đồ họa` → `Đang rà soát` → `Hoàn thành`.

## Công cụ hỗ trợ

* **Trình soạn thảo**: Overleaf (Cloud) hoặc VS Code + Extension "LaTeX Workshop" (Local).
* **Tra cứu màu sắc/hộp**: Tài liệu `tcolorbox` manual (CTAN).
* **Tra cứu đồ thị**: Tài liệu `pgfplots` manual để tùy chỉnh trục tọa độ, legend, fill vùng nghiệm.

## Rủi ro cần lưu ý

* **Lỗi biên dịch PGFPlots**: Cú pháp vẽ đồ thị rất khắt khe, thiếu dấu `;` ở cuối lệnh `\draw` hoặc `\addplot` sẽ gây lỗi toàn bộ file. *Giải pháp: Code đồ thị từng bước và biên dịch thử liên tục.*
* **Tràn công thức**: Các phương trình quá dài có thể bị tràn ra ngoài lề phải. *Giải pháp: Dùng môi trường `align*` để ngắt dòng tại dấu `=`. *
* **Lệch phiên bản Package**: Khai báo `compat=1.18` cho PGFPlots là bắt buộc để đồ thị không bị lệch tọa độ so với các phiên bản cũ.

---

## Cập nhật tiến độ mới nhất (21/09/2026)

### Đã hoàn thành

✅ **Nội dung Văn bản & Toán học:**

* Toàn bộ nội dung chữ từ Phần Mở đầu đến Kết luận đã hoàn tất.
* Các công thức tính toán, nghiệm số của bài toán thực tế đã được kiểm chứng logic.

✅ **Hệ thống Đồ họa (Hoàn thành 100%):**

* Đã lập trình thành công toàn bộ đồ thị bằng `TikZ` và `PGFPlots`.
* Vẽ thành công 6 parabol minh họa lý thuyết trong các hộp `tcolorbox`.
* Xử lý thành công việc đánh dấu điểm (mark), vẽ đường nét đứt (dashed) và tô màu vùng nghiệm (fill) cho 4 bài toán thực tiễn.

✅ **Bố cục & Định dạng:**

* Hộp lý thuyết hiển thị đẹp mắt, lề trang được căn chỉnh chuẩn A4.
* Trang bìa đã được thiết kế bố cục chuyên nghiệp.

### Cần làm tiếp (Giai đoạn 4)

🔲 **Hoàn thiện cuối cùng:**

* [ ] Bỏ dấu `%` và chèn đúng tên file logo trường ở trang bìa (nếu cần thiết).
* [ ] Đọc dò lại một lần cuối để bắt các lỗi đánh máy nhỏ (nếu có).
* [ ] Tải file PDF cuối cùng về máy để nộp báo cáo.

```eof


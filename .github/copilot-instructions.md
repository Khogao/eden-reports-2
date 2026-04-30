# Eden Reports — Copilot Instructions

Repo `Khogao/eden-reports-2` (GitHub Pages, branch `main`). Báo cáo Pre-FS / Executive Summary / Executive Summary Short cho dự án **Eden Residential** (An Phú Tây, Bình Chánh, TP.HCM).

## Cấu trúc 2 nguồn

```
d:\Eden\md\                    ← Source of truth (Markdown, KHÔNG thuộc git repo này)
d:\VsCode\eden-reports-2\      ← HTML render (git repo, deploy GitHub Pages)
D:\Eden\html\                  ← Backup local của HTML
```

**12 cặp file MD ↔ HTML** (đặt tên đối xứng):
- `PRE_FS_EDEN_{OG,OG1,V1,V2}` — báo cáo dài
- `EXECUTIVE_SUMMARY_{OG,OG1,V1,V2}` — báo cáo trung bình
- `ESS{OG,OG1,V1,V2}` — báo cáo ngắn

Ngoài ra: `FS_EDEN.html` (interactive financial model), `PROJECT_PLAN_EDEN.html`, `PROJECT_PLAN_EDITABLE.html`, `index.html`.

## Source-of-truth numbers (Eden V2 PA A — giá đất 15 tr/m²)

| Chỉ tiêu | Giá trị |
|---|---|
| Đất quy hoạch | 75.386 m² |
| Sàn CT10 | 222.736 m² (~2.011 căn, hệ số 8×, ~21 tầng) |
| Tổng sàn xây dựng | ~261.000 m² |
| Doanh thu | **14.951 tỷ** |
| Vốn cố định | **6.963 tỷ** = 1.131 (đất) + 3.917 (XD&HT) + 1.915 (CMĐSDĐ NQ87/2025) |
| Tổng chi phí dự án | **8.774 tỷ** = 6.963 + 1.495 (MKT/BH) + 196 (TK&QL) + 120 (PL) — **HOẶC** = 6.963 + 1.811 (BH/TV/QL gộp) trong các bản ngắn |
| EBIT (Lợi nhuận hoạt động, trước lãi vay & thuế) | **6.177 tỷ (41,3%)** |
| LNST | **~4.262 tỷ (28,5%)** |
| Lịch trình | 20 quý Q1/2026 → Q4/2030 |
| Giá đất giả định | 15 tr/m² (giá thị trường) |
| Giá CH giả định | 70 tr/m² |

V1 EBIT: **6.177 tỷ (41,3%)** ở giá đất 15 tr; **6.305 tỷ (42,2%)** ở giá đất 13 tr (PA B).
OG1 LNST ~1.173 tỷ; OG LNST ~703 tỷ.

## Workflow đồng bộ MD ↔ HTML

Khi sửa số liệu hoặc nội dung báo cáo:

1. **Sửa MD trước** ở `d:\Eden\md\<FILE>.md` (source of truth).
2. **Sửa HTML tương ứng** ở `d:\VsCode\eden-reports-2\<FILE>.html` — match nguyên văn.
3. **Verify cross-file consistency**: cùng số phải khớp giữa Pre-FS / ES / ESS cùng phiên bản; cùng phiên bản phải khớp MD ↔ HTML.
4. **Commit + push + backup**:
   ```powershell
   cd D:\VsCode\eden-reports-2
   git add <files>
   git commit -m "fix(<scope>): <mô tả tiếng Việt ngắn>"
   git push origin main
   Copy-Item "<file>.html" "D:\Eden\html\" -Force
   ```
   MD ở `d:\Eden\md\` không thuộc git repo này → chỉ lưu local.

## Verify-before-edit (chống subagent hallucination)

Khi audit dữ liệu qua subagent (Explore) báo "bất nhất":

> **PHẢI verify trực tiếp từng claim trước khi edit.**

Lý do: Explore agent có xu hướng generate "bất nhất giả" để báo cáo phong phú. Trong session trước, 4/4 issues subagent báo đều là hallucination.

Quy trình verify:
1. Lấy claim cụ thể: "file X line Y ghi giá trị A nhưng phải là B".
2. `grep_search` regex chứa số/cụm từ claim trên đúng file.
3. `read_file` đoạn đó kiểm tra nguyên văn.
4. Chỉ sửa nếu claim được xác nhận; nếu không → báo lại user "subagent hallucinated".

## Quy ước nội dung & ngôn ngữ

- **Toàn bộ tiếng Việt** (số dùng dấu chấm phân nghìn, dấu phẩy thập phân: `14.951 tỷ`, `41,3%`).
- "Phương án Gốc" = OG/OG1; "V1" = phương án xin tăng tầng PA A/B; "V2" = phương án điều chỉnh QHCT 1/500 toàn bộ CT10 hệ số 8×.
- "EBIT" = "Lợi nhuận hoạt động (trước lãi vay & thuế)" — annotation rõ ràng trong intro/bảng tổng hợp.
- ESS = bản ngắn (≤100 dòng MD); ES = bản trung bình; PRE_FS = bản dài đầy đủ.

## Lưu ý kỹ thuật

- HTML report dùng inline CSS, không phụ thuộc bundler. `assets/index-*.{css,js}` là build cũ của tool calculator (FS_EDEN), không liên quan các file `.html` static khác.
- `index.html` là landing page liệt kê toàn bộ báo cáo — cập nhật khi thêm file mới.
- Không tạo MD documentation về thay đổi trừ khi user yêu cầu.

# Eden Residential — Báo cáo Tiền Khả thi

Tài liệu nội bộ — phân tích đầu tư dự án Eden Residential, Xã An Phú Tây, Bình Chánh, TP.HCM.

## Xem báo cáo

**Live site:** https://khogao.github.io/eden-reports-2/

## Các phiên bản

| Phiên bản | Mô tả |
|---|---|
| **Gốc (OG)** | Triển khai theo quy hoạch 1/500 hiện hành — chung cư 15 tầng, hệ số SDĐ 3,28× |
| **V1** | Điều chỉnh quy hoạch: toàn bộ CT10 là chung cư, hệ số SDĐ 8× (~21 tầng) |
| **V2** | Phương án đề xuất — cùng quy mô V1, đất giá 15 tr/m², không PA B |

## Cấu trúc file

| File | Nội dung |
|---|---|
| `PRE_FS_EDEN_OG.html` | Pre-FS đầy đủ — Phương án Gốc |
| `PRE_FS_EDEN_V1.html` | Pre-FS đầy đủ — Phương án V1 |
| `PRE_FS_EDEN_V2.html` | Pre-FS đầy đủ — Phương án V2 |
| `EXECUTIVE_SUMMARY_OG.html` | Tóm tắt đầu tư — Phương án Gốc |
| `EXECUTIVE_SUMMARY_V1.html` | Tóm tắt đầu tư — Phương án V1 |
| `EXECUTIVE_SUMMARY_V2.html` | Tóm tắt đầu tư — Phương án V2 |
| `ESSOG.html` | Tóm tắt ngắn — Phương án Gốc |
| `ESSV1.html` | Tóm tắt ngắn — Phương án V1 |
| `ESSV2.html` | Tóm tắt ngắn — Phương án V2 |
| `FS_EDEN.html` | **FS đầy đủ — Khu Dân Cư Ê Đen V2** (mô hình theo quý, S-curve, NPV/IRR/Payback/PI/ROE) |
| `PROJECT_PLAN_EDEN.html` | **Project Plan V2** — Gantt 20 quý, 14 milestones, WBS, RACI, risk register |
| `TEMPLATE_FS_CALCULATOR.html` | Template Pre-FS có Section ⑨ NPV/IRR (tái sử dụng cho dự án khác) |
| `TEMPLATE_FS_FULL.html` | Template FS đầy đủ — 9 sections, mô hình quý (tái sử dụng) |
| `index.html` | Trang điều hướng chính |

## Số liệu chốt — Phương án V2 (Source of Truth)

Các con số dưới đây đã được verify nhất quán giữa **PRE_FS_EDEN_V2 · EXECUTIVE_SUMMARY_V2 · ESSV2 · FS_EDEN · PROJECT_PLAN_EDEN** (kiểm tra 30/04/2026):

### Quy mô
| Chỉ tiêu | Giá trị |
|---|---|
| Diện tích đất trong ranh | **75.386,4 m²** (~7,5 ha) |
| Diện tích tính tiền sử dụng đất | 54.257 m² (~35,3 tr/m² bình quân) |
| Tổng sàn xây dựng CT10 | 222.736 m² (hệ số SDĐ 8×) |
| Sàn thương phẩm căn hộ | **150.852 m²** (~2.011 căn × 75 m²) |
| Sàn thương phẩm TMDV | 12.960 m² |

### Tài chính (tỷ VND)
| Chỉ tiêu | V2 |
|---|---|
| Doanh thu | **14.951** |
| Chi phí mua đất | 1.131 |
| Tiền chuyển mục đích sử dụng đất (NQ 87/2025) | 1.915 |
| Chi phí xây dựng & hạ tầng | 3.917 |
| Chi phí bán hàng & tiếp thị (10%) | 1.495 |
| Tư vấn pháp lý & thủ tục | 120 |
| Tư vấn TK & thẩm tra (3% XD) | 118 |
| Quản lý doanh nghiệp (2% XD) | 78 |
| **Tổng chi phí** | **8.774** |
| **Lợi nhuận hoạt động** | **6.177** (41,3%) |

### Giá bán cơ sở
- Căn hộ: **70 tr/m²** sàn thương phẩm
- Thương mại dịch vụ: 87,5 tr/m² (= 1,25 × giá CH)
- Biệt thự: 150 tr/m²
- Liên kế: 120 tr/m²
- Đất giá vốn V2: 15 tr/m²

### Lịch trình
- Quý bắt đầu: **Q1/2026** · Bàn giao: Q4/2029 · Hết bảo hành: Q4/2030 (20 quý)
- Mở bán đợt 1 sau hoàn thành móng: **Q1/2028** (M8)
- Cất nóc CT10: Q3/2028 (M9) · Nghiệm thu PCCC: Q3/2029 (M10)

### Nhất quán với V1
- Doanh thu V1 = V2 = 14.951 tỷ (cùng quy mô, V2 chỉ thay đổi giá đất → 15 tr/m²)
- Khác biệt OG: doanh thu V2 gấp 1,9× OG (7.823 tỷ); LN HĐ V2 gấp 3,1× OG (1.966 tỷ)

## Quy ước dữ liệu

- **Source of truth**: số liệu Pre-FS V2 → các file khác (ES, ESS, FS, Project Plan) đồng bộ theo đó
- Khi điều chỉnh số liệu: sửa **PRE_FS_EDEN_V2** trước, sau đó cập nhật các file phụ thuộc theo thứ tự: ES → ESS → FS → Project Plan
- **Chủ đầu tư** trong các file công khai: hiển thị `[Bảo mật]`
- Viết tắt (CMĐSDĐ, TMDV, BH&TT, QL, LN HĐ): chỉ OK trong header bảng hẹp; visible text phải viết đầy đủ
- "Phương án" thay cho "Kịch bản" — nhất quán toàn bộ files

> Tài liệu nội bộ — không phát hành công khai.

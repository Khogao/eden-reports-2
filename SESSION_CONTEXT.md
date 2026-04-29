# SESSION CONTEXT — Eden Residential Reports
> Cập nhật: 29/04/2026 (session 3) — Dùng để tiếp nối từ máy khác hoặc session mới

---

## REPO CHÍNH THỨC

| Repo | Trạng thái | URL |
|---|---|---|
| `eden-reports` | 🔒 **ARCHIVED** — read-only, KHÔNG dùng | https://github.com/Khogao/eden-reports |
| `eden-reports-2` | ✅ **ACTIVE** — tất cả công việc đây | https://github.com/Khogao/eden-reports-2 |

**Local:** `D:\VsCode\eden-reports-2\`
**Live site:** https://khogao.github.io/eden-reports-2/

---

## CẤU TRÚC FILE

```
D:\Eden\
  md\
    PRE_FS_EDEN_OG.md         ✅ DONE
    PRE_FS_EDEN_V1.md         ✅ DONE
    EXECUTIVE_SUMMARY_OG.md   ✅ DONE
    EXECUTIVE_SUMMARY_V1.md   ✅ DONE
  html\                        ← SOURCE HTML (chỉnh sửa tại đây)
    PRE_FS_EDEN_OG.html        ✅ DONE
    PRE_FS_EDEN_V1.html        ✅ DONE
    PRE_FS_EDEN_OG1.html       ✅ DONE (OG1 — 15 tr/m² duy nhất)
    EXECUTIVE_SUMMARY_OG.html  ✅ DONE (đã xóa tham chiếu V1)
    EXECUTIVE_SUMMARY_V1.html  ✅ DONE
    EXECUTIVE_SUMMARY_OG1.html ✅ DONE (OG1 — 15 tr/m² duy nhất)
    ESSOG.html                 ✅ DONE (bản tóm tắt ngắn kịch bản Gốc)
    ESSOG1.html                ✅ DONE (bản tóm tắt ngắn OG1)
  image\EXECUTIVE_SUMMARY\     ← Images (không chỉnh)
  scripts\validate_html.py
  .venv\Scripts\python.exe

D:\VsCode\
  eden-reports-2\             ← Git repo chính (clone từ GitHub)
    *.html                     ← Deploy content (copy từ D:\Eden\html\)
    image\
    assets\
  gh-pages-deploy\            ← Worktree cũ (origin2 = eden-reports-2) — dùng phụ
```

---

## PUSH SEQUENCE CHUẨN

```powershell
$env:PYTHONIOENCODING="utf-8"
& d:\Eden\.venv\Scripts\python.exe D:\Eden\scripts\validate_html.py
Copy-Item "D:\Eden\html\*.html" "D:\VsCode\eden-reports-2\" -Force
Set-Location "D:\VsCode\eden-reports-2"
git add -A
git commit -m "<message>"
git push origin main
```

**Lưu ý:** eden-reports-2 main branch = static site content trực tiếp (không qua build step). Push lên main là live ngay sau ~60s GitHub Pages rebuild.

---

## URLS CÁC FILE

- https://khogao.github.io/eden-reports-2/EXECUTIVE_SUMMARY_OG.html
- https://khogao.github.io/eden-reports-2/EXECUTIVE_SUMMARY_V1.html
- https://khogao.github.io/eden-reports-2/PRE_FS_EDEN_OG.html
- https://khogao.github.io/eden-reports-2/PRE_FS_EDEN_V1.html
- https://khogao.github.io/eden-reports-2/ESSOG.html ← bản ngắn kịch bản Gốc
- https://khogao.github.io/eden-reports-2/ESSOG1.html ← bản ngắn OG1 (15 tr/m²)
- https://khogao.github.io/eden-reports-2/EXECUTIVE_SUMMARY_OG1.html
- https://khogao.github.io/eden-reports-2/PRE_FS_EDEN_OG1.html
- https://khogao.github.io/eden-reports-2/ESSV2.html ← bản ngắn V2 (15 tr/m², giả định chốt)
- https://khogao.github.io/eden-reports-2/EXECUTIVE_SUMMARY_V2.html
- https://khogao.github.io/eden-reports-2/PRE_FS_EDEN_V2.html

---

## WORKFLOW TUYỆT ĐỐI

```
Pre-FS MD → ES MD → Pre-FS HTML → ES HTML
```
- MD files = source of truth. Sync HTML theo MD, không ngược lại.
- Chỉnh HTML tại `D:\Eden\html\` rồi mới copy sang repo.
- Chạy validate trước mỗi lần push.

---

## DOS & DON'TS

### ✅ DO
- Chủ đầu tư = `[Bảo mật]` trong tất cả ES files
- Image paths trong HTML: `image/EXECUTIVE_SUMMARY/filename.png` (không có `../`)
- EBIT = trước lãi vay & thuế; LNST = sau lãi vay & thuế 20% TNDN
- Tỷ suất = LNST / Doanh thu (không phải EBIT%)
- Push lên `eden-reports-2` (ACTIVE)

### ❌ DON'T
- KHÔNG push lên `eden-reports` (archived)
- KHÔNG để tên "Công ty Cổ phần Ê Đen" hoặc "94–96 Lê Lai, Quận 1"
- KHÔNG đề cập V1 trong EXECUTIVE_SUMMARY_OG.html (OG ra trước, không biết V1)
- KHÔNG dùng `../image/` (sai path khi deploy ở root)
- KHÔNG gọi là "Lợi nhuận ròng" khi chưa trừ thuế
- KHÔNG dùng "Khu Dân Cư Ê Đen" trong heading (dùng "Eden Residential")
- KHÔNG dùng "OG" làm visible text trong báo cáo → dùng "Kịch bản Gốc" / "kịch bản Gốc"
- OK dùng "OG" trong: CSS class name, filename, backtick code

---

## SỐ LIỆU CỐT LÕI (KHÔNG THAY ĐỔI)

### Kịch bản Gốc OG (giá đất PA A=15 tr/m² / PA B=13 tr/m²):
- DT = 7.823 tỷ
- PA A: EBIT = 1.966 tỷ (25,1%); LNST ≈ 1.173 tỷ (15,0%)
- PA B: EBIT = 2.094 tỷ (26,8%); LNST ≈ 1.275 tỷ (16,3%)
- Sản phẩm: 376 căn hộ + 76 biệt thự + 24 liên kế + VP Lô C

### Kịch bản Gốc OG1 (giá đất 15 tr/m² DUY NHẤT — không có PA B):
- DT = 7.823 tỷ; Chi phí đất = 1.131 tỷ
- EBIT = 1.966 tỷ (25,1%)
- Lãi vay ≈ 500 tỷ; Thuế ≈ 293 tỷ
- LNST ≈ 1.173 tỷ (15,0%)
- Sensitivity: 60tr→9,8% / 65tr→12,5% / 70tr→15,0% / 75tr→17,3% / 80tr→19,4%

### Kịch bản V1 — PA B:
- DT = 14.951 tỷ
- EBIT = 6.305 tỷ (42,2%)
- Lãi vay ≈ 850 tỷ
- LNST ≈ 4.364 tỷ (29,2%)

### Công thức:
- TMDV = 1,25×CH; VP = 0,80×CH
- OG: CH TP=75%; TMDV TP=65%; VP TP=65%
- V1: CH TP=75%; TMDV TP=60%
- LNST = (EBIT − lãi vay) × 0,80

---

## CSS / DESIGN RULES

| Palette | ES (teal) | Pre-FS (amber) |
|---|---|---|
| Accent | `--teal: #1a8a7a` | `--amber: #b87820` |
| Deep | `--deep: #1e2d45` | `--forest: #1a2b1e` |
| Base font-size | 125% | 125% |

- Print CSS: `@media screen{.print-footer{display:none}.print-qr{display:none}}`
- img-plan (QH 1/500) print: `max-height:220mm`, separate rule từ img-gallery

---

## VALIDATE & PDF EXPORT

```powershell
# Validate
$env:PYTHONIOENCODING="utf-8"
& d:\Eden\.venv\Scripts\python.exe D:\Eden\scripts\validate_html.py

# PDF export
$edge = "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe"
& $edge --headless --disable-gpu --print-to-pdf="D:\Eden\pdf\FILENAME.pdf" --print-to-pdf-no-header "file:///D:/Eden/html/FILENAME.html"
```

---

## TRẠNG THÁI (29/04/2026)

| File | Bảo mật | Số liệu | Image path | V1 ref | Status |
|---|---|---|---|---|---|
| EXECUTIVE_SUMMARY_OG.html | ✅ | ✅ | ✅ | ❌ Đã xóa | ✅ OK |
| EXECUTIVE_SUMMARY_V1.html | ✅ | ✅ | ✅ | — | ✅ OK |
| EXECUTIVE_SUMMARY_OG1.html | ✅ | ✅ | ✅ | ❌ Không có | ✅ OK — 15 tr/m² only |
| PRE_FS_EDEN_OG.html | N/A | ✅ | ✅ | — | ✅ OK |
| PRE_FS_EDEN_V1.html | N/A | ✅ | ✅ | — | ✅ OK |
| PRE_FS_EDEN_OG1.html | N/A | ✅ | ✅ | — | ✅ OK — 15 tr/m² only |
| ESSV2.html | ✅ | ✅ | ✅ | — | ✅ OK — 15 tr/m² only |
| EXECUTIVE_SUMMARY_V2.html | ✅ | ✅ | ✅ | — | ✅ OK — 15 tr/m² only |
| PRE_FS_EDEN_V2.html | N/A | ✅ | ✅ | — | ✅ OK — 15 tr/m² only |
| ESSOG.html | ✅ | ✅ | ✅ | ❌ Không có | ✅ OK |
| ESSOG1.html | ✅ | ✅ | ✅ | ❌ Không có | ✅ OK — 15 tr/m² only |

### MD source files (D:\Eden\md\):
| File | Status |
|---|---|
| PRE_FS_EDEN_OG.md | ✅ OK — "OG" → "Kịch bản Gốc" ✅ |
| PRE_FS_EDEN_V1.md | ✅ OK — "OG" → "Kịch bản Gốc" ✅ |
| EXECUTIVE_SUMMARY_OG.md | ✅ OK |
| EXECUTIVE_SUMMARY_V1.md | ✅ OK — "OG" → "Kịch bản Gốc" ✅ |
| ESSOG.md | ✅ OK — không có "OG" visible |
| ESSV1.md | ✅ OK — "OG" → "Kịch bản Gốc" ✅ |
| ESSOG1.md | ✅ NEW — OG1, 15 tr/m² only |
| EXECUTIVE_SUMMARY_OG1.md | ✅ NEW — OG1, 15 tr/m² only |
| PRE_FS_EDEN_OG1.md | ✅ NEW — OG1, 15 tr/m² only |

---

## ĐỂ TIẾP NỐI TỪ MÁY KHÁC

1. Clone repo: `git clone https://github.com/Khogao/eden-reports-2.git D:\VsCode\eden-reports-2`
2. Đọc file này (`SESSION_CONTEXT.md`)
3. Paste nội dung vào đầu chat mới với Copilot
4. Tiếp tục từ bước tiếp theo

# KYC 文档处理工具参考

## 文档转换工具

### MarkItDown（推荐用于文字型文件）

将PDF/DOCX/XLSX/PPTX转换为Markdown文本：

```bash
markitdown 审计报告.pdf > 审计报告.md
markitdown 公司章程.docx > 公司章程.md
```

### Tesseract OCR（用于扫描件/图片）

KYC准入资料中常包含扫描版证件、营业执照、审计报告扫描件等，需OCR处理：

```bash
# 中文OCR
tesseract 营业执照扫描件.jpg stdout -l chi_sim > 营业执照文本.md

# 中英文混合（护照、外资文件）
tesseract 护照扫描件.jpg stdout -l chi_sim+eng > 护照文本.md
```

Python集成：

```python
import pytesseract
from PIL import Image
import os
os.environ['TESSDATA_PREFIX'] = '{TERMUX_PREFIX}/usr/share/tessdata'

# 中文证件
text = pytesseract.image_to_string(Image.open('身份证.jpg'), lang='chi_sim')
# 提取关键字段
for line in text.split('\n'):
    if '姓名' in line or '统一社会信用代码' in line or '地址' in line:
        print(line.strip())
```

## OpenCLI（公开数据辅助）

用于补充公开信息（如通过东方财富查询上市公司行情）：

```bash
opencli eastmoney quote 600519 -f json
```

## 安装验证

```bash
# markitdown
python3 -c "from markitdown import MarkItDown; print('markitdown ok')"

# tesseract + pytesseract
python3 -c "import pytesseract; print('tesseract', pytesseract.__version__)"

# 查看tesseract支持的语言
tesseract --list-langs
```
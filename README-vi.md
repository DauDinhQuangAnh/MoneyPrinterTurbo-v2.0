<div align="center">

# MoneyPrinterTurbo v2.0 💸

### Công Cụ Tạo Video Ngắn Bằng AI Toàn Diện (Open Source v2.0)

Chỉ cần cung cấp <b>chủ đề</b> hoặc <b>từ khóa</b>, hệ thống sẽ tự động viết kịch bản, tìm kiếm/tạo tư liệu hình ảnh & video, tổng hợp giọng đọc AI, tạo phụ đề động, ghép nhạc nền và kết xuất video ngắn chất lượng cao.

[![Python](https://img.shields.io/badge/python-3.11%2B-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

[Tiếng Việt](README-vi.md) | [English](README-en.md) | [简体中文](README.md) | [日本語](README-ja.md)

</div>

> [!NOTE]
> **Open Source & Lời tri ân tác giả gốc:**
> - Dự án này là mã nguồn mở (Open Source) được kế thừa, chuẩn hóa và cải tiến dựa trên dự án gốc tuyệt vời **[MoneyPrinterTurbo của tác giả harry0703](https://github.com/harry0703/MoneyPrinterTurbo)**.
> - Xin gửi lời tri ân chân thành và sâu sắc nhất tới **harry0703** cùng toàn thể cộng đồng đóng góp vì đã tạo nên một nền tảng tạo video AI tự động xuất sắc!

---

## 🖥️ Giao Diện Trực Quan

<h4 align="center">Giao Diện Web (Streamlit WebUI)</h4>

![](docs/webui.jpg)

<h4 align="center">Giao Diện API (FastAPI Swagger Docs)</h4>

![](docs/api.jpg)

---

## ✨ Tính Năng Nổi Bật

1. **Tạo kịch bản thông minh bằng AI (LLM)**:
   - Hỗ trợ đa dạng nhà cung cấp AI: **Google Gemini**, **OpenAI**, **Anthropic Claude**, **DeepSeek**, **Kimi (Moonshot AI)**, **Alibaba Qwen**, **ByteDance Doubao**, **xAI Grok**, **MiniMax**, và chạy offline bằng **Ollama**.
   - Tự động viết kịch bản phân cảnh và trích xuất từ khóa tìm kiếm tư liệu phù hợp.

2. **Chuyển văn bản thành giọng đọc (TTS) đa dạng & tự nhiên**:
   - Miễn phí & chất lượng cao qua **Edge-TTS** (hỗ trợ giọng tiếng Việt cực chuẩn: `vi-VN-HoaiMyNeural`, `vi-VN-NamMinhNeural`).
   - Hỗ trợ Azure Speech, OpenAI TTS, MiniMax, SiliconFlow (CosyVoice, ChatTTS), Google Gemini TTS, VoxCPM hoặc tải lên file giọng thu sẵn.

3. **Nguồn tư liệu Video & Hình ảnh phong phú**:
   - **Kho stock miễn phí**: Pexels, Pixabay, Coverr.
   - **Tạo video & ảnh AI độc quyền**: ByteDance Volcano Engine Seedance, Metaso MiniMax, OFox, MuAPI, OpenAI Image (DALL-E / Flux / SD).
   - Tự động dùng tư liệu video/ảnh có sẵn từ thư mục máy tính (Local).

4. **Phụ đề tự động & Hiệu ứng chữ sống động**:
   - Tự động đồng bộ timeline qua **Faster-Whisper** hoặc mốc thời gian từ Edge-TTS.
   - Hỗ trợ hiệu ứng nhảy chữ (pop_spring), hiển thị từng từ (word-by-word) hoặc từng câu.
   - Tùy chỉnh font chữ, kích cỡ, màu sắc, viền đổ bóng (stroke).

5. **Ghép nối âm thanh & Dựng phim tự động**:
   - Tự động cắt cúp, căn chỉnh tỷ lệ khung hình: **9:16 (Dọc/TikTok/Shorts)**, **16:9 (Ngang/YouTube)**, **1:1 (Vuông)**.
   - Hiệu ứng chuyển cảnh (FadeIn, SlideIn, ZoomIn, Shuffle...) và hiệu ứng chuyển động Ken Burns.
   - Tự động lồng nhạc nền (BGM), tự động hạ âm lượng nhạc nền khi có giọng đọc (ducking).

6. **Đăng video đa nền tảng tự động (Cross-Posting)**:
   - Tự động xuất bản lên **TikTok**, **YouTube Shorts**, **Instagram Reels**, **Facebook Reels**.

---

## 🚀 Hướng Dẫn Cài Đặt & Sử Dụng

### 1. Yêu cầu hệ thống
- **Python**: 3.11 trở lên.
- **FFmpeg**: Đã cài đặt và có trong biến môi trường PATH (hoặc đặt đường dẫn trong file cấu hình).

### 2. Cài đặt các thư viện cần thiết

Khuyến nghị sử dụng công cụ quản lý package hiện đại `uv` hoặc `pip`:

```bash
# Sử dụng pip
pip install -r requirements.txt
```

### 3. Khởi chạy Giao diện Web (WebUI)

Trên Windows:
```bash
webui.bat
```

Hoặc chạy lệnh trực tiếp bằng terminal:
```bash
streamlit run webui/Main.py --browser.serverAddress 127.0.0.1 --server.enableCORS false --server.enableXsrfProtection false
```

Sau khi khởi chạy, mở trình duyệt tại địa chỉ: `http://localhost:8501`.

### 4. Khởi chạy API Server

```bash
python main.py
```
Tài liệu tương tác Swagger UI: `http://localhost:8080/docs`.

### 5. Sử dụng giao diện dòng lệnh (CLI)

```bash
python cli.py --subject "Lợi ích của việc dậy sớm" --video-aspect 9:16 --voice-name vi-VN-HoaiMyNeural-Female
```

---

## ⚙️ Cấu Hình (config.toml)

Sao chép file mẫu `config.example.toml` thành `config.toml`:

```bash
cp config.example.toml config.toml
```

Trong file `config.toml`, bạn có thể nhập các API key tương ứng:
- `language = "vi"`: Ngôn ngữ mặc định giao diện.
- `video_language = "vi-VN"`: Ngôn ngữ kịch bản và giọng đọc mặc định.
- Cấu hình các nhà cung cấp AI LLM (OpenAI, Gemini, Kimi, DeepSeek...) và API key tạo video nếu muốn dùng.

---

## 📄 Giấy Phép (License)

Dự án phát hành theo giấy phép mã nguồn mở **MIT License**.

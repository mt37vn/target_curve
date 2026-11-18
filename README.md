# Target Curve — from Impulse Response

Công cụ web tạo target curve 31 điểm từ file impulse response `.wav`, phục vụ cân chỉnh âm thanh xe hơi với HouseCurve/REW.

Toàn bộ xử lý (đọc WAV, FFT, làm mượt, nội suy) diễn ra trong trình duyệt, không upload file lên server.

## Tính năng

- Kéo thả file impulse response `.wav`.
- Tính RTA bằng FFT và cửa sổ Tukey.
- Làm mượt theo fractional octave: 1/3, 1/2, 1, 2 hoặc 3 octave.
- Chọn cửa sổ IR: 125 / 250 / 500 / 1000 ms.
- Chuẩn hoá tại anchor frequency (mặc định 1000 Hz).
- Giới hạn dải tần số thấp/cao (mặc định 20 Hz – 20 kHz).
- Xuất đúng 31 điểm tần số 1/3 octave theo định dạng text của HouseCurve/REW.
- Sao chép hoặc tải file `.txt` / `.frd`.
- Biểu đồ so sánh RTA và target curve, có self-test.

## Sử dụng

Mở `index.html` trực tiếp trong trình duyệt, hoặc chạy static server:

```bash
python3 -m http.server 8000
```

Sau đó mở <http://localhost:8000>, kéo thả file WAV và tinh chỉnh tham số.

## Cấu trúc

```
index.html          # Ứng dụng chính
deploy/index.html   # Bản deploy trên Netlify
netlify.toml        # Cấu hình Netlify (publish = deploy)
```

## Lưu ý

- Target curve tạo ra là RTA đã làm mượt, chuẩn hoá tại anchor — không phải target curve lý thuyết.
- Nên dùng impulse response đo trong điều kiện thực tế của xe và kiểm tra lại bằng tai nghe trước khi áp dụng.

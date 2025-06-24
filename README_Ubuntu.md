# 🖥️ Ubuntu 4060 GPU Emotion Flask Server

本伺服器整合 Whisper 語音轉文字、Gemini 語意情緒分析、Whisper 語音情緒分析、FER 臉部情緒辨識，並使用 Edge-TTS 合成語音，供 Kebbi Air S 呼叫使用。

---

## 📂 檔案說明

| 檔案 | 說明 |
|------|------|
| server_gpu.py | Flask 主程式，支援 GPU 推論 |
| emotion_module.py | 模型載入與三模態情緒融合邏輯 |
| install_dependencies.sh | 安裝所有依賴的腳本 |
| kebbi_flask.service | systemd 開機自動啟動設定 |

---

## 🛠 安裝與執行步驟

### 步驟 1：安裝套件

```bash
chmod +x install_dependencies.sh
./install_dependencies.sh
```

### 步驟 2：啟動 Flask 伺服器

```bash
python3 server_gpu.py
```

伺服器會監聽在 `http://<你的IP>:5000`

---

## ✅ systemd 自動啟動（選用）

### 步驟 3：設定開機啟動

```bash
sudo cp kebbi_flask.service /etc/systemd/system/
sudo systemctl daemon-reexec
sudo systemctl enable kebbi_flask
sudo systemctl start kebbi_flask
```

---

## ✅ API 路徑

| 路徑 | 說明 |
|------|------|
| `/upload/audio` | 上傳音訊檔 input.wav |
| `/upload/image` | 上傳臉部圖像 face.jpg |
| `/analyze` | 執行三模態情緒融合分析並回傳語音與結果 |
| `/analyze_face_only` | 只分析臉部情緒並回傳標籤與信心值 |
| `/audio_response.mp3` | 語音回應檔案（Edge-TTS 合成） |

---

## 📋 注意事項

- 確保你使用的 GPU 為 NVIDIA 且已安裝 CUDA 驅動
- Whisper 將會自動切換至 GPU 模式（若可用）


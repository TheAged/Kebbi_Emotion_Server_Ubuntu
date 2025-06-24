# 🤖 Kebbi Air S Android Emotion App (Nuwa SDK)

此專案為整合 Nuwa SDK 的 Android 應用程式，具備語音與臉部表情情緒分析功能，並可與後端 Ubuntu GPU 伺服器整合使用。

---

## 📂 專案結構

| 檔案 | 功能 |
|------|------|
| MainActivity.java | 控制錄音、拍照、上傳語音與圖片至伺服器，並播放語音與表情動作 |
| FaceEmotionActivity.java | 拍照並分析臉部情緒，播放對應表情 |
| KebbiUploader.java | 負責將檔案（音檔、圖片）上傳至後端 Flask API |
| AndroidManifest.xml | 權限設定（錄音、相機、儲存空間、網路） |

---

## 🛠 使用步驟

### 步驟 1：開啟專案

1. 打開 Android Studio
2. 選擇 `Open an existing project`
3. 導入 `NuwaSDK_KebbiEmotion_Integrated` 專案資料夾

### 步驟 2：修改伺服器 IP

打開 `MainActivity.java` 和 `FaceEmotionActivity.java`，將以下網址：

```java
"http://<server-ip>:5000"
```

修改為你的 Ubuntu 主機實際 IP，例如：

```java
"http://192.168.50.100:5000"
```

### 步驟 3：編譯 APK 並安裝

1. 點選 `Build > Build APK(s)`
2. 將產生的 APK 複製至 USB 隨身碟
3. 插入 Kebbi Air S 並安裝 APK

---

## ✅ 啟動流程

- `MainActivity`：按下啟動後自動錄音 + 拍照 → 分析情緒 → 播放語音 + 表情動畫  
- `FaceEmotionActivity`：單純表情分析模式（只分析臉部）

---

請確保伺服器已啟動（請參考 Ubuntu 端說明）。

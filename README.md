<div align="center">
  <img src="assets/eggime-icon.png" width="112" height="112" alt="蛋注音 App 圖示">
  <h1>蛋注音 EggIME</h1>
  <p><strong>在 Mac 上，一句話裡就能打注音和英文。</strong></p>
  <p>大千注音・繁體優先・英文 Tab 補全</p>
  <p>
    <a href="https://github.com/J030104/EggIME/releases/latest"><strong>下載蛋注音 v1.0.0</strong></a>
    · <a href="#快速安裝">安裝指南</a>
    · <a href="#日常操作">日常操作</a>
    · <a href="#版本與已知問題">版本與已知問題</a>
  </p>
  <p>Apple silicon（M 系列） · macOS 26 以上</p>
</div>

---

## 打打看

| 想做什麼 | 怎麼打 |
| --- | --- |
| **用大千注音打繁體** | 輸入 `su3cl3`，按 <kbd>Enter</kbd> 送出「你好」。 |
| **在同一句接著打英文** | 中文組字後接著輸入英文。英文部分按 <kbd>Tab</kbd> 接受第一個補全，整句按 <kbd>Enter</kbd> 送出。 |
| **把逗號改成頓號** | 組字時按 <kbd>Shift</kbd> + <kbd>,</kbd> 輸入「，」，再按 <kbd>↓</kbd> 選「、」。 |

候選與送出的文字預設為繁體。中英交界與英文補全後的自動空格預設關閉，可在偏好設定各自開啟。

## 快速安裝

1. 從 [GitHub Releases](https://github.com/J030104/EggIME/releases/latest) 下載 `EggIME-1.0.0-macOS-arm64.zip` 與 `SHA256SUMS.txt`。
2. 核對 SHA-256 並解壓縮。若正在使用舊版蛋注音，先切換到其他輸入法並結束蛋注音。
3. 在 Finder 按兩下解壓縮資料夾內的 `install.command`。更新時會備份舊版 App。
4. 從輸入來源選單選「蛋注音」。若尚未出現，重新登入，再到「系統設定 → 鍵盤 → 輸入方式」加入。

> 安裝包採本機 ad-hoc 簽章，尚未取得 Apple Developer ID 簽章或 Apple 公證。macOS 可能提示安全警告。請先確認下載來源及校驗結果，再依 macOS 畫面處理。

<details>
<summary><strong>核對下載檔、開啟試打視窗與管理資料</strong></summary>

在下載檔與 `SHA256SUMS.txt` 所在的資料夾執行：

```sh
shasum -a 256 -c SHA256SUMS.txt
```

在解壓縮後的資料夾執行以下指令，可開啟獨立試打視窗。各 App 裡的系統輸入法行為仍需在安裝後試用。

```sh
open EggIME.app --args --demo
```

程式安裝於 `~/Library/Input Methods/EggIME.app`，設定、個人詞彙與備份位於 `~/Library/Application Support/EggIME/`。移除時，先切換輸入法並從鍵盤設定移除「蛋注音」，再將 App 移至垃圾桶。個人資料可另外備份或移除。

</details>

## 日常操作

| 按鍵 | 用途 |
| --- | --- |
| <kbd>Enter</kbd> | 送出組字。候選視窗開啟時先確認候選。 |
| <kbd>↓</kbd> | 打開中文詞語、英文補全或組字中的標點候選。 |
| <kbd>Tab</kbd> | 接受英文補全。候選視窗開啟時可展開或收合多欄候選。 |
| <kbd>←</kbd> / <kbd>→</kbd> / <kbd>⌫</kbd> | 移動游標與編輯組字。 |
| <kbd>Shift</kbd> + <kbd>,</kbd> / <kbd>.</kbd> | 輸入全形逗號「，」或句號「。」。 |
| <kbd>Esc</kbd> | 關閉候選視窗。 |

<details>
<summary><strong>偏好設定、句尾標點與本機 AI</strong></summary>

- **繁簡輸出**：從輸入法選單開啟偏好設定，在「進階 → 文字輸出」選擇是否改用簡體。
- **空格**：在「基本設定 → 空格」調整中英文及數字交界的空格，也可獨立開啟英文補全後自動加空格。
- **句尾標點**：標點還在組字中時可按 <kbd>↓</kbd> 回改。想讓一般句號留在組字中，可開啟「句尾標點後繼續保留組字，按 Enter 才送出」。
- **詞彙與候選**：可調整候選視窗與選字鍵，也可管理中英文自訂詞、排除詞與快捷文字。
- **本機 AI**：隨附模型在 Mac 上對既有同音候選評分。

</details>

## 版本與已知問題

**v1.0.0** 是第一個正式版，延續 alpha.5 的中英混打和標點候選。安裝包含中英文詞庫、繁體補充字表與本機 AI 執行環境。 [版本說明與下載](https://github.com/J030104/EggIME/releases/tag/v1.0.0)

- **ChatGPT 英文送出**：曾回報按 Enter 後英文偶發消失，目前仍未重現，原因待查。
- **首次切換輸入來源**：曾出現首輪按鍵直接送出英文字母，仍待調查。
- **相容性**：安裝包以 Apple silicon 與 macOS 26 以上為目標。Intel Mac、舊版 macOS 及各 App 的長時間使用仍待驗證。

<details>
<summary><strong>這版驗證了哪些項目？</strong></summary>

build `2026111901` 通過 118 項自動化測試，涵蓋混打、標點候選替換與取消，以及 30 組英文送出相關情境。已核對 ZIP 完整性、SHA-256、解壓後的 App 簽章及成品自我檢查。自我檢查確認詞庫、模型檔與混打核心，完整的模型推論與各 App 原生輸入仍需另外驗證。

</details>

遇到問題可提供 macOS 版本、App 名稱、重現步驟與實際結果，請先移除私人輸入內容。 [回報問題](https://github.com/J030104/EggIME/issues/new)

## 授權

EggIME 自行撰寫的部分採 [MIT 授權](LICENSE)。字典、模型與執行環境各依原授權，完整公告隨 App 提供。 [第三方授權與來源](THIRD_PARTY_NOTICES.md)

此 GitHub 倉庫提供安裝包及文件。Release 裡 GitHub 自動產生的 Source code 壓縮檔收錄本倉庫的內容，可安裝的 App 請使用獨立的 macOS ZIP。

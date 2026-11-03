# 霓光打磚塊 · Neon Breaker

使用 HTML、CSS 與原生 JavaScript Canvas 製作的打磚塊網頁遊戲。無須安裝套件或編譯，支援電腦與手機。

## 本機遊玩

直接用瀏覽器開啟 `index.html` 即可。

若有安裝 Python，也可在此資料夾執行：

```powershell
python -m http.server 8000
```

接著開啟 http://localhost:8000 。

## 操作方式

| 操作 | 控制 |
| --- | --- |
| 移動板子 | 滑鼠、觸控、左右方向鍵或 A / D |
| 發球 | 空白鍵或點擊遊戲畫面 |
| 暫停與繼續 | P 或畫面上的暫停按鈕 |
| 音效 | 右上角音效按鈕 |

## 遊戲規則

- 每通過一關加 1 分；每次挑戰共有三次生命。
- 球全部掉落才扣除一次生命。
- 後續關卡會增加磚塊硬度、行數並變化排列；硬磚上的數字代表剩餘擊打次數。
- 部分磚塊被擊破後會隨機掉落道具，使用板子接住即可生效。

| 道具 | 效果 |
| --- | --- |
| 多重球 | 額外產生兩顆球，最多同時 9 顆 |
| 加寬板 | 板子加寬，持續 12 秒 |
| 加速球 | 球速變為 1.3 倍，持續 10 秒 |
| 減速球 | 球速變為 0.72 倍，持續 10 秒 |

加速與減速會互相取代；再次取得相同計時道具會重新計時。最高分使用 localStorage 儲存在目前瀏覽器，清除網站資料後紀錄會消失，不會跨裝置同步。Google Fonts 無法連線時會使用系統字型。

## 專案結構

```text
打磚塊/
├── index.html                 # 遊戲頁面
├── style.css                  # 響應式外觀
├── game.js                    # 碰撞、關卡、道具與紀錄
├── README.md                  # 專案與上傳說明
├── .gitignore                 # 排除本機暫存檔
├── .nojekyll                  # 靜態網頁設定
└── .github/workflows/pages.yml # GitHub Pages 自動部署
```

## 上傳到 GitHub

### 使用網頁上傳

1. 在自己的 GitHub 建立新的儲存庫，例如 `neon-breaker`。
2. 使用上傳檔案功能，上傳本資料夾裡的檔案與 `.github` 資料夾，讓 `index.html` 位於儲存庫根目錄。
3. 若檔案總管隱藏了點開頭的檔案，請確認 `.github`、`.gitignore` 和 `.nojekyll` 也有上傳。

### 使用 Git 指令

先建立空白儲存庫，再將最後一行的網址換成自己的儲存庫網址：

```powershell
cd "D:\School\智慧系統\打磚塊"
git init -b main
git add .
git commit -m "新增霓光打磚塊遊戲"
git remote add origin https://github.com/你的帳號/neon-breaker.git
git push -u origin main
```

首次使用 Git 時，若要求設定作者資訊，先執行 `git config user.name "你的名字"` 與 `git config user.email "你的信箱"`，再重新提交。

## GitHub Pages

此專案包含 GitHub Pages 的 Actions 工作流程，只會發布遊戲的三個檔案。

上傳後在儲存庫的 **Settings → Pages → Source** 選擇 **GitHub Actions**。在 **Actions** 頁面手動執行 **Deploy game to GitHub Pages**，或推送新的 `main` 提交。部署完成後，可從 Pages 設定或成功的部署紀錄開啟遊戲。

儲存庫與方案必須支援 GitHub Pages，Actions 也必須啟用。

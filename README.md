# TCNR Website｜貓咪派對一頁式網站

## 專案簡介

本專案是一個以「貓咪派對企劃」為主題的一頁式形象網站，主要練習 HTML、CSS、Bootstrap 與 JavaScript 的整合應用。網站內容包含社群連結、導覽列、輪播圖、服務介紹、派對流程、企業理念、方案介紹、團隊成員、合作資訊、聯絡表單、徵才資訊與會員註冊／登入功能。

此專案屬於前端靜態網站實作，主要目標是練習網頁切版、響應式設計、互動元件、第三方套件整合，以及前端資料儲存與 API 串接。

## 線上展示

GitHub Pages：  
https://jason1596840052026.github.io/TCNR-website/

## 使用技術

### 1. HTML5

本專案使用 HTML5 建立網站的基本結構，將頁面切分成多個 section 區塊，例如：

- `s01`：社群連結
- `s02`：導覽列
- `s03`：首頁輪播圖
- `s04`：品牌與數字介紹
- `s05`：派對流程時間軸
- `s06`：企業精神
- `s07`：主方案介紹
- `s08`：團隊／主持人介紹
- `s09`：合作資訊
- `s10`：聯絡表單
- `s11`：徵才資訊
- `s12`：頁尾連結

透過語意化區塊整理網站內容，使頁面結構更清楚，也方便後續維護與調整。

### 2. CSS3

本專案使用 CSS3 製作自訂視覺風格，包含：

- 背景圖片滿版顯示
- 卡片陰影與圓角
- 漸層色彩設計
- 按鈕 hover 效果
- 圖片縮放與圓角動畫
- 時間軸樣式
- 響應式排版調整

其中 `modern-style.css` 定義主要視覺系統，例如主色、輔助色、陰影、圓角、按鈕、導覽列與各 section 的整體風格。頁面內也使用 `<style>` 補充部分客製樣式，例如輪播圖遮罩、時間軸節點、圖片 hover 效果與手機版文字背景。

### 3. Bootstrap 5

本專案使用 Bootstrap 5 協助完成版面與互動元件，主要應用包含：

- `container`、`row`、`col-md-*` 建立響應式格線系統
- `navbar` 製作導覽列
- `carousel` 製作首頁輪播圖
- `modal` 製作會員註冊與登入視窗
- `btn`、`badge`、`rounded`、`shadow` 等工具類別快速建立樣式
- `d-none`、`d-md-block`、`flex-row-reverse` 等工具類別控制不同裝置上的顯示方式

Bootstrap 讓網站能快速完成基本排版，並降低手寫響應式版面的複雜度。

### 4. Font Awesome

本專案使用 Font Awesome 圖示套件，應用在：

- 社群平台圖示，例如 Facebook、LINE、X、Threads、Instagram、YouTube
- 導覽列品牌圖示
- 按鈕圖示
- 服務項目與內容提示圖示

透過圖示輔助文字內容，可以讓網站畫面更直覺，也提升視覺辨識度。

### 5. JavaScript

本專案使用 JavaScript 處理網站互動功能，包含：

- 初始化動畫套件
- 監聽使用者輸入
- 表單驗證
- 控制 Bootstrap Modal 開啟與關閉
- 處理會員註冊與登入流程
- 操作 DOM 更新畫面內容

JavaScript 主要寫在 `index.html` 底部的 `<script>` 區塊中，讓頁面載入完成後再執行互動功能。

### 6. jQuery

本專案使用 jQuery 簡化 DOM 操作與事件監聽，主要應用包含：

- `$(function(){ ... })` 等待網頁載入完成後執行程式
- `.on("input blur", function(){ ... })` 監聽註冊欄位輸入
- `.click(function(){ ... })` 處理註冊與登入按鈕
- `.val()` 取得表單欄位資料
- `.addClass()`、`.removeAttr()`、`.text()` 更新畫面狀態
- `$.ajax()` 串接外部 API 並將資料加入頁面

jQuery 讓前端互動程式碼更簡潔，也方便操作 HTML 元素。

### 7. AJAX API 串接

本專案使用 jQuery AJAX 串接 Random User API：

```javascript
$.ajax({
    url: 'https://randomuser.me/api/?results=4',
    dataType: 'json',
    success: function (data) {
        data.results.forEach(function (item) {
            // 將 API 回傳的人物資料加入主持人區塊
        });
    }
});
```

此功能會從 API 取得 4 筆隨機人物資料，並動態新增到「特邀主持人」區塊中。這部分練習了前端如何向外部資料來源取得資料，並將資料轉換成 HTML 顯示在頁面上。

### 8. localStorage

本專案使用瀏覽器的 `localStorage` 製作簡易會員註冊與登入功能。

主要流程如下：

1. 使用者在註冊 Modal 輸入帳號、密碼與確認密碼。
2. JavaScript 檢查帳號格式、密碼長度與確認密碼是否一致。
3. 註冊成功後，將帳號資料存入 `localStorage`。
4. 使用者登入時，從 `localStorage` 讀取會員資料並比對帳號密碼。
5. 登入成功後，更新導覽列按鈕文字，顯示「已登入：使用者名稱」。

使用的儲存 key 為：

```javascript
const MEMBER_STORAGE_KEY = "cat_party_members";
```

此功能主要用於前端練習，資料儲存在瀏覽器端，尚未串接後端資料庫。

### 9. CounterUp2 與 IntersectionObserver

本專案使用 CounterUp2 製作數字遞增動畫，並搭配 `IntersectionObserver` 判斷數字區塊是否進入畫面。

應用位置包含：

- 年均派對數量
- 合作貓咪數量
- 安全訓練時數
- 服務據點數量

當使用者滑動到數字區塊時，數字會開始從 0 遞增到設定數值，提升網站的動態感與視覺吸引力。

### 10. WOW.js 動畫效果

本專案使用 WOW.js 製作滾動進場動畫，例如在主視覺區塊中使用：

```html
class="wow animate__bounceInLeft"
```

並在 JavaScript 中初始化：

```javascript
new WOW().init();
```

這讓部分區塊在進入畫面時產生動畫效果，使網站看起來更有互動感。

## 功能介紹

### 首頁輪播圖

使用 Bootstrap Carousel 製作首頁圖片輪播，包含三張貓咪主題圖片、標籤與文字說明，並搭配左右切換按鈕與下方指示點。

### 導覽列

使用 Bootstrap Navbar 製作導覽列，包含品牌名稱、下拉選單、服務項目、會員註冊與會員登入按鈕。手機版會自動收合成漢堡選單。

### 派對流程時間軸

使用 HTML 結構搭配 CSS 偽元素 `::before` 製作垂直時間軸，呈現確認需求、挑選主題、現場佈置與活動執行四個流程。

### 團隊成員區塊

團隊區塊包含固定人物資料，並額外透過 Random User API 動態載入特邀主持人資料。API 回傳後會用 JavaScript 組成 HTML 卡片並加入頁面。

### 會員註冊

使用 Bootstrap Modal 製作會員註冊視窗，並使用 JavaScript 進行即時欄位驗證：

- 帳號需為 4 到 12 個英文字母、數字或底線
- 密碼需為 6 到 20 個字元
- 確認密碼需與密碼一致
- 需勾選同意會員使用說明

註冊成功後，會員資料會被存入 localStorage。

### 會員登入

使用 Bootstrap Modal 製作會員登入視窗，登入時會從 localStorage 讀取會員資料並比對帳號密碼。登入成功後，會更新導覽列狀態，顯示目前登入的帳號名稱。

### 響應式設計

網站使用 Bootstrap Grid 與 CSS media query 處理不同螢幕尺寸的顯示方式。例如在手機版中，部分文字區塊會加上半透明背景，讓文字在圖片上仍然清楚可讀。

## 專案資料夾結構

```text
TCNR-website-main/
├── index.html
├── README.md
├── css/
│   ├── bootstrap.min.css
│   ├── all.min.css
│   ├── modern-style.css
│   └── mycss01.css
├── js/
│   ├── bootstrap.bundle.min.js
│   ├── jquery-4.0.0.js
│   └── wow.min.js
├── images/
│   └── 網站使用圖片素材
└── webfonts/
    └── Font Awesome 字型檔案
```

## 開啟方式

### 方法一：直接開啟

下載專案後，直接使用瀏覽器開啟：

```text
index.html
```

### 方法二：使用 VS Code Live Server

1. 使用 VS Code 開啟專案資料夾。
2. 安裝 Live Server 擴充套件。
3. 對 `index.html` 按右鍵。
4. 選擇 `Open with Live Server`。
5. 使用瀏覽器預覽網站。

## 學習重點

透過本專案，我練習到以下內容：

1. 使用 HTML 建立一頁式網站架構。
2. 使用 Bootstrap Grid 製作響應式版面。
3. 使用 Bootstrap 元件完成 Navbar、Carousel 與 Modal。
4. 使用 CSS 客製化網站主題、色彩、陰影、圓角與 hover 效果。
5. 使用 Font Awesome 增加社群與功能圖示。
6. 使用 JavaScript 與 jQuery 處理表單驗證與互動行為。
7. 使用 AJAX 串接外部 API 並動態產生畫面內容。
8. 使用 localStorage 儲存簡易會員資料。
9. 使用 CounterUp2 與 IntersectionObserver 製作數字動畫。
10. 使用 WOW.js 製作頁面滾動動畫。

## 目前限制與後續改進方向

目前此專案主要是前端練習，因此會員資料只儲存在瀏覽器 localStorage，尚未連接後端伺服器與資料庫。後續可以改進的方向包含：

- 串接後端 API，將會員資料儲存在資料庫
- 增加真正的登入狀態管理
- 補上表單送出功能
- 優化圖片大小，提升載入速度
- 檢查並補齊圖片素材路徑
- 將 JavaScript 從 `index.html` 拆分成獨立檔案，提升維護性
- 增加更多無障礙標籤與 SEO 設定

## 備註

本專案為課程練習與作業用途，主要目的在於展示前端切版、互動功能與第三方套件整合能力。

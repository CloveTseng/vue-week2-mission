# Vue - 第二週作業：使用者登入/註冊

這是一個基於 Vue.js 3 的使用者註冊與登入頁面，為六角學院 Vue.js 課程的第二週作業。

此專案主要練習串接遠端 API，並實作一個基礎的表單驗證與使用者狀態管理功能。

## ✨ 功能特色

*   **使用者註冊:**
    *   可填寫 Email、密碼、暱稱進行註冊。
    *   Email 格式驗證。
    *   密碼長度不得小於 6 個字元。
*   **使用者登入:**
    *   使用已註冊的 Email 和密碼進行登入。
    *   登入成功後會將 token 存入 cookie。
*   **登入狀態驗證:**
    *   頁面載入時會自動檢查 cookie 中的 token，並驗證使用者登入狀態。
    *   成功驗證後會顯示使用者暱稱。

## 🛠️ 使用技術

*   **前端框架:** [Vue 3](https://vuejs.org/)
*   **建置工具:** [Vite](https://vitejs.dev/)
*   **API 串接:** [Axios](https://axios-http.com/)
*   **CSS 框架:** [TailwindCSS](https://tailwindcss.com/)
*   **程式碼規範:** [ESLint](https://eslint.org/), [Prettier](https://prettier.io/)
*   **部署工具:** [gh-pages](https://github.com/tschaub/gh-pages)

## 🚀 如何開始

1.  **複製專案**
    ```bash
    git clone https://github.com/your-username/vue-week2-mission.git
    ```

2.  **進入專案目錄**
    ```bash
    cd vue-week2-mission
    ```

3.  **安裝依賴**
    ```bash
    npm install
    ```

4.  **啟動開發環境**
    ```bash
    npm run dev
    ```

## 📜 可用指令

| 指令 | 描述 |
| :--- | :--- |
| `npm run dev` | 啟動本地開發伺服器 |
| `npm run build` | 建置生產版本的應用程式 |
| `npm run preview` | 在本地預覽生產版本的建置成果 |
| `npm run lint` | 檢查並修正程式碼風格問題 |
| `npm run deploy` | 將 `dist` 資料夾部署到 GitHub Pages |
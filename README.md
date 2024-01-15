# MultiLangVitePressDemo
Run Steps
1. Download file and unzip it.
2. import folder with VSCode
3. Open terminal And run "npm i"
4. run "npm run docs:dev" in terminal
5. You will see the static website

要讓它出現多語系主要要注意幾個地方：
1. .vitepress/config/index.ts 裡面必須包含 locals Object
   每個項目包含 label（顯示在多語系選項上的文字），以及其他設定項目（目前是從 en.ts 與 zh.ts 複寫進來的，詳細原因可以參考 "解構賦值"，但這比較複雜，可以先忽略）
2. en.ts 與 zh.ts 中的 themeConfig 包含 nav 與 sidebar 兩個部分
   其中 nav 表示 "上面的兩個選項"，text 表示顯示的文字，link 表示要導到的頁面，資料夾路徑為絕對路徑
   sidebar 表示左邊顯示的項目，為一個 Object（Key - value）
   重點在他的 Value，裡面有個 base 跟 items
   base 表示 items 裡的 link 都會在前面加上 base 這個前綴，就不用一直重複打了

目前推測問題可能出在 zh.ts 裡面的 sidebar 中，沒有加上 base
可以朝這個方向去研究

P.S. 想要把 en 獨立出來一個資料夾也不是不行，但是會造成首頁會是空的（docs/index.md 必須存在）
如果想要讓 root 重新導向 en 資料夾的話，會需要花費額外的工，所以先不要考慮這個吧！

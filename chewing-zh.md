# GNOME 注音觸控鍵盤

## 相對於預設 OSK 的優點：
 - 功能鍵、修飾符、Tab 和箭頭鍵支持
 - 能夠在螢幕上移動
 - 佈局更緊湊

## 系統需求
 - GNOME 43 或更高版本
 - Wayland（X11 無法正常運作）
 - 已安裝 ```ibus-chdwing``` 或 ```fcitx5``` 或其他注音輸入法

## 安裝
1. 確認您已安裝[ExtensionManager](https://github.com/mjakeman/extension-manager)。
2. 安裝[https://extensions.gnome.org/extension/5949/gjs-osk/](https://extensions.gnome.org/extension/5949/gjs-osk/)
3. 安裝[Block Caribou 36](https://extensions.gnome.org/extension/3222/block-caribou-36/) 以阻止預設的 ​​GNOME OSK。
4. 確保選擇的語言是 QWERTY。
![image](https://github.com/proton-penguin/gjs-osk-chewing/assets/142492829/1c4ff63c-bf76-44e4-aaa3-05d1ada95b0d)
5. 執行以指令來加入注音 Layout 
   ```bash
   cd ~
   git clone https://github.com/proton-penguin/gjs-osk-chewing.git
   rm ~/.local/share/gnome-shell/extensions/gjsosk@vishram1123.com/keycodes.json
   cp ~/gjs-osk-chewing/gjsosk@vishram1123.com/keycodes.json ~/.local/share/gnome-shell/extensions/gjsosk@vishram1123.com/keycodes.json
   rm -r ~/gjs-osk-chewing/
   ```
6. 重新安裝 GJS OSK 來重置設定

## 用法
- 要拖曳鍵盤，請點擊右下角的移動圖標，然後在螢幕上拖曳鍵盤。 若要恢復完整鍵盤，請再次按下移動圖示。
  - 鍵盤將吸附在螢幕的角落、邊緣和中心。
  - 若要變更鍵盤的屬性，請開啟「擴充功能」應用程序，然後按一下此擴充功能下的「設定」以取得可變更屬性的列表
  - 關閉設定對話框以儲存所有修改的設定
  - 若要輸入特殊字符，請開啟 GNOME 設置，然後開啟鍵盤子選單下的「撰寫鍵」。 選擇修飾符（最好是右 alt），然後使用[此處列出的組合鍵](https://en.wikipedia.org/wiki/Compose_key#Common_compose_combinations) 鍵入特殊字符
  - 若要變更鍵盤佈局，請變更 GJS OSK 設定中的佈局
  - 若要新增打字預測，請將「Typing Booster」新增為輸入來源（在GNOME 設定中），並將其選擇為主要輸入來源[(此處為擴充指南)](https://mike-fabian.github.io/ibus-typing-booster/docs/user/)
  - 請注意，即使沒有開啟 OSK，這也會導致預測文字出現，並且必須在 Typing Booster 的設定中設定 Typing Booster 預測的輸入語言
- 若要從命令列（或使用捷徑）開啟鍵盤，請執行命令 ```dconf write /org/gnome/shell/extensions/gjsoskindicator/opened true```，這將開啟鍵盤

## Demo
[Chinese_Demo.webm](https://github.com/proton-penguin/gjs-osk-chewing/assets/142492829/5986bebe-2387-4999-9e71-84559d133729)

[Keyboard Demo.webm](https://user-images.githubusercontent.com/64966832/210458851-1b91adba-f6e4-4d40-b0d5-dba2c46cc354.webm)

[Settings Demo.webm](https://user-images.githubusercontent.com/64966832/210458854-eb458311-3d3f-4edb-93df-f5b8334d4cbc.webm)

## 已知問題/問題和預期功能（希望了解如何修復的解決方案）：
 - 100% 寬度或高度不會佔據整個顯示器寬度或高度（兩側減去 25 像素）。 相反，它會小 1 或 2 像素，具體取決於顯示器尺寸
 - 儘管鍵盤顯示在系統模式上，但它不可交互

## 幫助
 - 如果您發現任何錯誤，或有任何建議，請提出問題或提交拉取請求。 謝謝！

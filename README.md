# ManjaroKDE
學習安裝KDE、常用輸入法

### 安裝fcitx相關package

`sudo pacman -S fcitx-im fcitx-chewing fcitx-table-extra fcitx-configtool fcitx-rime`

* fcitx-im: fcitx + fcitx-qt5
  * fcitx: flexible Xontext-aware Input tool with eXtension
  * fcitx-qt5: fcitx Qt5 IM module
* fcitx-chewing : 注音輸入法
* fcitx-table-extra : 含行列, 倉頡, 大易，嘸蝦米等輸入法之宇碼表，其支援的字碼表細節可參考 Fcitx5-table-extra
* fcitx-configtool : 安裝fcitx圖形管理工具
* fcitx-rime : 安裝rime (rime 為跨平台的中文輸入法框架)

安裝完就請離開終端機，或下指令`sudo reboot`

接這務必要讓你的輸入法，在一開機就啟動，否則你會安裝成功，但是在圖形介面上按ctrl+space仍然打不開拼音輸入。

### 設定讓Manjaro KDE開機，就執行fcitx輸入法
* 請至home目錄下找`.config`資料夾，進入後找`environment.d`資料夾，如果沒有請自行建立。
* 進入`environment.d`資料夾，並建立`fcitx.conf`檔案。
* 使用kate打開`fcitx.conf`檔案，並輸入如下資料。
  ```
     GTK_IM_MODULE=fcitx
     QT_IM_MODULE=fcitx
     XMODIFIERS=@im=fcitx
     SDL_IM_MODULE=fcitx
  ```
* 重新開機讓設定生效。


### 如果遇到新酷音都安裝成功，也安裝完fcitx，但使用ctrl+space就是無法輸入拼音
* 您的系統沒有自動啟動 Fcitx 5 這個框架，所以您的應用程式（例如瀏覽器）不知道要去呼叫哪個程式來處理您的鍵盤輸入，因此才會一直維持在英文輸入狀態。
* 我們之前在終端機中設定環境變數的目的，就是要告訴您的 Manjaro KDE 系統：「嘿，當我登入的時候，請幫我啟動 Fcitx 這個輸入法框架，並讓它負責處理我的輸入。




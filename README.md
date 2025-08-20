# ManjaroKDE
學習安裝KDE、常用輸入法

### <ins>安裝fcitx相關package</ins>

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

### <ins>設定讓Manjaro KDE開機，就執行fcitx輸入法</ins>
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

### <ins>設定值說明</ins>
*  GTK_IM_MODULE=fcitx
   * GTK 是 GNOME、XFCE 等桌面環境廣泛使用的圖形使用者介面（GUI）工具套件。
   * 這個設定值告訴 GTK 應用程式（例如：Firefox、Kate、LibreOffice 等）要使用 fcitx 作為其輸入法模組。
*  QT_IM_MODULE=fcitx
   * QT 是另一套流行的 GUI 工具套件，KDE 桌面環境以及許多應用程式（如 VLC、VirtualBox）都使用它。
   * 這個設定值告訴 QT 應用程式要使用 fcitx 作為其輸入法模組。
*  XMODIFIERS=@im=fcitx
   * XMODIFIERS 是一個古老的 X Window System 環境變數，主要用於指定輸入法。雖然現在的 GUI 工具套件（GTK 和 QT）有自己的設定，但這個變數仍然很重要，可以確保一些舊的或非主流的應用程式也能正常使用輸入法。
   * @im=fcitx 的意思是「im（輸入法）是 fcitx」。
*  SDL_IM_MODULE=fcitx
   * SDL（Simple DirectMedia Layer）是一個跨平台的函式庫，主要用於開發遊戲和多媒體應用程式。
   * 這個設定值確保在使用 SDL 開發的應用程式（例如一些遊戲）中，fcitx 輸入法也能正常運作。    


### <ins>如果遇到新酷音都安裝成功，也安裝完fcitx，但使用ctrl+space就是無法輸入拼音</ins>
* 您的系統沒有自動啟動 Fcitx 5 這個框架，所以您的應用程式（例如瀏覽器）不知道要去呼叫哪個程式來處理您的鍵盤輸入，因此才會一直維持在英文輸入狀態。
* 我們之前在終端機中設定環境變數的目的，就是要告訴您的 Manjaro KDE 系統：「嘿，當我登入的時候，請幫我啟動 Fcitx 這個輸入法框架，並讓它負責處理我的輸入。




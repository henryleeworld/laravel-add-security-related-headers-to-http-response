# Laravel 10 伺服器端回應加入安全相關 HTTP 標頭

引入 bepsvpt 的 secure-headers 套件來擴增伺服器端回應加入安全相關 HTTP 標頭，不需大幅度的修改程式，就可以讓網站與使用者瀏覽器之間有更多的安全防護，因此這個方法是比較簡便可以達成，缺點是這些 HTTP 標頭在比較舊版本的瀏覽器有些是不支援的。

## 使用方式
- 把整個專案複製一份到你的電腦裡，這裡指的「內容」不是只有檔案，而是指所有整個專案的歷史紀錄、分支、標籤等內容都會複製一份下來。
```sh
$ git clone
```
- 將 __.env.example__ 檔案重新命名成 __.env__，如果應用程式金鑰沒有被設定的話，你的使用者 sessions 和其他加密的資料都是不安全的！
- 當你的專案中已經有 composer.lock，可以直接執行指令以讓 Composer 安裝 composer.lock 中指定的套件及版本。
```sh
$ composer install
```
- 產生 Laravel 要使用的一組 32 字元長度的隨機字串 APP_KEY 並存在 .env 內。
```sh
$ php artisan key:generate
```
- 在瀏覽器中輸入已定義的路由 URL 來訪問，例如：http://127.0.0.1:8000。
- 你可以經由 `/` 來進行歡迎畫面瀏覽。
> 如果是要避免 PHP 資訊暴露在 HTTP 標頭中，請將 `php.ini` 裡面的 `expose_php = Off`。

----

## 畫面截圖
![](https://i.imgur.com/js8lyXr.png)
> 過去往往只能被動地防堵瀏覽器的惡意請求，而有了 HTTP 安全相關的標頭，則可以主動控制瀏覽器不發起非安全操作，對安全防護來說，是不小的助益

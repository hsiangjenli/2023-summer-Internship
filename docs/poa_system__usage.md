# 輿情分析系統使用方式

## 點擊 Docker Desktop（一定要開）
> ![](https://github.com/hsiangjenli/2023-summer-internship/blob/master/images/poa_system_usage_1.png?raw=true)

## 至 container 選擇要執行爬蟲程式或是開啟 UI 介面
> ![](https://github.com/hsiangjenli/2023-summer-internship/blob/master/images/poa_system_usage_2.png?raw=true)

- `crawler-n-preprocessing` 爬蟲程式
- `nextjs-ui` UI 介面

爬蟲以及 UI 介面都是要手動開啟才會。沒開啟的時候 Icon 是灰色的。點擊執行按鈕就會執行，隔壁的 ports 如果變成藍色，直接點擊就會進入到 UI 介面。

> ![](https://github.com/hsiangjenli/2023-summer-internship/blob/master/images/poa_system_usage_3.png?raw=true)

> ![](https://github.com/hsiangjenli/2023-summer-internship/blob/master/images/poa_system_usage_4.png?raw=true)

UI 介面能夠正常運作的前提為 mongodb 以及 api 這兩組程式碼有正常運作，也就是都是亮綠燈。



## 資料庫
### `mongodb-ui` 圖形化介面管理 mongodb  

如果想要撰寫更複雜的 query 可以開啟這個程式，它提供一個輕量級的 web-based 管理介面。
> ![](https://github.com/hsiangjenli/2023-summer-internship/blob/master/images/poa_system_usage_5.png?raw=true)

### `mongo-remove-duplicate`  

理論上 `crawler-n-preprocessing` 執行完都會自動刪掉重複的文章，但是如果因為非預期性的關閉執行中的爬蟲，可能會沒有執行到最後刪除重複文章的指令。這時候就可以點擊執行這個按鈕，手動刪除重複的文章。

> ![](https://github.com/hsiangjenli/2023-summer-internship/blob/master/images/poa_system_usage_6.png?raw=true)
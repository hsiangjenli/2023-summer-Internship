# 輿情分析系統使用方式

## 記得放在 `Download` 底下的 `scsb-public-opinion-analysis-platform` 資料夾不要刪掉
因為資料庫的資料是綁在這個路徑底下

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


# 使用小技巧

## 資料庫

### 資料太多
如果覺得資料庫的內容太多，想刪除可以透過 `mongodb-ui` 刪除 

### 資料庫壞掉
如果 `mongodb-ui` 在 docker desktop 裡面的運行 icon 一直不斷的閃橘燈 + `nextjs-ui` 的頁面都沒有正常顯示，代表資料庫的資料出現問題，最簡單的解決方式就是直接把資料刪除

在 `scsb-public-opinion-analysis-platform` 裡面找 `data/mongodb/data` 這個路徑下的資料全部刪掉即可。

## 關鍵字搜尋（特殊寫法）
關鍵字搜尋的部分支援 `正則表達式` 的搜尋規則，比起一般的搜尋引擎提供更彈性的搜尋規則，雖然寫法有些反人類，但是可以將搜尋需求提供給 chatgpt 請他幫你把規則寫出來，下面提供幾個範例。
### 交集
同時出現 `上海` & `數位帳戶`
```python
(?=.*上海)(?=.*數位帳戶)
```

### 特殊規則
範例 1：出現關鍵字 `利率` 同時利率要在 1.5 ~ 1.7 之間（代表內文要出現 `1.5` `1.6` `1.7` 的文字）
```
(?=.*利率)(?=.*1\.[5-7])
```
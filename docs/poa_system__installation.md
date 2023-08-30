# 輿情分析系統安裝方式

## 必裝軟體
1. WSL2
2. Docker

## WSL2 安裝
### Open Control Panel  
### 搜尋 `Turn Windows Features on or off`，然後把下面三個選項選起來
- Virtual Machine Platform
- Windows Hypervisor Platform
- Window Subsystem for Linux

> ![](https://i.imgur.com/h7BWsGf.png)

> ![](https://i.imgur.com/w8krU78.png)

### 使用 power shell 安裝 `wsl --install`
查看有哪寫版本可以安裝
> ![](https://hackmd.io/_uploads/ByYVdPuF2.png)

> ![](https://hackmd.io/_uploads/BJIJHvdKn.png)

### `wsl --install -d Ubuntu-20.04` 目前 `20.04` 支援度比較高
### 點擊 windows 的按鈕就會發現 Ubuntu 裝好了
> ![](https://hackmd.io/_uploads/By-3rw_K3.png)
### 進入 Ubuntu 後，如果發生這個 Error Message 就到[官網](https://aka.ms/wsl2kernel)下載 Linux 核心更新套件
`WslRegisterDistribution failed with error: 0x800701bc`
> ![](https://hackmd.io/_uploads/ryK8HDuKh.png)
### 重新進入 Ubuntu，它會要你先設定帳號、密碼，然後你就可以在 windows 上跑 Ubuntu 了
![](https://hackmd.io/_uploads/ryP5PD_th.png)

## Docker Desktop
到官網下載 [Docker Desktop](https://www.docker.com/products/docker-desktop/)，下載完就可以使用了。

# 重新部屬程式
在本資料夾，按右鍵開啟在終端機，並且在終端機貼上該指令即可重新部屬

![Image](https://i.imgur.com/dD8zMBo.png)
![Image](https://i.imgur.com/twsCsiW.png)

```
docker compose up --build --force recreate
```

## 重建成功
可以至 docker desktop 裡的 container 裡看是否有順利建成功
# 數位出版聯盟有聲書範本

符合W3C[有聲書](https://www.w3.org/TR/audiobooks/)規格製作，另參考[出版品宣告](https://www.w3.org/TR/pub-manifest/)。

- 製作者：董福興

-----

## 作品

- 標題：[前進](https://zh.m.wikisource.org/zh-hant/前進)
- 作者：賴和
- 封面圖片：[賴和紀念碑](http://cls.lib.ntu.edu.tw/laihe/A/a_05.htm)（彰化城鄉局攝影）

## 錄音資訊

- 配音員：張心哲（鏡好聽聲音主播）
- 錄音室：[GBH Studio](https://www.facebook.com/gbhstudiotw/)
- 剪接師：Kevin Chen

-----

## 範本說明：

### Case1 具備所有元素的有聲書範本

- 包括：

    - 出版品宣告: `publication.json`
    - 主要進入頁面（內嵌目錄）: `index.html` 
    - 獨立目錄: `toc.html`
    - 封面圖片: `cover.jpg`
    - 對應時間: `sync/forward.json`
    - 文字內容: `html/forward.html`

- 說明：

在主要進入頁面(Primary Entry Page)中，以`link`元素包含對出版品宣告(Publication Manifest)publication.json的參照。然後在出版品宣告中提供閱讀順序(`readingOrder`)與音檔位置，在閱讀順序中使用`alternate`指定對應同步朗讀時間的forward.json檔案。

在forward.json中的`text`指定標註同步ID的html/forward.html檔案。

封面圖片、主要進入頁面、獨立目錄與文字內容另宣告在出版品宣告的資源(`resources`)中。

### Case2 使用獨立目錄的有聲書範本

- 說明：

與Case1大致相同，不同之處是在主要進入頁面中不提供嵌入目錄，而連結到獨立目錄。處理方式為在`resources`中，將`"rel": "contents"`指定到獨立目錄，而非Case1的主要進入頁面。

### Case3 簡單有聲書範本

- 包括：

    - 出版品宣告: `publication.json`
    - 獨立目錄: `toc.html`
    - 封面圖片: `cover.jpg`
    - 音檔: `forward.mp3`

- 說明：

相較於Case1,2，比較偏向於一般包裝有聲書作為交換使用。音檔不位於遠端伺服器，而位於本地端，同時也沒有主要進入頁面，程式應該直接搜尋出版品宣告進行處理。也不包含同步旁白資源。

### Case4 簡單有聲書範本的輕量化封裝

- 說明：

使用[輕量化包裝格式](https://www.w3.org/TR/lpf/)的.lpf檔案，內容物與Case3相同。

輕量化包裝格式採用ZIP壓縮，但聲音與影片等檔案不進行壓縮。處理.lpf檔案時，程式需直接搜尋出版品宣告`publication.json`及主要進入頁面`index.html`來進行處理。

### Case5 最小限度的有聲書範本

- 包括：

    - 出版品宣告: `publication.json`
    - 封面圖片: `cover.jpg`
    - 音檔: `forward.mp3`

最小限度的有聲書範本，連獨立目錄也不具備。僅提供出版品宣告與音檔，甚至可以進一步刪除封面圖片。

-----

| 範本編號 | 封裝 | PEP        | 獨立目錄（TOC） | 同步旁白 | 資源狀態 |
| -------- | ---- | ---------- | --------------- | -------- | -------- |
| 1        | 否   | 內嵌目錄   | 有              | 有       | 遠端     |
| 2        | 否   | 不內嵌目錄 | 有              | 有       | 遠端     |
| 3        | 否   | 無         | 有              | 無       | 本地     |
| 4        | LPF  | 無         | 有              | 無       | 本地     |
| 5        | 否   | 無         | 無              | 無       | 本地     |





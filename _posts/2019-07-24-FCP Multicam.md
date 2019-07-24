---
layout: post
title: Final Cut Pro 10.4 多機剪輯
categories: FCP
order: 1
---

介紹多個鏡頭的剪輯，搭配之前的剪輯 SOP，你將會看到我如何完成這次的演唱會影片，只能說是這根本是自虐的過程。這篇文章不在於教學，主要是分享整個過程，進而了解為何剪支影片需要兩三個禮拜的時間。

<!-- more -->

[工作環境](#工作環境)
[素材整理](#素材整理)
[鏡頭粗剪](#鏡頭粗剪)
[畫面處理](#畫面處理)
[特效處理](#特效處理)
[輸出檔案](#輸出檔案)
[片尾處理](#片尾處理)
[字幕工程](#字幕工程)

<iframe width="560" height="315" src="https://www.youtube.com/embed/siJhGhVdPGo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# 工作環境
在開始之前，先介紹我的軟硬體設備以及作業流程 SOP。

軟硬體設備參考：

* 硬體：MacBook Pro 13，CPU 2.4G i5，Memory 8G。
* 作業系統：MAC OS Mojave 10.14.5
* 軟體：FCP 10.4
* 外接 256 GB SSD (主要 FCP Library 會跑在上面，由於只有剪輯影片時才需要額外這麼大的空間，所以其實不需要升級 MacBook 的空間，有需要再外接 SSD 就好了，可以省一點錢XD)
* 外接 1 TB HDD (主要存放搜集來的素材，以及匯出最後的影片，這部分是容量需求，而非速度。)

每個人的作業流程可能都不太一樣，你也不一定要跟我一樣，最重要的是如何建立屬於自己的 SOP。

剪輯SOP參考：

1. 搜集素材檔案放到 1 TB 的 HDD。
2. New Library on SSD。
3. New Project。
4. New Keyword Collection
5. Import Media：選擇 **Proxy media** (Proxy media 負責低流量；Optimized media 負責高畫質)。
6. 開始剪輯
7. 輸出影片：
    * View —> Optimized/Original
    * File —> Share —> Master File
    * Setting —> Video Codec : ProRes 422 LT or ProRes 422

由於演唱會的影片太長了，為了更專注在每個畫面，所以採用 divide and conquer 的方式一首歌一首歌慢慢的剪輯，然後再利用疊加的方式慢慢合併成最後的演唱會影片，除了可以減少一次 import 過大的檔案外，也可以設立多個 milestone，以防止剪輯過程出了什麼差錯而需要全部重來，這種狀況真的會讓人崩潰啊～

# 素材整理
第一步當然是先搜集所有素材，越齊全越好，所以HDD的容量就很重要，至少要 1 TB 才能裝得下所有影音素材啊！我之前會把素材都放在 HDD，然後再 import media，但後來發現如果 SSD的容量許可的話可以直接 copy 所有素材到 SSD 上面直接剪輯也不錯，這時候 HDD 上面的素材就成了備份，以防 SSD 上面的素材出了什麼差錯，畢竟這些素材都是很珍貴的啊！

* *影片合併*：由於這次素材被分割成多個 2 GB 大小的檔案，因此如果要剪輯的目標歌曲片段被分割成兩個檔案，則需要先合併檔案，否則等等做影音同步的時候會發生無止盡的等待，因為他會找不到這兩個連續的檔案，相同的 audio pattern，相信我，我曾經等了一個晚上，四個小時。
* *素材分類*：按照上面的 SOP 將素材 import 進來後，我利用四機或是五機的名稱作為 keyword collection 的名稱：觀眾、center、left、right、動態。
* *片段選取*：選取五機的目標歌曲片段，並且加上 keyword 。
* *同步處理*：如果是多機影片，但是同一時間只想出現其中一機的畫面的話，選取「New Multicam Clip」。如果想要同一時間出現多機畫面的話，選取「Synchronize Clips」。

# 鏡頭粗剪

# 畫面處理

# 特效處理

# 輸出檔案

# 片尾處理

# 字幕工程


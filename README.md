長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
library(rvest)
```

    ## Warning: package 'rvest' was built under R version 3.3.3

    ## Loading required package: xml2

    ## Warning: package 'xml2' was built under R version 3.3.3

``` r
pttResult<-NULL
for(n in 1:6){
indexno = 5300-n
url<-paste0("https://www.ptt.cc/bbs/movie/index",indexno,".html")
pttContent<-read_html(url)
post_title <- pttContent %>% html_nodes(".title") %>% html_text()
post_pushNum<- pttContent %>% html_nodes(".nrec") %>% html_text()
post_author<- pttContent %>% html_nodes(".author") %>% html_text()
pttMovie<-data.frame(title=post_title,pushNum=post_pushNum,author=post_author)
pttResult<-rbind(pttResult,pttMovie)
}
```

爬蟲結果呈現
------------

``` r
#這是R Code Chunk
knitr::kable(pttResult)
```

| title                                                            | pushNum | author       |
|:-----------------------------------------------------------------|:--------|:-------------|
| \[情報\] 2017 北美4~6月上映電影列表                              | 15      | ooic         |
| \[好雷\] 我和我的冠軍女兒-以父威對抗體制                         | 7       | nosweating   |
| \[多部雷\]那些有血有肉的超級英雄們                               | 11      | LIPOYI       |
| \[選片\] 攻殼機動隊VS美女與野獸                                  | 24      | a85405       |
| \[問片\] 好朋友相約結婚                                          | 3       | purist       |
| Re: \[情報\]越南景甜破尺度主演【嚇女的誘惑】HD高畫質中文電影預告 |         | andey        |
| (本文已被刪除) <t4937054>                                        | 3       | -            |
| \[普雷\]一路順風－天亮了，我們繼續走。                           | 1       | guangpiano   |
| (本文已被刪除) <t4937054>                                        |         | -            |
| \[負雷\] 攻殼機動隊                                              | 5       | arrakis      |
| \[討論\] (Cinefix)十大不靠對話的電影                             | 6       | peter220     |
| \[請益\] 笑到流淚的戲劇                                          | 45      | chan520cc    |
| \[討論\] 浩劫重生 查克被救起來的過程?                            | 14      | Rajon        |
| \[負雷\] 金剛戰士中二重開機版...                                 | 2       | uus          |
| Re: \[討論\] 景甜真的很雷嗎？                                    | 5       | shinbird     |
| \[影評\] 聞天祥評 / 黑色追緝令                                   | 8       | MyAll        |
| Re: \[好雷\] 目擊者的疑問與想法                                  |         | arrakis      |
| (本文已被刪除) \[a80568911\]                                     |         | -            |
| (本文已被刪除) \[a80568911\]                                     |         | -            |
| \[討論\] 皮克斯《可可夜總會》(Coco) 狗狗午餐短篇                 | 1       | SKnight      |
| \[好雷\] 最後一頁，最恐怖－目擊者                                | 3       | ueiwei       |
| \[請益\] 自己一個人適合看這片嗎QQ?                               |         | NiNiHOT      |
| \[好雷\] 白雪公主殺人事件                                        | 16      | kurama1984   |
| \[新聞\] 好消息！以後電影上映45天網路上就看得到                  | 5       | jay5566      |
| \[討論\] marvel是不是沒                                          |         | justempty    |
| \[情報\] 《異形：聖約》片段預告                                  | 2       | Tristan0918  |
| \[片單\] 請推薦不限種類好看電影，我也推薦一下                    | 12      | koisppq      |
| (本文已被刪除) \[jay5566\]                                       |         | -            |
| \[請益\] 療養怨的小問題                                          | 3       | alista       |
| \[輕微雷\]攻殼機動隊腦粉簡短觀影心得                             | 8       | ahhway       |
| \[好雷\] 聲之形                                                  | 2       | nerv3890     |
| \[討論\] 《玩命鎗火》導演欲拍攝殭屍版漫威電影！                  |         | jay5566      |
| \[微好雷\]金剛戰士Power Rangers勾起滿滿回憶!                     | 1       | fullmetalyao |
| Re: \[討論\] marvel是不是沒                                      | 5       | LOLI5566     |
| \[普好雷\] 她們的顫慄故事(陸譯:女劫)-XX                          |         | LF25166234   |
| \[討論\] 最喜歡的「西遊」電影？                                  | 16      | kiradu       |
| \[問片\] 嬰兒殺父母的恐怖片                                      | 14      | amx2131      |
| \[新聞\] 湯姆克魯斯5月訪台　四度來台破紀錄！                     | 39      | jay5566      |
| \[情報\]《銀魂》真人電影片場劇照                                 | 69      | jay5566      |
| \[普雷\] 目擊者故事好但不算好的懸疑片                            | 4       | signm        |
| \[討論\] 景甜真的很雷嗎？                                        | 23      | jimmy9991    |
| \[討論\] 明天我要和昨天的妳約會聖地巡禮                          | 18      | thjyrsj      |
| \[新聞\] 北美週末:寶貝老闆稱霸, 美女野獸居次                     | 21      | lovemelissa  |
| \[好雷\] 目擊者-流暢的國片!!(買電影票要小心!!)                   | 18      | stoneJ       |
| \[情報\]【4/1(六) 台北單日電影票房粗估 】                        | 21      | ss30066      |
| \[問片\] 一部俄羅斯兄弟到美國發展的電影                          | 5       | Ga1axyNote7  |
| Re: \[新聞\] 北美週末:寶貝老闆稱霸, 美女野獸居次                 | 3       | senria       |
| Re: \[討論\] 景甜真的很雷嗎？                                    | 2       | bill1478963  |
| \[普雷\]目擊者                                                   | 3       | nothing188   |
| \[普雷\]攻殼機動隊 have no ghost in the shell                    | 11      | brioche      |
| \[ 好雷\] 寶貝老闆 出乎意料的好看！                              | 5       | TCPai        |
| \[好雷\] 明天，我要跟昨天的妳約會                                | 2       | QoHyacinthoQ |
| \[ 超好雷\] 目擊者 誰殺了XX                                      | 4       | lingary      |
| \[好雷\] 攻敵必救                                                | 15      | emip         |
| (本文已被刪除) <h2030625>                                        | 56      | -            |
| (本文已被刪除) \[LD0123\]                                        |         | -            |
| \[情報\]越南景甜破尺度主演【嚇女的誘惑】HD高畫質中文電影預告     | 3       | jas1123kimo  |
| \[好雷\] 目擊者的疑問與想法                                      | 7       | green741s    |
| \[微好雷\] 救殭清道夫                                            |         | flowgo       |
| \[吐雷\] 不吐不快之攻殼機動隊2017                                | 14      | lordyamato   |
| \[好雷\] 我和我的冠軍女兒 這片必看                               | 17      | stock5566    |
| \[LIVE\] X戰警天啟Apocalypse 猩猩台手剝21:00                     | 爆      | pttnowash    |
| \[新聞\] 周星馳太孤獨…找林允聊天                                 | 7       | jay5566      |
| \[普好雷\] 攻殼機動隊                                            | 3       | m19871006    |
| \[問片\] 今天狂新聞裡的電影片段                                  | 2       | archvalkyrie |
| \[問片\] 今天出來狂新聞開計程車                                  | 9       | a4839821     |
| \[好雷\] 單身動物園 The Lobster                                  | 35      | ownr         |
| (本文已被刪除) \[jay5566\]                                       |         | -            |
| \[請益\] 想請教魔女嘉莉原著和電影有差很多嗎                      | 26      | qwer04230423 |
| \[討論\] 孫儷加盟張藝謀三國新片擔任女主角！！！                  | 34      | jay5566      |
| \[好雷\] 目擊者-時間暫停的意義？                                 | 2       | zzz499       |
| \[好雷\] 聲之形～無法傳達的內心吶喊                              |         | paulyear     |
| \[片單\] 聰明縝密的犯罪者有好結果                                | 48      | NTUlosers    |
| \[ 好雷\] 另人耳目一新的目擊者                                   | 19      | a3696786     |
| \[討論\] 想聊聊蓋皮爾斯Guy Pearce這個演員                        | 60      | SpkSpawn     |
| \[不算有雷的雷\] The Quiet Passion 寂靜的激情                    |         | Ruthcat      |
| \[片單\] 無神論者被排擠的片?                                     | 6       | kyouya       |
| \[請益\] \[有雷\] 冠軍女兒的真實故事                             | 6       | endurant     |
| \[情報\] 《神鬼傳奇》最新預告 震撼登場                           | 67      | SKnight      |
| \[好雷\] 冥中注定我愛你 - 黃姵嘉好漂亮                           | 5       | SuperSg      |
| \[贈票\] 玩命關頭8 4/11特映會                                    | 4       | ck980417     |
| \[老雷\] 《鋼琴教師》真神作也                                    | 25      | Leika        |
| \[討論\] Angelababy                                              | 21      | kiradu       |
| \[普無雷\] 愛有來世 The Doscovery                                | 3       | biboga       |
| \[贈票\] 東京影展最佳影片《昨日盛開的花朵》贈票                  | 47      | pelicula     |
| \[請益\] 請問瘋狂麥斯是cyberpunk嗎？                             | 11      | pketam       |
| \[影展\] 4/5(三) 怪奇地下電影大賞【粉紅色水仙】                  |         | victorway    |
| \[新聞\] 那些年我們放棄的角色！12位婉拒演知名                    | 53      | go190214     |
| \[討論\]關於絕命鈴聲這部片                                       | 6       | gyfatz       |
| \[好雷\] 虎父無犬女———冠軍女兒                                   | 10      | takumixnobu  |
| Re: \[請益\] 請問瘋狂麥斯是cyberpunk嗎？                         | 98      | LOLI5566     |
| \[好雷\] 目擊者觀後感－意義深刻的笑話(有雷)                      | 18      | freeeedoom   |
| \[普雷\] 聲之形                                                  | 6       | kirktyler    |
| (本文已被刪除) <huanglove>                                       |         | -            |
| \[超好雷\] 低調的好動畫 聲之形                                   | 4       | dakkk        |
| Re: \[討論\]關於絕命鈴聲這部片                                   |         | gyfatz       |
| \[好雷\]《目擊者》- 兩好三壞安全上壘                             | 10      | jk10134      |
| \[請益\] 《聲之形》一個細節求解(有電影+漫畫雷)                   | 7       | larrybear    |
| \[新聞\] 凱文費吉談《復仇者聯盟》的沙威瑪片段                    | 8       | qn123456     |
| \[好雷\] 當他們認真編織時-超渡煩惱                               | 1       | immad        |
| \[普雷\] 點評《漫漫回家路》/微雷                                 |         | KACIRIE      |
| \[普好雷\] 目擊者 好但不會看第二次                               | 20      | cappa        |
| \[普雷\] 點評《絕境之南》：想贖罪，就留下來                      |         | KACIRIE      |
| \[ 算好雷\] 攻殼機動隊                                           | 19      | cw56983      |
| \[ 問片\] 眼前的壞人不是壞人                                     | 2       | a1322313     |
| \[新聞\] 最強老爸喪妻8年「聽見她說話」　如戲人                   |         | huanglove    |
| Re: \[討論\] 玩命關頭紅在哪                                      | 18      | Kobe2630     |
| \[問片\] 提到校園霸凌的同志電影                                  | 16      | itwitb       |
| 〔LIVE〕CINEMAX 太陽帝國                                         | 3       | HellKitty    |
| \[討論\] 【安娜貝爾：造孽】中文官方預告 釋出                     | 31      | MyAll        |
| \[請益\] 本能寺大飯店vs生日卡片                                  | 13      | baozi0329    |
| \[普雷\] 雙生姊魅 Let Her Out                                    |         | mysmalllamb  |
| (本文已被刪除) \[vincentgotu\]                                   |         | -            |
| \[普雷\] 描寫生動的寶貝老闆                                      | 5       | blacktooth   |
| \[選片\] 攻殼vs金剛vs異星智慧                                    | 37      | AE35         |
| \[新聞\] 蘇有朋 《嫌疑人》打趴好萊塢片 一夜捲2.                  | 12      | huanglove    |
| \[好雷\] 目擊者                                                  | 20      | innocent8675 |
| \[普雷\]《生日卡片》，做自己人生中的主角。                       | 2       | a122239      |
| \[好雷\] 我和我的冠軍女兒 Dangal                                 | 31      | BMay         |
| \[普雷\] 嫌疑犯X的獻身(中國版)                                   | 14      | kmwace       |

解釋爬蟲結果
------------

``` r
str(pttResult[1])
```

    ## 'data.frame':    120 obs. of  1 variable:
    ##  $ title: Factor w/ 116 levels "\n\t\t\t\n\t\t\t\t(本文已被刪除) [a80568911]\n\t\t\t\n\t\t\t",..: 11 4 3 15 10 18 2 12 2 5 ...

執行str(pttResult\[1\])，pttResult\[1\]用來取pttResult的第一個欄位，也就是標題 結果為:'data.frame':118 obs. of 1 variable，代表這次執行結果總共有118篇文章 (根據時間不同，文章數量可能會變動)

``` r
maxPost<-max(table(pttResult$author,exclude="-"))
for(m in 1:(length(table(pttResult$author)))){
  if(((table(pttResult$author))[[m]])==maxPost)
    print((table(pttResult$author))[m])
}
```

    ## jay5566 
    ##       6

先用table找出每個作者的貼文總數，再用max取最大值("-"代表已刪除貼文，要排除在外) 再用迴圈找貼文數和maxPost一樣的作者，並print出名字和貼文數，結果為jay5566，總共6篇貼文 (根據時間不同，結果可能會不同)

經過這次的爬蟲結果得出以下結論:

1.最近的新片攻殼機動隊和國片目擊者討論度很高 2."贈票"的文章推文數都很多 3.大部分都是討論好萊塢片，其他地區的電影討論度不高

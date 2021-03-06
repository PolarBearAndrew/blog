title: CleanCode 無瑕的程式碼 (上篇)
date: 2017-02-05 22:55:10
categories: Code要好好寫
thumbnail: /images/books/CleanCode_thumbnail.jpg
tags:
- 讀書心得
- 程式設計
- 重點筆記
- 心得分享
---

無瑕的程式碼，其實是我第二次詳細閱讀這本書。第一次是在大學一年級，剛開始寫程式的我根本完全看不懂書中在寫什麼啊！每字每句話都能看懂，卻完全無法理解意義或是體悟到任何的道理，丟在書架上幾年後，工作之餘再重新看了一次。這次感觸良多，有些是我犯過的錯，有些對我來說是重要的警告。總之，我認為這是一本程式設計師必讀的書，說是學習一種新的知識或是撰寫技巧其實並不精確，個人覺得是幫助自己釐清撰寫程式碼時的思考、自我反省的一本書。看完這本書仍然取決於我們自己要改變多少做事的風格。

![無瑕的程式碼 CleanCode](/images/books/CleanCode.jpg)

作者：Robert C. Martin
譯者：戴于晉、博碩文化
審校：陳錦輝
出版社：博碩文化

[CleanCode 無瑕的程式碼 (下篇)](/2017/02/05/20170205_BOOKS_CleanCode1-2/)

*****

為什麼需要花時間維程式碼的整潔？真正的"無瑕"的程式碼的定義是什麼？在第一章節作者給了一個大概的方向：無暇程式碼就是在追求程式碼的表達能力，且沒有任何一個流派是絕對正確的。維護整潔的程式碼，不僅僅是程式設計師對於專業的自我要求，也是在日益龐大的系統開發中，迫切需要重視的問題。或許在小型的專案中我們能仰賴記憶力、猜測、或是一些經驗推導來維持整個專案的運作。隨著團隊的人數擴增、專案程式碼行數的成長、甚至單純是客戶的要求朝三暮四的變化，整潔的程式碼開始成為必要的開發條件，不論是實質上的效率問題，甚至是影響到日後的修改、維護，缺乏整潔觀念的程式碼必然會帶來一場災難。

# 整潔程式碼的第一步

討論變數命名、函數、註解、程式碼編排等等細節的技巧，在這部分我在學生時期就有特別在注意，但往往沒有相當明確的方向與見解，以下綜合書中的資訊和我在職場前輩身上學到的智慧，大致整理成以下幾個重點：

<!--more-->

### 排版、正確註解

排版和正確語意的註解是相當基本的東西，基本除了不要亂雷別人之外，沒有什麼爭議問題。最需要討論的應該就是註解的量，有些開發者會相當仰賴註解把事情說清楚，而另一派的開發者認為，當前開發的語言幾乎都是高階語言了，我們透過變數和函數的命名就應該將事情說明清楚。我個人是支持後者的說法，在工作經驗中也是比較偏向後者的作風。註解只用來補足某些程式碼無法陳述的部分而已，嘗試更精確地名命、重構程式碼才是正確的整潔方式。

而註解掉的廢棄程式碼則是完全不應該出現的，刪除時應當對程式碼負責。總之，這是版本控管的事情了，他本身就不應該留在那邊。註解下來的程式碼，只會變成永遠的殘存程式碼放在那邊而已，而沒有人敢去刪除它，留著他感覺很重要，但是註解掉就代表不需要了。

### 不要白目、避免自己犯錯

不論是常數、變數、函數甚至類別命名等，最重要的事情是如實的反應內容，當然擁有很多命名的規則，或是慣用的習慣，但最大的重點是忠實的反應實際上的內容。同時不要使用無意義的命名：諸如 `tmp`, `data` 這些命名其實是我在學生時期撰寫程式碼常用的，當然因為我多半是一個認自己寫，我總是知道 `tmp` 我多半用在拆解資料，`data` 通常我用在 API 或是函數回傳的資料。但真正的主因是學生時期的系統往往不太複雜，就算我繳交過最複雜的幾個 APP 和選課系統，往往都是瀑布式開發，一次完成的。命名最大的影響在於：當我們回頭看自己的程式碼時。當我們回頭追尋問題、修改功能、甚至是看別人的程式碼時，這些無意義的命名將會造成很大的影響，問題小則浪費時間，大則用錯變數、重疊使用變數，造成交叉感染。當然白目的命名就更不可取了 `magicNumber`、`justDoThis()` 等，當我們自己在撰寫時可能覺得情投意合，完全表達了我們想表達的狀況，但往往會造成更多的誤導。

而在命名的選擇中，需要仔細的衡量 "完全表達內容" 和 "避免贅述"，並且找到適當的平衡點，不要一昧的把變數名稱拉長來完整描述狀況，適當即可。何謂適當？我自己認為這就是專業的 Developer 和 Programer 之間的第一個差距，在龐大的組織中會針對開發做細節的規範，但如果只會死板地遵循規範，不應該是一個稱為智力型工作者的 Developer 該有的樣子。

### 函數即映射

這是在前一份工作的前輩指點，幾個月前的自己對於函數命名犯下許多錯誤，但當時並不知覺，在之後雷到自己。`函數即映射` 很明確的指出，每個函數的名稱應該正確的描述自己內部的行為，同時可推導出 pure function 的觀念，一個操作或是一個動作，就是一個函數，片段的函數在組合包裝成更大的功能，層層包裝之中，必須分工明確，這樣才能完整地描述整件事情的操作流程。這其中有一個相當重要的觀念需要注意，函數不應該有副作用，超出預期功能的函數並不會比較方便，而是製造更多的麻煩而已。

### 善用物件及資料結構來表達

類似於封裝的觀念，了解物件真正要做的事情是什麼，完整的命名後打包，正確的封裝來避免外界的干擾，同時也是減少對外界傳達不必要的資訊。而針對 Node.js 在這部分的觀念，個人認為重點是善用第三方套件，用大家熟機的套見就像使用物件一樣，將程式更明確的語易化，而熟悉的套件功能，也減少了閱讀程式碼的成本，更明確的闡述一切。舉例套件 `lodash`，lodash中友需許多多已經包裝好的片段功能，協助我們取出資料、整理資料等等，很多功能其實也只要單純一兩個迴圈加上幾個if便可以完成，但在不考慮效能的情況下，第三方套件會比自己撰寫的迴圈來得更語意明確。

### 層層的錯誤處理

錯誤處理是大型型系統開中最重要的環節，在中後期開發或是功能橋接的階段，不可避免的事面對各種錯誤，而如何尋找出錯誤，除了仰賴工程師自己的技巧之外，透過錯誤處理系統正確的承接錯誤的來源也相當重要，正確的定義每個錯誤，避免整個系統只使用少數幾個甚至一個錯誤包裝。先前我覺得全域是的承接錯誤很方便很帥，結果在系統開發中後期造成了不少的困擾。當然逐層追回仍然能解析出來錯誤真正的原因，但是在每個承接錯誤的地方加上註記，或許會來得更好。

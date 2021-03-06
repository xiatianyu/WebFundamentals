project_path: /web/_project.yaml
book_path: /web/fundamentals/_book.yaml
description:改善網頁的無障礙功能

{# wf_updated_on:2018-03-09 #}
{# wf_published_on:2016-06-26 #}

# 無障礙功能 {: .page-title }

{% include "web/_shared/contributors/megginkearney.html" %}
{% include "web/_shared/contributors/dgash.html" %}
{% include "web/_shared/contributors/aliceboxhall.html" %}
{% include "web/_shared/contributors/robdodson.html" %}

本文是 [Udacity 無障礙功能課程](https://www.udacity.com/course/web-accessibility--ud891){: .external }中所涉及部分內容的文字版本。但其並非視頻課程的直接文字記錄，而是旨在以課程原有內容爲基礎，對無障礙功能的原理和實踐進行更簡要的論述。

### TL;DR {: .hide-from-toc }

- 瞭解無障礙功能的含義及其對網絡開發的作用。
- 瞭解如何讓所有人都能訪問和使用網站。
- 瞭解如何在儘量減小開發影響的情況下加入基本無障礙功能。
- 瞭解提供了哪些 HTML 功能以及如何利用它們來改善無障礙功能。
- 瞭解在打造美觀的無障礙體驗時一些高級無障礙功能技巧的相關內容。

瞭解無障礙功能及其範圍和影響可令您成爲更出色的網絡開發者。
本指南旨在幫助您瞭解如何才能讓所有人都能訪問和使用您的網站。

儘管“Accessibility”（無障礙功能）難以拼寫，卻不一定難以實現。
在本指南中，您將瞭解如何通過一些速效方法以最少的工作量幫助改善無障礙功能，如何才能利用 HTML 的內置功能打造更加強健並具有更佳無障礙功能的界面，以及如何充分利用一些高級技巧來打造美觀的無障礙體驗。

您還會發現，其中的許多技巧幫助您打造的界面所帶來的滿意度和易用性提升並非僅僅適用於殘障人士，而是適用於*所有*用戶。

當然，許多開發者對無障礙功能含義的理解還很模糊（不就是與政府合同、檢查清單和屏幕閱讀器有關的功能嗎？），也流傳着許多有關它的誤解。例如，許多開發者認爲，處理無障礙功能問題就是強迫他們在打造賞心悅目的體驗與粗鄙醜陋但具有無障礙功能的體驗之間做出選擇。

當然，實際情況根本不是這樣，因此讓我們先澄清這個問題，然後再進入正題。
無障礙功能有何含義？您可以通過本文了解它的哪些相關內容？

## 什麼是無障礙功能？

一般來說，當我們說某個網站具有無障礙功能時，我們的意思是網站的內容可用，並且毫不誇張地講，其功能可由*任何人*操作。作爲開發者，您會輕易地認爲所有用戶都能看見和使用鍵盤、鼠標或觸摸屏，並且與網頁內容的交互方式也與您相同。這會造成一些人能夠獲得良好的體驗，其他人則會遇到從簡單煩惱到重大障礙的各種問題。

那麼，無障礙功能就是指這樣一類用戶的體驗，他們可能不在“典型”用戶這一狹窄範圍之內，並且與網站的訪問或交互方式異於常規。具體地講，它所涉及的用戶具有某種身體缺陷或殘障（切記這種體驗可能具有非生理性或暫時性）。

例如，儘管我們在探討無障礙功能時往往是圍繞身體有缺陷的用戶，但實際上都能將其與我們使用的界面由於其他原因而無法訪問的經歷聯繫起來。您是否曾在手機上使用桌面版本網站時遇到問題？是否看到過“您所在地區不提供該內容”消息？或者是否在平板電腦上找不到熟悉的菜單？這些都屬於無障礙功能問題。

隨着瞭解的深入，您會發現在這種更廣泛、更普遍意義上解決無障礙功能問題幾乎總能讓所有人的用戶體驗得到改善。

讓我們來看一個例子：

![一個無障礙功能不佳的表單](imgs/pooraccess.jpg)

這個表單存在幾個無障礙功能問題。

- 文本對比度低，這會讓弱視用戶難以閱讀。
- 將標籤置於左側而將字段置於右側會讓許多人難以將它們關聯起來，也會讓需要進行放大的人幾乎無法使用頁面；想像一下，如果您在手機上看到這個畫面，並且需要來回平移才能搞明白標籤與字段的關聯，會有多麼鬱悶。
- “Remember details?”標籤未關聯複選框，因此您只得點按或點擊那個小方框，而不能直接點擊標籤；此外，使用屏幕閱讀器的用戶會難以弄清楚關聯問題。

現在讓我們揮一揮無障礙功能魔棒，看看解決上述問題後的表單。我們將要完成的工作是：將文本的顏色加深；修改設計，讓標籤靠近它們所標示的字段；以及修正標籤，使其與複選框關聯起來，以便點擊標籤同樣可以進行狀態切換。

![一個改善了無障礙功能的表單](imgs/betteraccess.jpg)

您更願意使用哪一個？如果您說的是“無障礙版本”，就表明您正在試圖瞭解本指南的一個主要前提。
給少數用戶構成徹底阻礙的問題往往也是許多其他用戶面臨的痛點，因此如果解決了無障礙功能問題，就能讓所有人的體驗得到改善。

## 網絡內容無障礙功能指南

本指南通篇都會提到[網絡內容無障礙功能指南 (WCAG) 2.0](https://www.w3.org/TR/WCAG20/){: .external }，這一套由無障礙功能專家編輯的指南和最佳做法旨在有系統地闡述“無障礙功能”的含義。實際上，有若干國家在其網絡無障礙功能法律要求中明令，必須使用這些指南。

WCAG 圍繞四大原則進行組織，通常使用首字母縮寫詞 *POUR* 來稱呼這些原則：

- **可感知**：用戶是否能感知內容？這有助於我們緊記這一點：僅憑可通過一種感官（例如視覺）感知內容並不能斷定所有用戶都能感知。

- **可操作**：用戶是否能使用 UI 組件和在內容中導航？例如，需要懸停交互的內容無法由不能使用鼠標或觸摸屏的用戶操作。

- **可理解**：用戶是否能理解內容？用戶能否理解界面，以及其一致性是否足以避免產生混淆？

- **強健**：內容是否能被多種 User Agent（瀏覽器）使用？
    它是否能與輔助技術協作？

儘管 WCAG 提供了無障礙內容含義的全面概覽，可能還會讓人覺得有點不知所措。
爲幫助緩解這種壓力，[WebAIM](http://webaim.org/){: .external }（網絡無障礙功能思維）小組將 WCAG 指南提煉成了一份易於遵循的檢查清單，專以網絡內容爲目標。

[WebAIM 檢查清單](http://webaim.org/standards/wcag/checklist){: .external }以高屋建瓴的方式簡要介紹了您需要實現的內容，同時還在您需要擴展定義時提供了底層 WCAG 規範的鏈接。

有這個工具在手，您就可以爲自己的無障礙功能工作制定方向，並堅信只要項目達到規定標準，用戶就能在訪問您的內容時獲得良好的體驗。

## 瞭解用戶的多樣性

在瞭解有關無障礙功能的內容時，瞭解世界上用戶的多樣性以及影響他們的無障礙功能主題的種類會有幫助。爲做進一步說明，請看一看下面這段包含豐富信息的問答對話，問答的對象是 Victor Tsaran 這位全盲的 Google 技術項目經理。

<figure class="attempt-right">
  <img src="imgs/victor_tsaran.jpg" alt="Victor Tsaran">	
  <figcaption>Victor Tsaran</figcaption>
</figure>

<hr>

> *您在 Google 從事什麼工作？*

我在 Google 的工作是幫助確保我們的產品適用於各類多樣化用戶，無論他們是否有身體缺陷或殘障。

> *用戶存在哪些類型的身體缺陷？*

當我們思考哪些類型的身體缺陷會讓用戶難以訪問我們的內容時，許多人的頭腦中立即會出現我這樣盲人用戶的畫面。沒錯，這種身體缺陷的確會令用戶難以甚至無法使用大量網站。

許多現代化的網絡技術都有一個令人遺憾的副作用，那就是使用它們創建的網站對盲人用戶訪問網絡時使用的工具兼容性不佳。不過，實際上無障礙功能並非只侷限在這一方面。我們發現，將身體缺陷視爲分成視覺、運動、聽覺和認知這四大類很有幫助。

> *下面我們逐一瞭解這四類缺陷。您能否舉出一些視覺缺陷的例子？*

視覺缺陷可以分爲幾個類別：像我這樣的無視力用戶可以使用屏幕閱讀器、盲文或結合使用這兩者。

<figure class="attempt-right">
  <img src="imgs/braille-reader.png" alt="一臺盲文閱讀器">	
  <figcaption>一臺盲文閱讀器</figcaption>
</figure>

現在，完全沒有任何視力實際上相當罕見，但您認識或遇到至少一位全盲者的機率還是很高的。不過，還存在着數量龐大得多的所謂弱視用戶。

這一羣體的覆蓋範圍很廣，既包括我的妻子這樣沒有任何角膜的人（儘管她能看到東西的大致輪廓，卻難以閱讀印刷文字，在法律上會被視爲盲人），也包括因視力很差而需要配戴高度數處方眼鏡的人。

這是個龐大的羣體，因此這一類別人羣使用的視覺調節自然種類多樣：一些人使用屏幕閱讀器或盲文顯示器（我甚至聽說過有一位婦女閱讀顯示在屏幕上的盲文，因爲這些盲文比印刷文字更容易看清），他們也可以使用不含完整屏幕閱讀器功能的文字語音轉換技術，使用可對屏幕進行局部放大的屏幕放大鏡，或者直接使用瀏覽器縮放來增大字號。他們還可以使用高對比度方案，例如操作系統高對比度模式、高對比度瀏覽器擴展程序或網站的高對比度主題背景。

<figure class="attempt-right">
  <img src="imgs/high-contrast.png" alt="高對比度模式">	
  <figcaption>高對比度模式</figcaption>
</figure>

許多用戶甚至組合使用上述視覺調節，比如我的朋友 Laura，她就組合使用了高對比度模式、瀏覽器縮放和文字語音轉換技術。

弱視會涉及到許多人。首先，隨着年齡增長，我們都會經歷視力減退的情況，因此即使您沒有親身經歷，也很有可能聽到過父母對此的抱怨。但許多人都會有這樣沮喪的經歷：在一扇灑滿陽光的窗戶旁拿出一臺筆記本電腦時，卻突然發現自己什麼也看不清！或者任何接受了激光手術或可能就是需要看清房間對面內容的人，他們可能就使用過我提到的某種視覺調節。因此，我認爲開發者體現對弱視用戶的同情不難做到。

對了，我不該忘了提及顏色視覺低下的羣體，要知道，約有 9% 的男性具有某種形式的顏色視覺缺陷！
此外還有 1% 的女性也存在這種缺陷。
他們可能難以區分紅色和綠色，或黃色和藍色。請在您下一次設計表單驗證時考慮這一因素。

> *有哪些運動缺陷的例子？*

沒錯，運動缺陷，或者說是靈巧性缺陷。這一羣體的範圍既包括可能是由於受到 RSI 或類似損傷，害怕疼痛而不願意使用鼠標的用戶，也包括身體癱瘓以及某些身體部位運動範圍受限的用戶。

<figure class="attempt-right">
  <img src="imgs/eye-tracking.png" alt="一個使用眼球追蹤設備的人">	
  <figcaption>一臺眼球追蹤設備</figcaption>
</figure>

運動缺陷用戶可以使用鍵盤、開關設備、語音控制甚至眼球追蹤設備來與計算機進行交互。

與視覺缺陷類似，運動缺陷也可能屬於暫時性或情境性問題：
可能是您使用鼠標的手腕部骨折。也可能是筆記本電腦的觸控板損壞，或者您搭乘的火車運行不穩。
用戶的機動性可能在許多情況下受到妨礙，我們可以通過確保滿足這些情況下的用戶需求來改善總體體驗，無論是具有永久性缺陷的用戶，還是發現自己暫時無法使用基於指針 UI 的用戶，他們的體驗都能得到改善。

> *很好，讓我們談一談聽力缺陷吧。*

這一羣體的範圍可能包括深度耳聾者直至弱聽者。我們的聽力往往會隨年齡增長而衰退，這與視力很相似。
我們之中有許多人會使用助聽器之類的常見輔助裝置來幫助自己。

<figure class="attempt-right">
  <img src="imgs/screen-captions.png" alt="一臺底部顯示有字幕的電視">	
  <figcaption>屏幕字幕</figcaption>
</figure>

對於聽力受損的用戶，我們需要確保不能依賴聲音，因此務必要使用視頻字幕和文字記錄之類的東西，並在聲音是界面的組成部分時提供某種替代項。

正如我們在視覺和運動缺陷部分見識到的，想像出聽力正常的人同樣受益於這些調節的情形真的很容易。我的許多朋友都說他們很喜歡配有字幕和文字記錄的視頻，因爲這意味着即使他們身處一個開放式辦公室，又沒有攜帶耳機，仍然可以觀看視頻！

> *好了，您能給我們講點有關認知缺陷的例子嗎？*

認知疾病有許多種（例如注意力缺陷障礙、失讀症和孤獨症），這可能意味着這些人想要或需要以不同方式獲取信息。
面向這些羣體的調節自然極其多樣，但我們無疑發現了這些調節與其他領域發生了重疊，例如使用縮放功能來簡化閱讀或注意力集中。此外，這些用戶還會發現，真正的極簡式設計效果最好，因爲它能最大限度減少注意力分散和認知負荷。

我認爲每一個人都能切身體會認知超載的壓力，因此顯而易見的是，如果我們打造的體驗適合認知缺陷者，我們就會致力於打造能夠令所有人滿意的體驗。

> *那麼，您會怎樣總結自己對無障礙功能的理解？*

如果您審視一下人類可能具有的各種能力和殘障，就會發現讓設計和構建的產品只適合視力、聽力、靈巧性和認知能力健全者使用似乎思慮極欠周詳。這幾乎是在自取失敗，因爲我們打造的體驗對所有人而言壓力更大、合用性不足，並且對部分用戶而言，打造這樣的體驗實際上是將他們完全排除在外。

<hr>

在這次訪談中，Victor 提到了多種缺陷，並將它們分成四大類：*視覺*、*運動*、*聽覺*和*認知*。
他還指出，每一種缺陷都可能是*情境性*、*暫時性*或*永久性*缺陷。

讓我們看一些訪問缺陷實例，瞭解它們分屬其中的哪些類別和類型。
請注意，一些缺陷可能歸屬多個類別或類型。

<table>
  <tr>
    <th></th>
    <th>情境性</th>
    <th>暫時性</th>
    <th>永久性</th>
  </tr>
  <tr>
    <th>視覺</th>
    <td></td>
    <td>腦震盪</td>
    <td>失明</td>
  </tr>
  <tr>
    <th>運動</th>
    <td>懷抱一個嬰兒</td>
    <td>手臂骨折、RSI*</td>
    <td>RSI*</td>
  </tr>
  <tr>
    <th>聽覺</th>
    <td>嘈雜的辦公室</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th>認知</th>
    <td></td>
    <td>腦震盪</td>
    <td></td>
  </tr>
</table>

*重複性勞損：例如腕管綜合徵、網球肘、扳機指

## 後續步驟

我們已經取得了不錯的進展！您已閱讀了以下方面的內容：

- 什麼是無障礙功能以及爲什麼說它對所有人都很重要
- WCAG 和 WebAIM 無障礙功能檢查清單
- 您應該考慮的不同類型缺陷

在指南的其餘部分，我們將深入介紹創建無障礙網站的實用層面。
我們的介紹將圍繞以下三大主題領域進行組織：

- [**焦點**](/web/fundamentals/accessibility/focus)：我們將瞭解如何構建可使用鍵盤替代鼠標進行操作的界面。
    這當然對運動缺陷用戶很重要，但同時也要確保您的 UI 能給所有用戶帶來良好體驗。

- [**語義**](/web/fundamentals/accessibility/semantics-builtin)：我們將確保以能夠兼容各種輔助技術的強健方式表達我們的用戶界面。

- [**樣式設置**](/web/fundamentals/accessibility/accessible-styles)：我們將以視覺設計爲例，瞭解一些能夠讓界面的視覺元素儘可能靈活合用的技巧。

由於上述每一個主題都能構成一個完整的課程，因此我們不會對創建無障礙網站的每一個層面進行介紹，
而是會爲您提供足夠的入門信息，併爲您推薦一些不錯的資源，讓您能夠深入瞭解各主題的相關信息。

<!-- title: 紐結理論 -->
<!-- category: notes -->
<!-- tags: math, topology -->
<!-- published time: 2023/09/06 -->

# 紐結理論 (Knot theory)

---

## 參考資料

* [Veritasium - How The Most Useless Branch of Math Could Save Your Life](https://youtu.be/8DBhTXM_Br4?si=wH7gK8Qd4Eo-VDKY)
* [維基百科 - 素紐結](https://zh.wikipedia.org/zh-tw/%E7%B4%A0%E7%BA%BD%E7%BB%93)
* [維基百科 - 紐結理論](https://zh.wikipedia.org/zh-tw/%E7%B4%90%E7%B5%90%E7%90%86%E8%AB%96)
* [維基百科 - 素紐結列表](https://zh.wikipedia.org/zh-tw/%E7%B4%A0%E7%B4%90%E7%B5%90%E5%88%97%E8%A1%A8)
* [維基百科 - 拓撲異構酶](https://zh.wikipedia.org/zh-tw/%E6%8B%93%E6%92%B2%E7%95%B0%E6%A7%8B%E9%85%B6)

---

## 術語中英對照

|中文|英文|
|---|---|
|平凡紐結|Unknot|
|三葉紐結|Trefoil|
|八字紐結|Figure-eight knot|

## 素紐結 (Prime knot)

* 不可分解且不為`平凡紐結`的紐結

## 複合紐結 (Composite knot)

* 將多個素紐結相連接後的紐結

## 紐結表 (knot table)

* 以紐結結構按照交點數目所排列成的表
* 常以`亞歷山大-布里格斯符號`作為其中各結構的表示代號

## R變換 (Reidemeister moves)

* 用於表示紐結變換過程的變換操作
* 其變換動作分別為
	1. R1 Twist  
	將單一邊進行扭轉，或由扭轉狀態解開
	2. R2 Poke  
	將兩邊相互交疊，或由交疊狀態分離
	3. R3 Slide  
	將其中一個邊滑過另外兩個邊的交疊處
* 若一紐結可以透過`R變換`形成另一紐結，則該二紐結相等

## 三色性 (Tricolorability)

* 規則
* `三色性`在`R變換`下的變化
	1. Twist  
	多出1個單色交點
	2. Poke  
	多出2個三色交點
	3. Slide  
	3個三色變為2個三色、1個單色
* 以三色性來區別`平凡紐結`與`三葉紐結`
	> `平凡紐結`是單色的，而`三葉紐結`則可上色成三種顏色  
	> 因此可區別此二結為不同的結
* `三色性`的規則僅能用於區分叉數為3以下的結，叉數超過便會有顏色不夠用的問題  
進而發展出`P色性`的分類規則

## P色性 (P-colorability)

* 「P」可為2以外的任何質數
* 規則
	1. 必須使用兩種以上的數字
	2. 兩條下方線的數字相加除以P後的餘數必須與兩倍上方線數字除以P後的餘數相同  
	$(b_1 + b_2)\%p = 2t\%p$

在`P色性`之下，`八字紐結`可著色成`(0, 1, 4, 3)`的五色性結，即可與`平凡紐結`的「不著色」做出區分

## 亞歷山大多項式

* 1923年，早於`R變換`
* 規則
	1. $A(Unknot) = 1$
	2. 可以對於單一交點進行「`Forward (fwd)`、`Backward (bwd)`、`Separate (sep)`」等變換，  
	並得到$A(fwd) - A(bwd) + (t^{1/2} - t^{-1/2})A(sep) = 0$的關係式

使用這樣的規則就可以得到
$$
\begin{equation}
\begin{aligned}
	&A(Unknot) - A(Unknot) + (t^{1/2} - t^{-1/2})A(Unlink) = 0\\
	&\Rightarrow 1 - 1 + (t^{1/2} - t^{-1/2})A(Unlink) = 0\\
	&\Rightarrow A(Unlink) = 0
\end{aligned}
\end{equation}
$$
$$
\begin{equation}
\begin{aligned}
	&A(Hopf\ link) - A(Unlink) + (t^{1/2} - t^{-1/2})A(Unknot) = 0\\
	&\Rightarrow A(Hopf\ link) - 0 + (t^{1/2} - t^{-1/2}) = 0\\
	&\Rightarrow A(Hopf\ link) = -t^{1/2} + t^{-1/2}
\end{aligned}
\end{equation}
$$
$$
\begin{equation}
\begin{aligned}
	&A(Trefoil) - A(Unknot) + (t^{1/2} - t^{-1/2})A(Hopf\ link) = 0\\
	&\Rightarrow A(Trefoil) - 1 + (t^{1/2} - t^{-1/2})(-t^{1/2} + t^{-1/2}) = 0\\
	&\Rightarrow A(Trefoil) = t - 1 + t^{-1}
\end{aligned}
\end{equation}
$$

## 瓊斯多項式

* 1984年
* 規則
	1. $A(Unknot) = 1$
	2. 可以對於單一交點進行「`Forward (fwd)`、`Backward (bwd)`、`Separate (sep)`」等變換，  
	並得到$t^{-1}V(fwd) - tV(bwd) - (t^{1/2} - t^{-1/2})V(sep) = 0$的關係式
* HOMFLY多項式  
$lP(fwd) - l^{-1}P(bwd) + mP(sep) = 0$

## Perko對

* $10_{162}knot = 10_{161}knot$
* `十叉結`數量從166個修成165個

## 第二型拓撲異構酶 (Type II topoisomerase)

* 一種異構酶，能使DNA長鏈斷裂與接合  
過程是將一條DNA雙股螺旋上的兩股DNA皆切斷，使另一條雙股螺旋能夠穿過此缺口，之後再將通道重新黏合
* 之所以有拓撲異構酶之名稱，是因DNA環以扭轉形式存在時稱為拓撲異構物
* 部分藥物即是使用干擾之來達到防止細菌或癌細胞增值的效果  
e.g., 廣效氟化奎林酮類抗生素 (Fluoroquinolone)
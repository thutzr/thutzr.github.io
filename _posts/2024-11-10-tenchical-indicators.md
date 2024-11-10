---
layout: post
title:  "量化交易中的一些技术指标"
date:   2024-11-10 14:54:05 +0800
categories: post
---

## Momentum Indicators

### Chaikin A/D Line

* **Formula:** $CLV = \frac{(Close - Low) - (High - low)}{High - Low}, CF = CLV \times Volume, ADL = previous ADL + CF $ 
* **Intuition:** 当Close = mean(High, Low)，则CLV = 0, Close=High, CLV=1, Close=Low, CLV=-1, CLV一定程度上衡量了这个High发生的时间点和Close的时间点是否比较接近，如果比较接近，说明在这个bar内，价格是在上升的。CF则衡量了这个bar内净流入资金（近似），ADL则衡量了累计的资金净流入



### Chaikin Oscillator

* **Formula:** $CO = EMA(ADL, 3) - EMA(ADL, 10)$ 
* **Intuition:** 当CO为正是意味着买方力量更强，价格可能趋于向上，反之，价格趋于向下

### ADX

* **Formula:** $+DM = CurrHigh - PrevHigh, Smooth+DM = \sum_{t=1}^{14} +DM - \sum_{t=1}^{14} +DM/14 + Curr+DM$ 
  * $+DI = \frac{Smooth+DM}{ATR} \times 100, DX = \frac{|+DI - -DI|}{|+DI + -DI|}\times 100$  
  * $ADX = \frac{PrevADX \times 13 + CurrADX}{14}$ 

* **Intuition:** +DI衡量过去一段时间的价格趋势，DX衡量了价格变化的强度，ADX是DX的指数移动平均

### ADXR

* **Formula:** $ ADXR = (ADX + ADX_{t-n}) / 2$ 
* **Intuition:** 是ADX的lagging，二者可能结合起来用比较好，但是感觉很奇怪，可能可以直接求ADX的EMA

### Absolute Price Oscillator

* **Formula:** $APO = EMA(Price, 12) - EMA(Price, 26)$  
* **Intuition:** APO衡量了价格的趋势

### Aroon

* **Formula:** $AroonUp = \frac{\argmax_{i=1,\cdots,25} High_i }{25}\times 100, AroonDown = \frac{\argmax_{i=1,\cdots,25} Low_i }{25}\times 100$ 
* **Intuition:** 看最近的价格高点/低点距离当前有多远，如果比较近，可能意味着上升/下降趋势

### Aroon Oscillators

* **Formula:** $AO = AroonUp - AroonDown$ 
* **Intuition:** AO大于0时，意味着最高点出现的点离当前更近，可能意味着一个上升趋势

### Balance of Power

* **Formula:** $BoP = \frac{Close - Open}{High - Low}$
* **Intuition:** BoP越大可能意味着买方力量越强

### Commodity Channel Index

* **Formula:** $CCI = \frac{TypicalPrice - MA}{0.015 \times MeanDeviation}, TypicalPrice = \frac{High + Low + Close}{3}, MA = EMA(TypicalPrice, 12), MeanDeviation = \sum_{i=1}^{12}\frac{|TypicalPrice - MA|}{12}$ 
* **Intuition:**  CCI衡量了当前价格和MA之间的偏离程度，偏离越远可能意味着趋势强度越高

### Two Crows

* **Formula:** 第一个bar是阳线，第二个bar是阴线，但是第二个bar的Close大于第一个的Close，第三个bar的Open比第二个的Open高，第三个bar的Close比第二个的低，但是比第一个的Close高
* **Intuition:** 当这个pattern出现在上升趋势中时，可能意味着要开始反转了，因为即使第二个和第三个的Open比较高，最终仍然是阴线，可能意味着大家不看多

### Three Black Crows

* **Formula:** 在一轮上涨之后，出现连续的三根比较长的阴线
* **Intuition:** 在上涨之后，突然连续下跌，可能意味着买方力量减弱，卖方市场开启，引起一轮下跌。

### Three Inside Up/Down

* **Formula:** Up: 	在一个下跌市场中，第一个bar是长阴线，第二根和第三根都是阳线，并且第三根阳线的Close比第二根的高
* **Intuition:** 第一根长阴线中，卖方力量被消耗很多，第二三根中买方接管，可能是买方市场的信号



### 3 Outside Up/Down

* **Formula:** Up: 市场在一个下跌趋势中，第二根bar包含了第一根bar，第一根是阴线，第二三根是阳线，第三根的close比第二根的高
* **Intuition:** 和之前类似

<img src="/Users/tanzeren/Library/Application Support/typora-user-images/截屏2024-11-06 20.32.37.png" alt="截屏2024-11-06 20.32.37" style="zoom:25%;" />



### Three Stars in the South

* **Formula:**  市场在下跌中，第一根bar是长阴线，下影线也很长，第二根bar比较短一点，但是low比第一根的高，第三根也是阴线但是没有下影线，close在第二根中间
* **Intuition:** 这三根bar的形状表明，卖方力量在逐渐被消耗尽，最后可能出现反转效应



### Bullish Abandoned Baby

* **Formula:** 
  * The first bar is a large down candlestick located within a defined downtrend.
  * The second bar is a doji candle (open is approximately equal to the close) that gaps below the [close](https://www.investopedia.com/terms/c/closingprice.asp) of the first bar.
  * The third bar is a large white candle that [opens](https://www.investopedia.com/terms/o/openingprice.asp) above the second bar.
* **Intuition:** 第一根bar说明卖方卖了很多，第二根说明卖方力量减弱，第三根说明买方接管市场



### Advance Block

* **Formula:** 
  * 价格在上涨趋势中
  * 两根比较短的bar线之后有三根阳线
  * 第二根和第三根阳线的Open在前一个bar线中间
  * 上影线逐渐变长
* **Intuition:** 连续上涨，但是open并没有明显变高，可能意味着上涨力量不够强



### Williams percent range

* **Formula:** $WPR = \frac{Highest High - Close}{Highest High - Lowest Low}$ 
* **Intuition:** 如果WPR比较大，可能意味着当前价格很高，未来有反转的空间。



### Ultimate Oscillator

* **Formula:** $UO = \frac{4\times A_7 + 2 A_{14} + A_{28}}{7}, A_7 = \frac{\sum_{i=1}^7 BP_i}{\sum_{i=1}^7 TR_i}, BP = Close - \min(Low, PrevClose), TR = \max(High, PrevClose) - \min(Low, PrevClose)$ 
* **Intuition:** UO和其他Oscillator一样衡量了趋势强度，但是用不同时间尺度的信息做了平滑



### Triple Exponential Average

* **Formula:** $EMA1 = EMA(Price, N), EMA2 = EMA(EMA1, N), EMA3 = EMA(EMA2, N), TRIX = \frac{EMA3(i) - EMA3(i-1)}{EMA3(i-1)}$ 
* **Intuition:** EMA用于平滑一些噪声，通过多次EMA可以得到更加平滑的信号，但是也有平滑点信息的风险，TRIX很大时可能意味着标的overbought，很小意味着oversold。同时TRIX也可以衡量趋势的强度。



### RSI

* **Formula:** $ RSI=100 - \frac{100}{1 + \frac{AvgGain}{AvgLoss}}$ 
* **Intuition:** 主要是根据过去一点时间涨跌比例，判断当前是否买方overbought或者卖方oversold，导致反转。



### Stochastic RSI

* **Formula:** $StochRSI = \frac{RSI - ]min(RSI, N)}{\max(RSI, N) - \min(RSI, N)}$ 
* **Intuition:** StochRSI是RSI这个oscillator的oscillator，他比RSI更加敏感，当市场发生变化时，它变化更快，比如RSI连续处于高位，但是处于下降状态时，StochRSI能做出反应



### Parabolic SAR

* **Formula:** $SAR_{t+1} = SAR_{t} + \alpha (EP - SAR_t)$,  EP is the highest/lowest price reached in uptrend/downtrend. 
* **Intuition:**  在uptrend中，SAR会不断的变大，向上收敛接近于真实价格，downtrend中SAR会不断变小，如果SAR小于当前价格，但是也在上升，可能意味着上升趋势。



### Money Flow Index

* **Formula:** $MFI = 100 - \frac{100}{1 + MFR}, MFR = \frac{Positive Money Flow}{Negative Money Flow}, MoneyFlow = Price \times Volume$ 
* **Intuition:**  类似于用Volume加权的RSI



### MACD

* **Formula:** $MACD = EMA(12) - EMA(26), MACDSignal = EMA(MACD, 9)$
* **Intuition:** 当MACD上穿MACDSigna_ = plt.hist(data['mfi_4'], bins=100)l时，可能意味着上升趋势的开启。

### Kaufman Adaptive Moving Average

* **Formula:** $KAMA_t = KAMA_{t-1} + SC \times (Price - KAMA_{t-1}), SC = (ER \times (FastestSC - SlowestSC) + SlowestSC)^2, ER = \frac{|Close_t - Close_{t-10}}{\sum_{i=0}^9 |Close_{t-i} - Close_{t-i+1}}$ 
* **Intuition:** 加强版的moving average，ER衡量了价格变化的强度，当价格连续变低时为1. 用于调整EMA中的系数，价格波动更大时会给更近的价格更多的权重。



### Double Exponential Moving Average

* **Formula:** $DEMA = 2EMA(N) - EMA(EMA(N), N)$ 
* **Intuition:** 通过两层EMA来平滑掉一些噪声

### Chande Momentum Oscillator

* **Formula:** $CMO = \frac{sH - sL}{sH + sL} \times 100, sH = SumOfClose Where Bar Is Positive$
* **Intuition:** 当所有的bar都是阳线时，CMO=1，买方力量在经过这么多的上涨之后削弱，之后会反转

`

## Volatility Indicators

### ATR

* **Formula:** $ATR = \frac{(n-1) PrevATR + TR}{n}, TR = \max\{High - Low, | High - PrevClose|, |Low - PrevClose|\}$ 
* **Intuition:** ATR越大意味着今天的价格变化越大，波动越大


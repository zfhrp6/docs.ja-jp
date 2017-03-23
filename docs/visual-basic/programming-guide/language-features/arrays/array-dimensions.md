---
title: "Array Dimensions in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "dimensions, arrays"
  - "arrays [Visual Basic], dimensions"
  - "arrays [Visual Basic], rectangular"
  - "arrays [Visual Basic], rank"
  - "rectangular arrays"
  - "ranking, arrays"
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Array Dimensions in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

*次元*とは、配列の要素の仕様を変更できる方向のことです。  その月の売上合計を日付ごとに保持している配列は、1 次元となります \(月の日付\)。  その月の日付ごとの売上合計を部門別に保持している配列は、2 次元となります \(部門の番号と月の日付\)。  配列で保持している次元の数は、*ランク*と呼ばれます。  
  
> [!NOTE]
>  配列で保持している次元の数は、<xref:System.Array.Rank%2A> プロパティを使用して確認できます。  
  
## 次元の使用  
 配列の要素を指定するには、その配列の各次元に対して*インデックス*または*添字*を提供します。  要素は、インデックス 0 からその次元で最も高位のインデックスまで、各次元に従って連続しています。  
  
 ランクが異なる配列の概念的構造を次の図に示します。  図の各要素は、これにアクセスするインデックスの値を示しています。  たとえば、2 次元配列の 2 行目の最初の要素にアクセスするには、インデックス `(1, 0)` を指定します。  
  
 ![1 次元配列のグラフィック ダイアグラム](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.png "ArrayExDimOne")  
1 次元配列  
  
 ![2 次元配列のグラフィック ダイアグラム](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")  
2 次元配列  
  
 ![3 次元配列のグラフィック ダイアグラム](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.png "ArrayExDimThree")  
3 次元配列  
  
### 1 次元  
 各年齢の人数など、1 次元だけの配列は多数あります。  要素を指定するのに唯一必要なことは、その要素でカウントする年齢だけです。  したがって、このような配列では 1 つのインデックスだけを使用します。  次の例では、年齢が 0 ～ 120 の年齢別カウントの *1 次元配列*を保持する変数を宣言しています。  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### 2 次元  
 キャンパス内の各建物のフロアごとのオフィスの数など、2 次元の配列を持つものがあります。  要素を指定するには、建物の番号とフロアの両方が必要で、さらに各要素は建物とフロアを組み合わせたカウントを保持する必要があります。  したがって、このような配列では 2 つのインデックスを使用します。  次の例では、建物の番号が 0 ～ 40、そしてフロアが 0 ～ 5 であるオフィスの数の *2 次元配列*を保持する変数を宣言しています。  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 2 次元配列は、*多次元配列*とも呼ばれます。  
  
### 3 次元  
 3 次元空間の値など、3 次元での配列もいくつかあります。  このような配列では 3 つのインデックスを使用し、その場合には物理的な空間を x、y、および z 軸で表します。  次の例では、3 次元ボリュームのさまざまなポイントでの気温を表すため *3 次元配列*を保持する変数を宣言しています。  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### 3 次元より多くの次元  
 配列では最高 32 次元まで保持することが可能ですが、3 次元より多くなることは稀です。  
  
> [!NOTE]
>  配列に必要なメモリ領域は多次元になるほど増大するので、多次元配列を宣言するときには注意してください。  
  
## 異なる次元の使用  
 当月の売上額を日付ごとに追跡する場合を考えます。  次の例で示されているように、月の日付ごとに 1 つずつ、31 の要素に対して 1 次元の配列を宣言する必要があります。  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 その月の日付についてだけでなく、年間をとおして毎月同じ情報を追跡する場合を考えます。  次の例で示すように、12 行 \(月\) と 31 列 \(日付\) の 2 次元配列を宣言できます。  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 配列に複数年の情報を保持させる場合を考えます。  5 年間分の売上額を追跡する場合は、次の例で示すように、5 層、12 行、および 31 列の 3 次元配列を宣言できます。  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 各インデックスの値は 0 から最大値まで多岐にわたるため、`salesAmounts` の各次元は、その次元で必要な長さより小さく宣言されることに注意してください。  また、配列のサイズは新しい次元ごとに増大していくことにも注意してください。  前の例では 3 つのサイズは、それぞれ 31、372、および 1,860 要素です。  
  
> [!NOTE]
>  `Dim` ステートメントまたは `New` 句を使用せずに、配列を作成できます。  たとえば、<xref:System.Array.CreateInstance%2A> メソッドを呼び出すか、または別のコンポーネントでこの方法により作成された配列のコードを渡すことができます。  このような配列では 0 以外の下限を持つことができます。  <xref:System.Array.GetLowerBound%2A> メソッドまたは `LBound` 関数を使用して、いつでも次元の下限をテストできます。  
  
## 参照  
 [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Troubleshooting Arrays](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
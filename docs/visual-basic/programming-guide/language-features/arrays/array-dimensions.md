---
title: Visual Basic における配列の次元
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: cf295288dd034d744dceb71b5c58278be5cc2a2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651757"
---
# <a name="array-dimensions-in-visual-basic"></a>Visual Basic における配列の次元
A*ディメンション*は、方向、配列の要素の仕様を変更できます。 月の日付ごとの売上を合計を保持する配列には、1 つのディメンション (月の日) があります。 月の日付ごとに、売り上げ高を部門によって合計を保持する配列には、2 つのディメンション (部署番号と月の日) があります。 配列がディメンションの数が呼び出されますその*ランク*です。  
  
> [!NOTE]
>  使用することができます、<xref:System.Array.Rank%2A>配列には、次元数を決定するプロパティです。  
  
## <a name="working-with-dimensions"></a>ディメンションの使用  
 指定することによって、配列の要素を指定する、*インデックス*または*添字*の各次元です。 要素は、各ディメンションに従ってそのディメンションの最も大きいインデックスをインデックス 0 から連続しています。  
  
 次の図は、異なるランクを持つ配列の概念の構造を表示します。 図内の各要素は、これにアクセスするインデックス値を示します。 たとえば、インデックスを指定することによって、2 次元配列の 2 番目の行の最初の要素をアクセス`(1, 0)`です。  
  
 ![1 つのグラフィック ダイアグラム&#45;次元配列](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")  
1 次元配列  
  
 ![2 つのグラフィック ダイアグラム&#45;次元配列](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")  
2 次元配列  
  
 ![3 つのグラフィック ダイアグラム&#45;次元配列](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")  
3 次元配列  
  
### <a name="one-dimension"></a>1 つのディメンション  
 多くのアレイは、各年齢のユーザーの数などの 1 つだけディメンションを持ちます。 要素を指定する唯一の要件は、その要素がカウントを保持する期間です。 そのため、このような配列は、1 つだけのインデックスを使用します。 次の例を保持する変数の宣言、 *1 次元配列*年齢の年齢が 0 ~ 120 の数します。  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a>2 つのディメンション  
 一部の配列では、キャンパスの各建物のフロアごとのオフィスの数など、2 次元があります。 要素の仕様は、建物番号と、切り捨ての両方が必要ですし、各要素は、ビルとフロアの組み合わせの数を保持します。 したがって、このような配列には、2 つのインデックスが使用されます。 次の例を保持する変数の宣言、 *2 次元配列*オフィスの数の 0 ~ 40 のビルとフロアが 0 ~ 5 です。  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 2 次元の配列とも呼ばれますが、*四角形配列*です。  
  
### <a name="three-dimensions"></a>3 つのディメンション  
 いくつかの配列では、3 次元空間の値など、3 つの次元を持ちます。 このような配列では、ここでは、x、y、および物理領域の z 座標を表す 3 つのインデックスを使用します。 次の例を保持する変数の宣言、 *3 次元配列*3 次元のボリューム内のさまざまな時点での気温します。  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a>複数の 3 つのディメンション  
 配列には、最大 32 次元を持つことができます、ケースはまれ 3 以上です。  
  
> [!NOTE]
>  配列にディメンションを追加するときに配列に必要な合計ストレージ増大は多次元配列を払ってください。  
  
## <a name="using-different-dimensions"></a>別のディメンションを使用します。  
 当月の日の売上を追跡したいとします。 次の例として、月の日付ごとに 1 つを示しています、31 の要素の 1 次元配列を宣言することがあります。  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 今すぐ毎日についてだけでなく、1 か月のすべての月、年のに対しても、同じ情報を追跡したいとします。 次の例のように 12 行 (月) と 31 列 (日)、2 次元配列を宣言することがあります。  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 ようになりましたことに決定したと仮定しますお使いの配列は 1 年間以上の情報を保持します。 5 年の売上額を追跡する場合は、次の例のように 5 層、12 の行と列を含む 31、3 次元の配列を宣言する可能性があります。  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 なお、各インデックスが 0、最大の各次元に異なりますので`salesAmounts`そのディメンションの 1 つ必要な長さより小さい値として宣言されています。 配列のサイズは、新しい次元ごとに増加にも注意してください。 前の例では、3 つのサイズは、それぞれ 31、372、および 1,860 要素です。  
  
> [!NOTE]
>  使用せずに配列を作成することができます、`Dim`ステートメントまたは`New`句。 たとえばを呼び出すことができます、<xref:System.Array.CreateInstance%2A>メソッド、または別のコンポーネントをこのように作成された配列、コードを渡すことができます。 このような配列には、0 以外の下限を持つことができます。 常にテストできます、次元の下限値を使用して、<xref:System.Array.GetLowerBound%2A>メソッドまたは`LBound`関数。  
  
## <a name="see-also"></a>関連項目  
 [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [配列のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)

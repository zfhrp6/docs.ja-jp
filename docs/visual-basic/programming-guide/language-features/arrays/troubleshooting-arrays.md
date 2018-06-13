---
title: 配列のトラブルシューティング (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: 4ab6d376ad8652e460e33c4f2c3285e8c80286fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654269"
---
# <a name="troubleshooting-arrays-visual-basic"></a>配列のトラブルシューティング (Visual Basic)
このページには、配列を扱うときに発生する可能性がある一般的な問題が一覧表示されます。  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>コンパイル エラーを宣言して、配列の初期化  
 コンパイル エラーは、宣言、作成、および配列の初期化の規則の誤解から発生することができます。 次のエラーの最も一般的な原因を示します。  
  
-   指定する、 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)配列変数の宣言に次元の長さを指定した後の句。 次のコード行は、この型の無効な宣言を示しています。  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   ジャグ配列の最上位の配列より多くの次元の長さを指定します。 次のコード行は、この型の無効な宣言を示しています。  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   省略すると、`New`キーワードは要素の値を指定する場合。 次のコード行は、この型の無効な宣言を示しています。  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   指定する、`New`句なしで中かっこ (`{}`)。 次のコード行は、この型の無効な宣言を示しています。  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>範囲外の配列へのアクセス  
 配列の初期化中のプロセスは、各ディメンションを上限と下限の境界を割り当てます。 配列の要素へのアクセスには、有効なインデックスまたは添字の各次元を指定します。 インデックスの場合は、下限を下回る、またはその上限を超えて、<xref:System.IndexOutOfRangeException>例外が発生します。 実行時にエラーが発生したため、コンパイラは、このようなエラーを検出できません。  
  
### <a name="determining-bounds"></a>範囲の確認  
 場合は、コードに別のコンポーネントが配列を渡すと、たとえば、プロシージャの引数としてわからないその配列のサイズまたはその次元の長さ。 任意の要素にアクセスしようとする前に常に配列のすべての次元の上限の境界を決定する必要があります。 配列は、Visual Basic 以外のいくつかの方法で作成されている場合`New`句、下限が 0 以外のものありますでありもその下限の境界を決定する最も安全な方法です。  
  
### <a name="specifying-the-dimension"></a>ディメンションを指定します。  
 多次元配列の境界を決定するときに注意して、ディメンションを指定する方法。 `dimension`のパラメーター、<xref:System.Array.GetLowerBound%2A>と<xref:System.Array.GetUpperBound%2A>メソッドは、中に、0 から始まる、 `Rank` 、Visual Basic のパラメーター<xref:Microsoft.VisualBasic.Information.LBound%2A>と<xref:Microsoft.VisualBasic.Information.UBound%2A>関数は、1 から始まります。  
  
## <a name="see-also"></a>関連項目  
 [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [方法: Visual Basic で配列変数を初期化する](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)

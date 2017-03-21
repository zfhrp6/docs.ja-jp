---
title: "配列のトラブルシューティング (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
caps.latest.revision: 17
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: db38c0c2a4f8b74a6b862f86f426b4d8837f4424
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-arrays-visual-basic"></a>配列のトラブルシューティング (Visual Basic)
ここでは、配列を扱うときに発生する一般的な問題についてを説明します。  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>コンパイル エラーを宣言して、配列の初期化  
 コンパイル エラーは、宣言、作成、および配列の初期化の規則の誤解から発生します。 エラーの最も一般的な原因として、次のとおりです。  
  
-   指定すること、 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)配列変数の宣言に次元の長さを指定した後の句。 次のコード行では、この型の無効な宣言を表示します。  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   ジャグ配列の最上位の配列の次元の長さを指定します。 次のコード行では、この型の無効な宣言を示します。  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   省略すると、`New`キーワードは要素の値を指定する場合。 次のコード行では、この型の無効な宣言を示します。  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   指定すること、`New`句なしで中かっこ (`{}`)。 次のコード行では、この型の無効な宣言を表示します。  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>配列の範囲外にアクセスします。  
 配列を初期化するプロセスは、各次元に、上限と下限の境界を割り当てます。 配列の要素へのアクセスには、有効なインデックスまたは添字のすべてのディメンションを指定します。 下限またはその上限を超えて任意のインデックスがある場合、<xref:System.IndexOutOfRangeException>例外が発生します</xref:System.IndexOutOfRangeException>。 コンパイラは、実行時にエラーが発生したため、このようなエラーを検出できません。  
  
### <a name="determining-bounds"></a>範囲の確認  
 別のコンポーネントは、配列をコードに合格した場合など、プロシージャの引数としてわからないその配列のサイズまたはその次元の長さ。 要素にアクセスしようとする前に、配列のすべての次元の上限の境界を調べる必要があります。 かどうか、配列が作成されてなんらかの方法で以外の場合、 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `New`句、下限の境界、0 以外の場合がありますおよびが安全にもその下限の境界を決定します。  
  
### <a name="specifying-the-dimension"></a>ディメンションを指定します。  
 多次元配列の境界を決定する際は、ディメンションを指定する方法ように注意します。 `dimension`のパラメーター、<xref:System.Array.GetLowerBound%2A>と<xref:System.Array.GetUpperBound%2A>メソッドは、中に、0 から始まる、`Rank`のパラメーター、 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Information.LBound%2A>と<xref:Microsoft.VisualBasic.Information.UBound%2A>関数は、1 から始まります</xref:Microsoft.VisualBasic.Information.UBound%2A></xref:Microsoft.VisualBasic.Information.LBound%2A></xref:System.Array.GetUpperBound%2A></xref:System.Array.GetLowerBound%2A>。  
  
## <a name="see-also"></a>関連項目  
 [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [方法: Visual Basic で配列変数を初期化](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)

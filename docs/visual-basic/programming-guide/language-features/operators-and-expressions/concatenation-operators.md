---
title: "Visual Basic の連結演算子 |Microsoft ドキュメント"
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
- '& operator [Visual Basic], concatenation'
- concatenation operators
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators, Visual Basic strings
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: fa11f1dcff2c333861596cbac03391403cf962c1
ms.lasthandoff: 03/13/2017

---
# <a name="concatenation-operators-in-visual-basic"></a>Visual Basic の連結演算子
連結演算子は、複数の文字列を結合して&1; つの文字列にします。 連結演算子には、`+` と `&` の&2; つがあります。 どちらの演算子も、次の例に示すように基本的な連結演算を行います。  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 これらの演算子は、次のように `String` 型の変数を連結することもできます。  
  
 [!code-vb[VbVbalrOperators #&76;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]  
  
## <a name="differences-between-the-two-concatenation-operators"></a>2 つの連結演算子の相違点  
 [+ 演算子](../../../../visual-basic/language-reference/operators/addition-operator.md)が&2; つの数値を追加する主な目的です。 ただし、数値オペランドを文字列オペランドに連結することもできます。 `+`演算子は、複雑な一連のルールを追加、連結、コンパイラ エラーを報告または実行時にスローするかどうかを決定する<xref:System.InvalidCastException>例外</xref:System.InvalidCastException>。  
  
 [&Gt;/documents/report1.rdl」の演算子](../../../../visual-basic/language-reference/operators/concatenation-operator.md)に対してのみ定義`String`オペランド、および、常に拡大変換するには、そのオペランド`String`の設定に関係なく、`Option Strict`です。 文字列の連結には `&` 演算子を使用することをお勧めします。この演算子は文字列専用として定義されているため、意図しない変換が発生する可能性を減らすことができます。  
  
## <a name="performance-string-and-stringbuilder"></a>パフォーマンス: 文字列と StringBuilder  
 パフォーマンスが向上する非常に多くの連結、削除、置換などの文字列操作の操作を行う場合、<xref:System.Text.StringBuilder>クラス、<xref:System.Text>名前空間</xref:System.Text></xref:System.Text.StringBuilder>。 作成および初期化するには追加の命令を受け取り、<xref:System.Text.StringBuilder>オブジェクト、および別の命令を最終的な値に変換する、 `String`、ために、この時間を埋め合わせることがありますが、<xref:System.Text.StringBuilder>高速に実行できます</xref:System.Text.StringBuilder></xref:System.Text.StringBuilder>。  
  
## <a name="see-also"></a>関連項目  
 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Visual Basic で文字列操作メソッドの種類](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)   
 [Visual Basic における算術演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Visual Basic における比較演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Visual Basic での論理/ビット処理演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)

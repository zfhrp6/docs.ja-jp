---
title: 最初のオペランドはバイナリで&#39;場合&#39;式を null 許容にする必要がありますまたは型の参照
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 76078d315b2c32a2a29aa652a65b463622afec36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590830"
---
# <a name="first-operand-in-a-binary-39if39-expression-must-be-nullable-or-a-reference-type"></a>最初のオペランドはバイナリで&#39;場合&#39;式を null 許容にする必要がありますまたは型の参照
`If`式が 2 または 3 つの引数を受け取ることができます。 2 つの引数を送信するときに、最初の引数は、参照型または null 許容型にする必要があります。 最初の引数が以外の何もする評価された場合に`Nothing`、その値が返されます。 最初の引数が評価された場合`Nothing`、2 番目の引数が評価され、返されます。  
  
 たとえば、次のコードには 2 つ`If`3 つの引数と 2 つの引数の式。 式が計算され、同じ値が返すされます。  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 次の式では、このエラーが発生します。  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 **エラー ID:** BC33107  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   最初の引数が null 許容型または参照型であるようにコードを変更することはできない場合、は、3 つの引数に変換することを検討してください`If`式、または、`If...Then...Else`ステートメントです。  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a>関連項目  
 [If 演算子](../../../visual-basic/language-reference/operators/if-operator.md)  
 [If...Then...Else ステートメント](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [null 許容値型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)

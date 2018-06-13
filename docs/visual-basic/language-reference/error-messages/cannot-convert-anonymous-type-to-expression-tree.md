---
title: 型のプロパティは別のプロパティを初期化するために使用されるため、匿名型を式のツリーに変換することはできません。
ms.date: 07/20/2015
f1_keywords:
- bc36548
- vbc36548
helpviewer_keywords:
- BC36548
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
ms.openlocfilehash: d43f6ef19591af326d06a4ce21194d8f9fa58c2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585477"
---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a>型のプロパティは別のプロパティを初期化するために使用されるため、匿名型を式のツリーに変換することはできません。
コンパイラでは、匿名型の別のプロパティを初期化するために、匿名型の 1 つのプロパティを使用する場合、匿名の式ツリーへの変換は受け入れられません。 たとえば、次のコードで`Prop1`が初期化リストで宣言されの初期値として使用し、`Prop2`です。  
  
```vb  
Module M2  
  
    Sub ExpressionExample(Of T)(ByVal x As Expressions.Expression(Of Func(Of T)))  
    End Sub  
  
    Sub Main()  
        ' The following line causes the error.  
        ' ExpressionExample(Function() New With {.Prop1 = 2, .Prop2 = .Prop1})  
  
    End Sub  
End Module  
```  
  
 **エラー ID:** BC36548  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   初期値を割り当てる`Prop1`ローカル変数にします。 両方にその変数を割り当てる`Prop1`と`Prop2`、次のコードに示すようにします。  
  
    ```  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a>関連項目  
 [匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [式ツリー](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)  
 [方法 : 式ツリーを使用して動的クエリをビルドする](http://msdn.microsoft.com/library/1e37e0cc-eef3-48bb-8b69-3adabf322735)

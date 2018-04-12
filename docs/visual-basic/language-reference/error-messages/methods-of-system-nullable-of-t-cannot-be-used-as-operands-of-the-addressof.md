---
title: メソッド &#39;'System.nullable(of (Of T) &#39;オペランドとして使用することはできません、&#39;です。AddressOf &#39;演算子
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ce0e9bc6abd71f22e3f6c3486ef40493e74d820f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="methods-of-39systemnullableof-t39-cannot-be-used-as-operands-of-the-39addressof39-operator"></a>メソッド &#39;'System.nullable(of (Of T) &#39;オペランドとして使用することはできません、&#39;です。AddressOf &#39;演算子
ステートメントを使用して、`AddressOf`のプロシージャを表すオペランドと演算子、<xref:System.Nullable%601>構造体。  
  
 **エラー ID:** BC32126  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   プロシージャ名に置き換えます、`AddressOf`のメンバーではないオペランドを含む句<xref:System.Nullable%601>です。  
  
-   メソッドをラップするクラスを記述<xref:System.Nullable%601>を使用します。 次の例で、`NullableWrapper`クラスという名前の新しいメソッドを定義する`GetValueOrDefault`です。 この新しいメソッドがのメンバーではないため<xref:System.Nullable%601>に適用できる`nullInstance`、フォームの引数を null 許容型のインスタンス`AddressOf`です。  
  
```vb  
Module Module1  
  
    Delegate Function Deleg() As Integer  
  
    Sub Main()  
        Dim nullInstance As New Nullable(Of Integer)(1)  
  
        Dim del As Deleg  
  
        ' GetValueOrDefault is a method of the Nullable generic  
        ' type. It cannot be used as an operand of AddressOf.  
        ' del = AddressOf nullInstance.GetValueOrDefault  
  
        ' The following line uses the GetValueOrDefault method  
        ' defined in the NullableWrapper class.  
        del = AddressOf (New NullableWrapper(  
            Of Integer)(nullInstance)).GetValueOrDefault  
  
        Console.WriteLine(del.Invoke())  
    End Sub  
  
    Class NullableWrapper(Of T As Structure)  
        Private m_Value As Nullable(Of T)  
  
        Sub New(ByVal Value As Nullable(Of T))  
            m_Value = Value  
        End Sub  
  
        Public Function GetValueOrDefault() As T  
            Return m_Value.Value  
        End Function  
    End Class  
End Module  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Nullable%601>  
 [AddressOf 演算子](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [null 許容値型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

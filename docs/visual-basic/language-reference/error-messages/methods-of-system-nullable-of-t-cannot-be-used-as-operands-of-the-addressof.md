---
title: メソッドの&#39;'system.nullable(of T)&#39;のオペランドとして使用することはできません、 &#39;AddressOf&#39;演算子
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 3a3e4fc033f47fb6a72076dff79f1eece8d01a30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594121"
---
# <a name="methods-of-39systemnullableof-t39-cannot-be-used-as-operands-of-the-39addressof39-operator"></a>メソッドの&#39;'system.nullable(of T)&#39;のオペランドとして使用することはできません、 &#39;AddressOf&#39;演算子
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

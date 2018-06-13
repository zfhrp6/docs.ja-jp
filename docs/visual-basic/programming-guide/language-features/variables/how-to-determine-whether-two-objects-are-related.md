---
title: '方法: 2 つのオブジェクトが関連しているかどうかを判別する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 2041f89ffd954e479046eb85c6dd82de1f8793ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649826"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>方法: 2 つのオブジェクトが関連しているかどうかを判別する (Visual Basic)
その作成元のクラス間のリレーションシップを判断する 2 つのオブジェクトを比較することができます。 <xref:System.Type.IsInstanceOfType%2A>のメソッド、<xref:System.Type?displayProperty=nameWithType>クラスを返します`True`指定したクラスを現在のクラスから継承する場合、または現在の型が指定したクラスでサポートされているインターフェイス。  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>1 つのオブジェクトが別のオブジェクトのクラスまたはインターフェイスから継承かどうかを決定するには  
  
1.  思われるオブジェクトの可能性がありますの基本型、呼び出し、<xref:System.Object.GetType%2A>メソッドです。  
  
2.  <xref:System.Type?displayProperty=nameWithType>によって返されるオブジェクト<xref:System.Object.GetType%2A>を呼び出し、<xref:System.Type.IsInstanceOfType%2A>メソッドです。  
  
3.  引数リストの<xref:System.Type.IsInstanceOfType%2A>、派生型のオブジェクトと思われる場合がありますを指定します。  
  
     <xref:System.Type.IsInstanceOfType%2A> 返します`True`からその引数の型を継承する場合、<xref:System.Type?displayProperty=nameWithType>オブジェクトの種類。  
  
## <a name="example"></a>例  
 次の例では、1 つのオブジェクトが別のオブジェクトのクラスから派生するクラスを表すかどうかを判断します。  
  
```  
Public Class baseClass  
End Class  
Public Class derivedClass : Inherits baseClass  
End Class  
Public Class testTheseClasses  
    Public Sub seeIfRelated()  
        Dim baseObj As Object = New baseClass()  
        Dim derivedObj As Object = New derivedClass()  
        Dim related As Boolean  
        related = baseObj.GetType().IsInstanceOfType(derivedObj)  
        MsgBox(CStr(related))  
    End Sub  
End Class  
```  
  
 呼び出しで 2 つのオブジェクト変数の予期しない配置に注意してください<xref:System.Type.IsInstanceOfType%2A>です。 生成に使用される基本型、<xref:System.Type?displayProperty=nameWithType>クラス、およびされる派生型が引数として渡される、<xref:System.Type.IsInstanceOfType%2A>メソッドです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.IsInstanceOfType%2A>  
 [Object 型](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [オブジェクト変数の値](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [方法: 2 つのオブジェクトが同一であるかどうか判別する](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)

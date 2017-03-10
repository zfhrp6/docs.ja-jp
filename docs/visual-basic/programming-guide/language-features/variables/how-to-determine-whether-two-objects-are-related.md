---
title: "How to: Determine Whether Two Objects Are Related (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "inheritance, Visual Basic objects"
  - "objects [Visual Basic], inheritance"
  - "object variables, determining relation"
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# How to: Determine Whether Two Objects Are Related (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

2 つのオブジェクトの各作成元クラス間の関係 \(もしあれば\) を確認するために、それらのオブジェクトを比較することができます。  指定されたクラスが現在のクラスから継承されている場合、または指定されたクラスが現在の型をサポートしている場合、<xref:System.Type?displayProperty=fullName> クラスの <xref:System.Type.IsInstanceOfType%2A> メソッドは `True` を返します。  
  
### あるオブジェクトが、他のオブジェクトのクラスまたはインターフェイスを継承しているかどうかを決めるには  
  
1.  基本型と思われるオブジェクトで、<xref:System.Object.GetType%2A> メソッドを呼び出します。  
  
2.  <xref:System.Object.GetType%2A> によって返された <xref:System.Type?displayProperty=fullName> オブジェクトで、<xref:System.Type.IsInstanceOfType%2A> メソッドを呼び出します。  
  
3.  <xref:System.Type.IsInstanceOfType%2A> の引数リスト内で、派生型であると思われるオブジェクトを指定します。  
  
     引数型が <xref:System.Type?displayProperty=fullName> オブジェクト型を継承している場合、<xref:System.Type.IsInstanceOfType%2A> は `True` を返します。  
  
## 使用例  
 次に示すのは、一方のオブジェクトの表すクラスが、もう一方のオブジェクトのクラスから派生したものかどうかを確認する例です。  
  
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
  
 <xref:System.Type.IsInstanceOfType%2A> への呼び出し内にある 2 つのオブジェクト変数が、期待どおり設定されない場合があることに注意してください。  この処理では、想定される基本型を使用して <xref:System.Type?displayProperty=fullName> クラスが生成され、想定される派生型が引数として <xref:System.Type.IsInstanceOfType%2A> メソッドに渡されます。  
  
## 参照  
 <xref:System.Object.GetType%2A>   
 <xref:System.Type?displayProperty=fullName>   
 <xref:System.Type.IsInstanceOfType%2A>   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [How to: Determine Whether Two Objects Are Identical](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
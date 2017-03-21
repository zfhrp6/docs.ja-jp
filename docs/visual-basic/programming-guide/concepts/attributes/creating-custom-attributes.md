---
title: "カスタム属性 (Visual Basic) の作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1aa97a591fdbdfab931a8b5e4f70ec3c00762332
ms.lasthandoff: 03/13/2017

---
# <a name="creating-custom-attributes-visual-basic"></a>カスタム属性 (Visual Basic) の作成
独自のカスタム属性を作成するには、属性クラスから直接または間接的に派生したクラスを定義することで<xref:System.Attribute>、迅速かつ容易なメタデータで属性の定義を識別するため、</xref:System.Attribute> 。 タグという名前の型の型を記述したプログラマにするとします。 カスタムを定義することも`Author`属性クラス。  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
        version = 1.0  
    End Sub  
End Class  
```  
  
 クラス名は、属性の名`Author`します。 派生`System.Attribute`ので、これはカスタム属性クラスです。 コンス トラクターのパラメーターは、カスタム属性の位置指定パラメーターです。 この例では`name`位置指定パラメーターです。 任意の読み取り/書き込みのパブリック フィールドまたはプロパティは名前付きパラメーター。 この場合、`version`はのみ名前付きパラメーター。 使用に注意してください、`AttributeUsage`属性を`Author`属性がクラスでのみ有効と`Structure`宣言します。  
  
 次のように、この新しい属性を使用できます。  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 `AttributeUsage`名前付きパラメーターを持つ`AllowMultiple`、これは、カスタム属性単一目的または multiuse とします。 次のコード例では、multiuse 属性が作成されます。  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 次のコード例では、同じ種類の複数の属性がクラスに適用されます。  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
>  属性クラスにプロパティが含まれている場合、そのプロパティは読み取り/書き込みをする必要があります。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Reflection></xref:System.Reflection>   
 [Visual Basic のプログラミング ガイド](../../../../visual-basic/programming-guide/index.md)   
 [カスタム属性の記述](http://msdn.microsoft.com/library/97216f69-bde8-49fd-ac40-f18c500ef5dc)   
 [リフレクション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)   
 [属性 (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)   
 [リフレクション (Visual Basic) を使用して属性へのアクセス](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)   
 [AttributeUsage (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)

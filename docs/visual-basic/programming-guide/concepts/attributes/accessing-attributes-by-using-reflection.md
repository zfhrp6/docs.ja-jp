---
title: "リフレクション (Visual Basic) を使用して属性へのアクセス |Microsoft ドキュメント"
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
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
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
ms.openlocfilehash: 4763eccc5d1a6bdf3e89c1c4d825d5ff5c6caa3e
ms.lasthandoff: 03/13/2017

---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a>リフレクション (Visual Basic) を使用して属性へのアクセス
その情報を取得、およびその操作方法がないほとんどの値のカスタム属性を定義し、ソース コード内に配置できることになります。 リフレクションを使用するには、カスタム属性で定義されている情報を取得できます。 重要なメソッドは`GetCustomAttributes`実行時に相当するソース コードの属性であるオブジェクトの配列が返されます。 このメソッドには、いくつかのオーバー ロードされたバージョンがあります。 詳細については、 <xref:System.Attribute>。</xref:System.Attribute>を参照してください。  
  
 などの属性の指定:  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 概念的にはこれと同じです。  
  
```vb  
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")  
anonymousAuthorObject.version = 1.1  
```  
  
 ただし、コードをまで実行されず`SampleClass`の属性の照会します。 呼び出す`GetCustomAttributes`に`SampleClass`により、`Author`オブジェクトを構築しても、上記のように初期化します。 その他の属性をクラスには、その他の属性のオブジェクトが同様に構築されます。 `GetCustomAttributes`戻ります、`Author`オブジェクトと配列内の他の属性オブジェクトです。 この配列を反復処理することができますし、各配列要素の種類に基づいて適用された属性を確認し、属性のオブジェクトから情報を抽出します。  
  
## <a name="example"></a>例  
 完全な例を次に示します。 カスタム属性が定義されている、複数のエンティティに適用され、リフレクションを使用して取得します。  
  
```vb  
' Multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
  
        ' Default value  
        version = 1.0  
    End Sub  
  
    Function GetName() As String  
        Return name  
    End Function          
End Class  
  
' Class with the Author attribute  
<Author("P. Ackerman")>   
Public Class FirstClass  
End Class  
  
' Class without the Author attribute  
Public Class SecondClass  
End Class  
  
' Class with multiple Author attributes.  
<Author("P. Ackerman"), Author("R. Koch", Version:=2.0)>   
Public Class ThirdClass  
End Class  
  
Class TestAuthorAttribute  
    Sub Main()  
        PrintAuthorInfo(GetType(FirstClass))  
        PrintAuthorInfo(GetType(SecondClass))  
        PrintAuthorInfo(GetType(ThirdClass))  
    End Sub  
  
    Private Shared Sub PrintAuthorInfo(ByVal t As System.Type)  
        System.Console.WriteLine("Author information for {0}", t)  
  
        ' Using reflection  
        Dim attrs() As System.Attribute = System.Attribute.GetCustomAttributes(t)  
  
        ' Displaying output  
        For Each attr In attrs  
            Dim a As Author = CType(attr, Author)  
            System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version)  
        Next              
    End Sub  
  
    ' Output:  
    '   Author information for FirstClass  
    '     P. Ackerman, version 1.00  
    ' Author information for SecondClass  
    ' Author information for ThirdClass  
    '  R. Koch, version 2.00  
    '  P. Ackerman, version 1.00  
  
End Class  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Reflection></xref:System.Reflection>   
 <xref:System.Attribute></xref:System.Attribute>   
 [Visual Basic のプログラミング ガイド](../../../../visual-basic/programming-guide/index.md)   
 [属性に格納されている情報を取得します。](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c)   
 [リフレクション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)   
 [属性 (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)   
 [カスタム属性 (Visual Basic) の作成](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)

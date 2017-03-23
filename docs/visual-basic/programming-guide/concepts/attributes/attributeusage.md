---
title: "AttributeUsage (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
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
ms.openlocfilehash: bf56f40033f9d1547d63fccd25e3c0561bb62cb1
ms.lasthandoff: 03/13/2017

---
# <a name="attributeusage-visual-basic"></a>AttributeUsage (Visual Basic)
カスタム属性クラスの使用方法を決定します。 `AttributeUsage`新しい属性を適用する方法を制御するカスタム属性の定義に適用できる属性です。 既定の設定は、明示的に適用されるときに、次のようになります。  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 この例では、`NewAttribute`クラスは、すべての属性を使用できるコード エンティティを適用して、エンティティごとに&1; 回だけ適用できます。 基本クラスに適用すると、派生クラスによって継承されます。  
  
 `AllowMultiple`と`Inherited`のため、このコードは、同じ効果を持ちます引数は省略できます。  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 最初の`AttributeUsage`引数の&1; つまたは複数の要素でなければなりません、<xref:System.AttributeTargets>列挙体</xref:System.AttributeTargets>。 複数のターゲット型は、次のように、OR 演算子と一緒にリンクされたことができます。  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 場合、`AllowMultiple`に設定されている引数`true`、次のように、単一のエンティティに結果の属性が複数回適用されます。  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=True)>   
Class MultiUseAttr  
    Inherits Attribute  
End Class  
  
<MultiUseAttr(), MultiUseAttr()>   
Class Class1  
End Class  
```  
  
 ここで`MultiUseAttr`ため繰り返し適用できる`AllowMultiple`に設定されている`true`します。 複数の属性を適用する場合、両方の形式は有効です。  
  
 場合`Inherited`に設定されている`false`、属性が指定されるクラスから派生したクラスによって継承されません。 例:  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Class, Inherited:=False)>   
Class Attr1  
    Inherits Attribute  
End Class  
  
<Attr1()>   
Class BClass  
  
End Class    
  
Class DClass  
    Inherits BClass  
End Class  
```  
  
 ここで`Attr1`には適用されません`DClass`継承を使用しています。  
  
## <a name="remarks"></a>コメント  
 `AttributeUsage`属性は、単一目的の属性 - 同じクラスに複数回適用することはできません。 `AttributeUsage`<xref:System.AttributeUsageAttribute>。</xref:System.AttributeUsageAttribute>エイリアスします。  
  
 詳細については、次を参照してください。[属性 (Visual Basic) を使用してリフレクションによってへのアクセス](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)します。  
  
## <a name="example"></a>例  
 次の例では、効果、`Inherited`と`AllowMultiple`への引数、`AttributeUsage`属性、およびクラスに適用されるカスタム属性を列挙する方法です。  
  
```vb  
Imports System  
```  
  
```vb  
' Create some custom attributes:  
<AttributeUsage(System.AttributeTargets.Class, Inherited:=False)>   
Class A1  
    Inherits System.Attribute  
End Class  
  
<AttributeUsage(System.AttributeTargets.Class)>   
Class A2  
    Inherits System.Attribute  
End Class      
  
<AttributeUsage(System.AttributeTargets.Class, AllowMultiple:=True)>   
Class A3  
    Inherits System.Attribute  
End Class  
  
' Apply custom attributes to classes:  
<A1(), A2()>   
Class BaseClass  
  
End Class  
  
<A3(), A3()>   
Class DerivedClass  
    Inherits BaseClass  
End Class  
  
Public Class TestAttributeUsage  
    Sub Main()  
        Dim b As New BaseClass  
        Dim d As New DerivedClass  
        ' Display custom attributes for each class.  
        Console.WriteLine("Attributes on Base Class:")  
        Dim attrs() As Object = b.GetType().GetCustomAttributes(True)  
  
        For Each attr In attrs  
            Console.WriteLine(attr)  
        Next  
  
        Console.WriteLine("Attributes on Derived Class:")  
        attrs = d.GetType().GetCustomAttributes(True)  
        For Each attr In attrs  
            Console.WriteLine(attr)  
        Next              
    End Sub  
End Class  
```  
  
## <a name="sample-output"></a>出力例  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Attribute></xref:System.Attribute>   
 <xref:System.Reflection></xref:System.Reflection>   
 [Visual Basic のプログラミング ガイド](../../../../visual-basic/programming-guide/index.md)   
 [属性](https://msdn.microsoft.com/library/5x6cd29c)   
 [リフレクション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)   
 [属性 (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)   
 [カスタム属性 (Visual Basic) の作成](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)   
 [リフレクション (Visual Basic) を使用して属性へのアクセス](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)

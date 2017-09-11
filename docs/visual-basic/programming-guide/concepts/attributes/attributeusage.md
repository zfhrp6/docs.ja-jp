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
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c91f2686a03d2590e1aaf166d27c49744bb13c9b
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="attributeusage-visual-basic"></a><span data-ttu-id="f5e88-102">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5e88-102">AttributeUsage (Visual Basic)</span></span>
<span data-ttu-id="f5e88-103">カスタム属性クラスの使用方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="f5e88-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="f5e88-104">`AttributeUsage`新しい属性を適用する方法を制御するカスタム属性の定義に適用できる属性です。</span><span class="sxs-lookup"><span data-stu-id="f5e88-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="f5e88-105">既定の設定は、明示的に適用されるときに、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f5e88-105">The default settings look like this when applied explicitly:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="f5e88-106">この例では、`NewAttribute`クラスは、すべての属性を使用できるコード エンティティを適用して、エンティティごとに&1; 回だけ適用できます。</span><span class="sxs-lookup"><span data-stu-id="f5e88-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="f5e88-107">基本クラスに適用すると、派生クラスによって継承されます。</span><span class="sxs-lookup"><span data-stu-id="f5e88-107">It is inherited by derived classes when applied to a base class.</span></span>  
  
 <span data-ttu-id="f5e88-108">`AllowMultiple`と`Inherited`のため、このコードは、同じ効果を持ちます引数は省略できます。</span><span class="sxs-lookup"><span data-stu-id="f5e88-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="f5e88-109">最初の`AttributeUsage`引数の&1; つまたは複数の要素でなければなりません、<xref:System.AttributeTargets>列挙体</xref:System.AttributeTargets>。</span><span class="sxs-lookup"><span data-stu-id="f5e88-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="f5e88-110">複数のターゲット型は、次のように、OR 演算子と一緒にリンクされたことができます。</span><span class="sxs-lookup"><span data-stu-id="f5e88-110">Multiple target types can be linked together with the OR operator, like this:</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 <span data-ttu-id="f5e88-111">場合、`AllowMultiple`に設定されている引数`true`、次のように、単一のエンティティに結果の属性が複数回適用されます。</span><span class="sxs-lookup"><span data-stu-id="f5e88-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>  
  
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
  
 <span data-ttu-id="f5e88-112">ここで`MultiUseAttr`ため繰り返し適用できる`AllowMultiple`に設定されている`true`します。</span><span class="sxs-lookup"><span data-stu-id="f5e88-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="f5e88-113">複数の属性を適用する場合、両方の形式は有効です。</span><span class="sxs-lookup"><span data-stu-id="f5e88-113">Both formats shown for applying multiple attributes are valid.</span></span>  
  
 <span data-ttu-id="f5e88-114">場合`Inherited`に設定されている`false`、属性が指定されるクラスから派生したクラスによって継承されません。</span><span class="sxs-lookup"><span data-stu-id="f5e88-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="f5e88-115">例:</span><span class="sxs-lookup"><span data-stu-id="f5e88-115">For example:</span></span>  
  
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
  
 <span data-ttu-id="f5e88-116">ここで`Attr1`には適用されません`DClass`継承を使用しています。</span><span class="sxs-lookup"><span data-stu-id="f5e88-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5e88-117">コメント</span><span class="sxs-lookup"><span data-stu-id="f5e88-117">Remarks</span></span>  
 <span data-ttu-id="f5e88-118">`AttributeUsage`属性は、単一目的の属性 - 同じクラスに複数回適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="f5e88-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="f5e88-119">`AttributeUsage`<xref:System.AttributeUsageAttribute>。</xref:System.AttributeUsageAttribute>エイリアスします。</span><span class="sxs-lookup"><span data-stu-id="f5e88-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="f5e88-120">詳細については、次を参照してください。[属性 (Visual Basic) を使用してリフレクションによってへのアクセス](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)します。</span><span class="sxs-lookup"><span data-stu-id="f5e88-120">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5e88-121">例</span><span class="sxs-lookup"><span data-stu-id="f5e88-121">Example</span></span>  
 <span data-ttu-id="f5e88-122">次の例では、効果、`Inherited`と`AllowMultiple`への引数、`AttributeUsage`属性、およびクラスに適用されるカスタム属性を列挙する方法です。</span><span class="sxs-lookup"><span data-stu-id="f5e88-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>  
  
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
  
## <a name="sample-output"></a><span data-ttu-id="f5e88-123">出力例</span><span class="sxs-lookup"><span data-stu-id="f5e88-123">Sample Output</span></span>  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5e88-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5e88-124">See Also</span></span>  
 <span data-ttu-id="f5e88-125"><xref:System.Attribute></xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="f5e88-125"><xref:System.Attribute></span></span>   
 <span data-ttu-id="f5e88-126"><xref:System.Reflection></xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="f5e88-126"><xref:System.Reflection></span></span>   
<span data-ttu-id="f5e88-127"> [Visual Basic のプログラミング ガイド](../../../../visual-basic/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f5e88-127"> [Visual Basic Programming Guide](../../../../visual-basic/programming-guide/index.md) </span></span>  
<span data-ttu-id="f5e88-128"> [属性](https://msdn.microsoft.com/library/5x6cd29c) </span><span class="sxs-lookup"><span data-stu-id="f5e88-128"> [Attributes](https://msdn.microsoft.com/library/5x6cd29c) </span></span>  
<span data-ttu-id="f5e88-129"> [リフレクション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="f5e88-129"> [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span></span>  
<span data-ttu-id="f5e88-130"> [属性 (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span><span class="sxs-lookup"><span data-stu-id="f5e88-130"> [Attributes (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span></span>  
<span data-ttu-id="f5e88-131"> [カスタム属性 (Visual Basic) の作成](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="f5e88-131"> [Creating Custom Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md) </span></span>  
<span data-ttu-id="f5e88-132"> [リフレクション (Visual Basic) を使用して属性へのアクセス](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="f5e88-132"> [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)</span></span>

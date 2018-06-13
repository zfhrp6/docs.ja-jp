---
title: AttributeUsage (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: ae162c310511db160806501af895276a4a4bba5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643406"
---
# <a name="attributeusage-visual-basic"></a><span data-ttu-id="ae7d2-102">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae7d2-102">AttributeUsage (Visual Basic)</span></span>
<span data-ttu-id="ae7d2-103">カスタム属性クラスの使用方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="ae7d2-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="ae7d2-104">`AttributeUsage` は、カスタム属性の定義に適用して新しい属性の適用方法を制御できる属性です。</span><span class="sxs-lookup"><span data-stu-id="ae7d2-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="ae7d2-105">明示的に適用するときの既定の設定は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ae7d2-105">The default settings look like this when applied explicitly:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="ae7d2-106">この例では、属性にできる任意のコード エンティティに `NewAttribute` クラスを適用できますが、各エンティティに適用できるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="ae7d2-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="ae7d2-107">基底クラスに適用すると、派生クラスによって継承されます。</span><span class="sxs-lookup"><span data-stu-id="ae7d2-107">It is inherited by derived classes when applied to a base class.</span></span>  
  
 <span data-ttu-id="ae7d2-108">`AllowMultiple` 引数と `Inherited` 引数は省略できるので、次のコードは同じ効果を持ちます。</span><span class="sxs-lookup"><span data-stu-id="ae7d2-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="ae7d2-109">最初の `AttributeUsage` 引数は、<xref:System.AttributeTargets> 列挙型の 1 つまたは複数の要素でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="ae7d2-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="ae7d2-110">次のように、複数のターゲット型を OR 演算子で 1 つにまとめることができます。</span><span class="sxs-lookup"><span data-stu-id="ae7d2-110">Multiple target types can be linked together with the OR operator, like this:</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 <span data-ttu-id="ae7d2-111">`AllowMultiple` 引数を `true` に設定すると、次のように、結果の属性を 1 つのエンティティに複数回適用できます。</span><span class="sxs-lookup"><span data-stu-id="ae7d2-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>  
  
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
  
 <span data-ttu-id="ae7d2-112">この例では、`AllowMultiple` が `true` に設定されているので、`MultiUseAttr` を繰り返し適用できます。</span><span class="sxs-lookup"><span data-stu-id="ae7d2-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="ae7d2-113">示されているどちらの形式でも、複数の属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="ae7d2-113">Both formats shown for applying multiple attributes are valid.</span></span>  
  
 <span data-ttu-id="ae7d2-114">`Inherited` を `false` に設定すると、属性化されたクラスから派生するクラスは属性を継承しません。</span><span class="sxs-lookup"><span data-stu-id="ae7d2-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="ae7d2-115">例えば:</span><span class="sxs-lookup"><span data-stu-id="ae7d2-115">For example:</span></span>  
  
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
  
 <span data-ttu-id="ae7d2-116">この例では、`Attr1` は継承によって `DClass` に適用されません。</span><span class="sxs-lookup"><span data-stu-id="ae7d2-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae7d2-117">コメント</span><span class="sxs-lookup"><span data-stu-id="ae7d2-117">Remarks</span></span>  
 <span data-ttu-id="ae7d2-118">`AttributeUsage` 属性は、1 回だけ使用できる属性です。同じクラスに複数回適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="ae7d2-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="ae7d2-119">`AttributeUsage` は <xref:System.AttributeUsageAttribute> の別名です。</span><span class="sxs-lookup"><span data-stu-id="ae7d2-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="ae7d2-120">詳細については、「[リフレクションを使用した属性へのアクセス (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae7d2-120">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae7d2-121">例</span><span class="sxs-lookup"><span data-stu-id="ae7d2-121">Example</span></span>  
 <span data-ttu-id="ae7d2-122">次の例を見ると、`AttributeUsage` 属性に対する `Inherited` 引数と `AllowMultiple` 引数の効果、およびクラスに適用されているカスタム属性の列挙方法がわかります。</span><span class="sxs-lookup"><span data-stu-id="ae7d2-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>  
  
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
  
## <a name="sample-output"></a><span data-ttu-id="ae7d2-123">出力例</span><span class="sxs-lookup"><span data-stu-id="ae7d2-123">Sample Output</span></span>  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae7d2-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae7d2-124">See Also</span></span>  
 <xref:System.Attribute>  
 <xref:System.Reflection>  
 [<span data-ttu-id="ae7d2-125">Visual Basic プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="ae7d2-125">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="ae7d2-126">属性</span><span class="sxs-lookup"><span data-stu-id="ae7d2-126">Attributes</span></span>](../../../../standard/attributes/index.md)  
 [<span data-ttu-id="ae7d2-127">リフレクション (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae7d2-127">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="ae7d2-128">属性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae7d2-128">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)  
 [<span data-ttu-id="ae7d2-129">カスタム属性の作成 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae7d2-129">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [<span data-ttu-id="ae7d2-130">リフレクションを使用した属性へのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae7d2-130">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)

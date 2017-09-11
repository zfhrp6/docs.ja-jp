---
title: AttributeUsage (C#)
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 22c45568-9a6a-4c2f-8480-f38c1caa0a99
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c008c1a696e93bc3b756a926a046aa5a6942bc10
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="attributeusage-c"></a><span data-ttu-id="2fd66-102">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="2fd66-102">AttributeUsage (C#)</span></span>
<span data-ttu-id="2fd66-103">カスタム属性クラスの使用方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="2fd66-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="2fd66-104">`AttributeUsage` は、カスタム属性の定義に適用して新しい属性の適用方法を制御できる属性です。</span><span class="sxs-lookup"><span data-stu-id="2fd66-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="2fd66-105">明示的に適用するときの既定の設定は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2fd66-105">The default settings look like this when applied explicitly:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All,  
                   AllowMultiple = false,  
                   Inherited = true)]  
class NewAttribute : System.Attribute { }  
```  
  
 <span data-ttu-id="2fd66-106">この例では、属性にできる任意のコード エンティティに `NewAttribute` クラスを適用できますが、各エンティティに適用できるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="2fd66-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="2fd66-107">基底クラスに適用すると、派生クラスによって継承されます。</span><span class="sxs-lookup"><span data-stu-id="2fd66-107">It is inherited by derived classes when applied to a base class.</span></span>  
  
 <span data-ttu-id="2fd66-108">`AllowMultiple` 引数と `Inherited` 引数は省略できるので、次のコードは同じ効果を持ちます。</span><span class="sxs-lookup"><span data-stu-id="2fd66-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All)]  
class NewAttribute : System.Attribute { }  
```  
  
 <span data-ttu-id="2fd66-109">最初の `AttributeUsage` 引数は、<xref:System.AttributeTargets> 列挙型の 1 つまたは複数の要素でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="2fd66-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="2fd66-110">次のように、複数のターゲット型を OR 演算子で 1 つにまとめることができます。</span><span class="sxs-lookup"><span data-stu-id="2fd66-110">Multiple target types can be linked together with the OR operator, like this:</span></span>  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Property | AttributeTargets.Field)]  
class NewPropertyOrFieldAttribute : Attribute { }  
```  
  
 <span data-ttu-id="2fd66-111">`AllowMultiple` 引数を `true` に設定すると、次のように、結果の属性を 1 つのエンティティに複数回適用できます。</span><span class="sxs-lookup"><span data-stu-id="2fd66-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Class, AllowMultiple = true)]  
class MultiUseAttr : Attribute { }  
  
[MultiUseAttr]  
[MultiUseAttr]  
class Class1 { }  
  
[MultiUseAttr, MultiUseAttr]  
class Class2 { }  
```  
  
 <span data-ttu-id="2fd66-112">この例では、`AllowMultiple` が `true` に設定されているので、`MultiUseAttr` を繰り返し適用できます。</span><span class="sxs-lookup"><span data-stu-id="2fd66-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="2fd66-113">示されているどちらの形式でも、複数の属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="2fd66-113">Both formats shown for applying multiple attributes are valid.</span></span>  
  
 <span data-ttu-id="2fd66-114">`Inherited` を `false` に設定すると、属性化されたクラスから派生するクラスは属性を継承しません。</span><span class="sxs-lookup"><span data-stu-id="2fd66-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="2fd66-115">例:</span><span class="sxs-lookup"><span data-stu-id="2fd66-115">For example:</span></span>  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Class, Inherited = false)]  
class Attr1 : Attribute { }  
  
[Attr1]  
class BClass { }  
  
class DClass : BClass { }  
```  
  
 <span data-ttu-id="2fd66-116">この例では、`Attr1` は継承によって `DClass` に適用されません。</span><span class="sxs-lookup"><span data-stu-id="2fd66-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fd66-117">コメント</span><span class="sxs-lookup"><span data-stu-id="2fd66-117">Remarks</span></span>  
 <span data-ttu-id="2fd66-118">`AttributeUsage` 属性は、1 回だけ使用できる属性です。同じクラスに複数回適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="2fd66-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="2fd66-119">`AttributeUsage` は <xref:System.AttributeUsageAttribute> の別名です。</span><span class="sxs-lookup"><span data-stu-id="2fd66-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="2fd66-120">詳しくは、「[リフレクションを使用した属性へのアクセス (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2fd66-120">For more information, see [Accessing Attributes by Using Reflection (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fd66-121">例</span><span class="sxs-lookup"><span data-stu-id="2fd66-121">Example</span></span>  
 <span data-ttu-id="2fd66-122">次の例を見ると、`AttributeUsage` 属性に対する `Inherited` 引数と `AllowMultiple` 引数の効果、およびクラスに適用されているカスタム属性の列挙方法がわかります。</span><span class="sxs-lookup"><span data-stu-id="2fd66-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>  
  
```csharp  
using System;  

// Create some custom attributes:  
[AttributeUsage(System.AttributeTargets.Class, Inherited = false)]  
class A1 : System.Attribute { }  
  
[AttributeUsage(System.AttributeTargets.Class)]  
class A2 : System.Attribute { }  
  
[AttributeUsage(System.AttributeTargets.Class, AllowMultiple = true)]  
class A3 : System.Attribute { }  
  
// Apply custom attributes to classes:  
[A1, A2]  
class BaseClass { }  
  
[A3, A3]  
class DerivedClass : BaseClass { }  
  
public class TestAttributeUsage  
{  
    static void Main()  
    {  
        BaseClass b = new BaseClass();  
        DerivedClass d = new DerivedClass();  
  
        // Display custom attributes for each class.  
        Console.WriteLine("Attributes on Base Class:");  
        object[] attrs = b.GetType().GetCustomAttributes(true);  
        foreach (Attribute attr in attrs)  
        {  
            Console.WriteLine(attr);  
        }  
  
        Console.WriteLine("Attributes on Derived Class:");  
        attrs = d.GetType().GetCustomAttributes(true);  
        foreach (Attribute attr in attrs)  
        {  
            Console.WriteLine(attr);  
        }  
    }  
}  
```  
  
## <a name="sample-output"></a><span data-ttu-id="2fd66-123">出力例</span><span class="sxs-lookup"><span data-stu-id="2fd66-123">Sample Output</span></span>  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a><span data-ttu-id="2fd66-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="2fd66-124">See Also</span></span>  
 <span data-ttu-id="2fd66-125"><xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="2fd66-125"><xref:System.Attribute></span></span>   
 <span data-ttu-id="2fd66-126"><xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="2fd66-126"><xref:System.Reflection></span></span>   
 <span data-ttu-id="2fd66-127">[C# プログラミング ガイド](../../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="2fd66-127">[C# Programming Guide](../../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="2fd66-128">[属性](https://msdn.microsoft.com/library/5x6cd29c) </span><span class="sxs-lookup"><span data-stu-id="2fd66-128">[Attributes](https://msdn.microsoft.com/library/5x6cd29c) </span></span>  
 <span data-ttu-id="2fd66-129">[リフレクション (C#)](../../../../csharp/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="2fd66-129">[Reflection (C#)](../../../../csharp/programming-guide/concepts/reflection.md) </span></span>  
 <span data-ttu-id="2fd66-130">[属性](../../../../csharp/programming-guide/concepts/attributes/index.md) </span><span class="sxs-lookup"><span data-stu-id="2fd66-130">[Attributes](../../../../csharp/programming-guide/concepts/attributes/index.md) </span></span>  
 <span data-ttu-id="2fd66-131">[カスタム属性の作成 (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="2fd66-131">[Creating Custom Attributes (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md) </span></span>  
 [<span data-ttu-id="2fd66-132">リフレクションを使用した属性へのアクセス (C#)</span><span class="sxs-lookup"><span data-stu-id="2fd66-132">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)


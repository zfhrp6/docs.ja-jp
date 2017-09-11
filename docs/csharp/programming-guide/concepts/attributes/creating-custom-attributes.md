---
title: "カスタム属性の作成 (C#)"
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
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
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
ms.openlocfilehash: 8ae5084501a2dd60ae23c93bbdb52dcd44f3f3f7
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="565c2-102">カスタム属性の作成 (C#)</span><span class="sxs-lookup"><span data-stu-id="565c2-102">Creating Custom Attributes (C#)</span></span>
<span data-ttu-id="565c2-103">属性クラスを定義することで、独自のカスタム属性を作成できます。属性クラスは、<xref:System.Attribute> の直接的または間接的な派生クラスです。これにより、メタデータの中で属性の定義をすばやく簡単に特定できます。</span><span class="sxs-lookup"><span data-stu-id="565c2-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="565c2-104">型にそれを記述したプログラマーの名前でタグを付けるとします。</span><span class="sxs-lookup"><span data-stu-id="565c2-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="565c2-105">`Author` というカスタム属性クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="565c2-105">You might define a custom `Author` attribute class:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct)  
]  
public class Author : System.Attribute  
{  
    private string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
        version = 1.0;  
    }  
}  
```  
  
 <span data-ttu-id="565c2-106">クラス名は属性の名前の `Author` です。</span><span class="sxs-lookup"><span data-stu-id="565c2-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="565c2-107">このクラスは `System.Attribute` から派生しているので、カスタム属性クラスです。</span><span class="sxs-lookup"><span data-stu-id="565c2-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="565c2-108">コンストラクターのパラメーターはカスタム属性の位置指定パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="565c2-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="565c2-109">この例では、`name` が位置指定パラメーターになります。</span><span class="sxs-lookup"><span data-stu-id="565c2-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="565c2-110">パブリックな読み取り/書き込みフィールドまたはプロパティは名前付きパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="565c2-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="565c2-111">この場合は、`version` が唯一の名前付きパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="565c2-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="565c2-112">`AttributeUsage` 属性を使用して、クラスと `struct` の宣言に対してのみ `Author` 属性を有効にしていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="565c2-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="565c2-113">この新しい属性の使用方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="565c2-113">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="565c2-114">`AttributeUsage` には名前付きパラメーター `AllowMultiple` があります。これを使用すると、カスタム属性が 1 回しか指定できない属性か、または複数回指定できる属性かを設定できます。</span><span class="sxs-lookup"><span data-stu-id="565c2-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="565c2-115">次のコード例では、複数回指定できる属性が作成されます。</span><span class="sxs-lookup"><span data-stu-id="565c2-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 <span data-ttu-id="565c2-116">次のコード例では、同じ型の複数の属性が 1 つのクラスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="565c2-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="565c2-117">属性クラスにプロパティが含まれている場合、そのプロパティは読み取り/書き込み可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="565c2-117">If your attribute class contains a property, that property must be read-write.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="565c2-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="565c2-118">See Also</span></span>  
 <span data-ttu-id="565c2-119"><xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="565c2-119"><xref:System.Reflection></span></span>   
 <span data-ttu-id="565c2-120">[C# プログラミング ガイド](../../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="565c2-120">[C# Programming Guide](../../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="565c2-121">[カスタム属性の記述](../../../../standard/attributes/writing-custom-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="565c2-121">[Writing Custom Attributes](../../../../standard/attributes/writing-custom-attributes.md) </span></span>  
 <span data-ttu-id="565c2-122">[リフレクション (C#)](../../../../csharp/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="565c2-122">[Reflection (C#)](../../../../csharp/programming-guide/concepts/reflection.md) </span></span>  
 <span data-ttu-id="565c2-123">[属性 (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md) </span><span class="sxs-lookup"><span data-stu-id="565c2-123">[Attributes (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md) </span></span>  
 <span data-ttu-id="565c2-124">[リフレクションを使用した属性へのアクセス (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md) </span><span class="sxs-lookup"><span data-stu-id="565c2-124">[Accessing Attributes by Using Reflection (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md) </span></span>  
 [<span data-ttu-id="565c2-125">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="565c2-125">AttributeUsage (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)


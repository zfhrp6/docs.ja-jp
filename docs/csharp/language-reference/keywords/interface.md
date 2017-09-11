---
title: "インターフェイス (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- interface_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
caps.latest.revision: 29
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 126e674a2c56f04f54f35a011c24ebf0f713ee8d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="interface-c-reference"></a><span data-ttu-id="24194-102">インターフェイス (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="24194-102">interface (C# Reference)</span></span>
<span data-ttu-id="24194-103">インターフェイスには、[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)、[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)、[イベント](../../../csharp/programming-guide/events/index.md)、[インデクサー](../../../csharp/programming-guide/indexers/index.md)のシグネチャのみが含まれています。</span><span class="sxs-lookup"><span data-stu-id="24194-103">An interface contains only the signatures of [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [events](../../../csharp/programming-guide/events/index.md) or [indexers](../../../csharp/programming-guide/indexers/index.md).</span></span> <span data-ttu-id="24194-104">インターフェイスを実装するクラスまたは構造体は、インターフェイス定義で指定されているインターフェイスのメンバーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24194-104">A class or struct that implements the interface must implement the members of the interface that are specified in the interface definition.</span></span> <span data-ttu-id="24194-105">次の例の `ImplementationClass` クラスは、`SampleMethod` を返す、パラメーターのない `void` メソッドを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24194-105">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>  
  
 <span data-ttu-id="24194-106">使用例を含む詳細については、「[インターフェイス](../../../csharp/programming-guide/interfaces/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24194-106">For more information and examples, see [Interfaces](../../../csharp/programming-guide/interfaces/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="24194-107">例</span><span class="sxs-lookup"><span data-stu-id="24194-107">Example</span></span>  
 <span data-ttu-id="24194-108">[!code-cs[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="24194-108">[!code-cs[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]</span></span>  
  
 <span data-ttu-id="24194-109">インターフェイスは、名前空間またはクラスのメンバーであり、次のメンバーのシグネチャを含むことができます。</span><span class="sxs-lookup"><span data-stu-id="24194-109">An interface can be a member of a namespace or a class and can contain signatures of the following members:</span></span>  
  
-   [<span data-ttu-id="24194-110">メソッド</span><span class="sxs-lookup"><span data-stu-id="24194-110">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="24194-111">プロパティ</span><span class="sxs-lookup"><span data-stu-id="24194-111">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [<span data-ttu-id="24194-112">インデクサー</span><span class="sxs-lookup"><span data-stu-id="24194-112">Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [<span data-ttu-id="24194-113">イベント</span><span class="sxs-lookup"><span data-stu-id="24194-113">Events</span></span>](../../../csharp/language-reference/keywords/event.md)  
  
 <span data-ttu-id="24194-114">インターフェイスは、1 つ以上の基底インターフェイスから継承できます。</span><span class="sxs-lookup"><span data-stu-id="24194-114">An interface can inherit from one or more base interfaces.</span></span>  
  
 <span data-ttu-id="24194-115">基本型のリストに基底クラスとインターフェイスが含まれる場合は、基底クラスがリストの最初に表示されます。</span><span class="sxs-lookup"><span data-stu-id="24194-115">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>  
  
 <span data-ttu-id="24194-116">インターフェイスを実装するクラスは、そのインターフェイスのメンバーを明示的に実装できます。</span><span class="sxs-lookup"><span data-stu-id="24194-116">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="24194-117">明示的に実装されているメンバーには、クラス インスタンスではアクセスできません。インターフェイスのインスタンスを使用した場合にのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="24194-117">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span>  
  
 <span data-ttu-id="24194-118">明示的なインターフェイスの実装の詳細とコード例については、「[明示的なインターフェイスの実装](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24194-118">For more details and code examples on explicit interface implementation, see [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="24194-119">例</span><span class="sxs-lookup"><span data-stu-id="24194-119">Example</span></span>  
 <span data-ttu-id="24194-120">ここでは、インターフェイスの実装例を示します。</span><span class="sxs-lookup"><span data-stu-id="24194-120">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="24194-121">この例では、インターフェイスにプロパティ宣言が含まれ、クラスに実装が含まれます。</span><span class="sxs-lookup"><span data-stu-id="24194-121">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="24194-122">`IPoint` を実装するクラスのインスタンスには、整数プロパティ `x` および `y` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="24194-122">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>  
  
 <span data-ttu-id="24194-123">[!code-cs[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="24194-123">[!code-cs[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="24194-124">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="24194-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="24194-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="24194-125">See Also</span></span>  
 <span data-ttu-id="24194-126">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="24194-126">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="24194-127">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="24194-127">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="24194-128">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="24194-128">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="24194-129">[参照型](../../../csharp/language-reference/keywords/reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="24194-129">[Reference Types](../../../csharp/language-reference/keywords/reference-types.md) </span></span>  
 <span data-ttu-id="24194-130">[インターフェイス](../../../csharp/programming-guide/interfaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="24194-130">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span></span>  
 <span data-ttu-id="24194-131">[プロパティの使用](../../../csharp/programming-guide/classes-and-structs/using-properties.md) </span><span class="sxs-lookup"><span data-stu-id="24194-131">[Using Properties](../../../csharp/programming-guide/classes-and-structs/using-properties.md) </span></span>  
 <span data-ttu-id="24194-132">[インデクサーの使用](../../../csharp/programming-guide/indexers/using-indexers.md) </span><span class="sxs-lookup"><span data-stu-id="24194-132">[Using Indexers](../../../csharp/programming-guide/indexers/using-indexers.md) </span></span>  
 <span data-ttu-id="24194-133">[class](../../../csharp/language-reference/keywords/class.md) </span><span class="sxs-lookup"><span data-stu-id="24194-133">[class](../../../csharp/language-reference/keywords/class.md) </span></span>  
 <span data-ttu-id="24194-134">[struct](../../../csharp/language-reference/keywords/struct.md) </span><span class="sxs-lookup"><span data-stu-id="24194-134">[struct](../../../csharp/language-reference/keywords/struct.md) </span></span>  
 [<span data-ttu-id="24194-135">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="24194-135">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)


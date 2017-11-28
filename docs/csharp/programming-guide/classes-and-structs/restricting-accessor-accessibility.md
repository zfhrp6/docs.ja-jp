---
title: "アクセサーのアクセシビリティの制限 (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accesibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a4905885323f59d8b8b2654a5331e02054334398
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a><span data-ttu-id="2b30a-102">アクセサーのアクセシビリティの制限 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="2b30a-102">Restricting Accessor Accessibility (C# Programming Guide)</span></span>
<span data-ttu-id="2b30a-103">プロパティまたはインデクサーの [get](../../../csharp/language-reference/keywords/get.md) および [set](../../../csharp/language-reference/keywords/set.md) 部分は、*アクセサー*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="2b30a-103">The [get](../../../csharp/language-reference/keywords/get.md) and [set](../../../csharp/language-reference/keywords/set.md) portions of a property or indexer are called *accessors*.</span></span> <span data-ttu-id="2b30a-104">既定では、これらのアクセサーは、それらが属するプロパティまたはインデクサーと同じ可視性またはアクセス レベルを持っています。</span><span class="sxs-lookup"><span data-stu-id="2b30a-104">By default these accessors have the same visibility, or access level: that of the property or indexer to which they belong.</span></span> <span data-ttu-id="2b30a-105">詳細については、「[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b30a-105">For more information, see [accessibility levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> <span data-ttu-id="2b30a-106">ただし、これらのアクセサーのいずれかにアクセスを制限すると便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="2b30a-106">However, it is sometimes useful to restrict access to one of these accessors.</span></span> <span data-ttu-id="2b30a-107">通常、これには、`set` アクセサーのアクセシビリティを制限しながら、`get` アクセサーのパブリック アクセスを維持する操作が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2b30a-107">Typically, this involves restricting the accessibility of the `set` accessor, while keeping the `get` accessor publicly accessible.</span></span> <span data-ttu-id="2b30a-108">例:</span><span class="sxs-lookup"><span data-stu-id="2b30a-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_1.cs)]  
  
 <span data-ttu-id="2b30a-109">この例では、`Name` というプロパティが `get` および `set` アクセサーを定義します。</span><span class="sxs-lookup"><span data-stu-id="2b30a-109">In this example, a property called `Name` defines a `get` and `set` accessor.</span></span> <span data-ttu-id="2b30a-110">`get` アクセサーは、プロパティ自体のアクセシビリティ レベル (この場合は `public`) を受け取り、同時に `set` アクセサーは、[protected](../../../csharp/language-reference/keywords/protected.md) アクセサー修飾子をアクセサー自体に適用することによって明示的に制限されます。</span><span class="sxs-lookup"><span data-stu-id="2b30a-110">The `get` accessor receives the accessibility level of the property itself, `public` in this case, while the `set` accessor is explicitly restricted by applying the [protected](../../../csharp/language-reference/keywords/protected.md) access modifier to the accessor itself.</span></span>  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a><span data-ttu-id="2b30a-111">アクセサーのアクセス修飾子の制限</span><span class="sxs-lookup"><span data-stu-id="2b30a-111">Restrictions on Access Modifiers on Accessors</span></span>  
 <span data-ttu-id="2b30a-112">プロパティまたはインデクサーでのアクセサー修飾子の使用は、以下の条件の対象になります。</span><span class="sxs-lookup"><span data-stu-id="2b30a-112">Using the accessor modifiers on properties or indexers is subject to these conditions:</span></span>  
  
-   <span data-ttu-id="2b30a-113">インターフェイスまたは明示的な [interface](../../../csharp/language-reference/keywords/interface.md) メンバーの実装でアクセサー修飾子を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="2b30a-113">You cannot use accessor modifiers on an interface or an explicit [interface](../../../csharp/language-reference/keywords/interface.md) member implementation.</span></span>  
  
-   <span data-ttu-id="2b30a-114">アクセサー修飾子は、プロパティまたはインデクサーに `set` と `get` アクセサーの両方がある場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="2b30a-114">You can use accessor modifiers only if the property or indexer has both `set` and `get` accessors.</span></span> <span data-ttu-id="2b30a-115">この場合、修飾子は、2 つのアクセサーのいずれかでのみ許可されます。</span><span class="sxs-lookup"><span data-stu-id="2b30a-115">In this case, the modifier is permitted on one only of the two accessors.</span></span>  
  
-   <span data-ttu-id="2b30a-116">プロパティまたはインデクサーに [override](../../../csharp/language-reference/keywords/override.md) 修飾子がある場合は、アクセサー修飾子はオーバーライドされるアクセサーのアクセサー (存在する場合) と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b30a-116">If the property or indexer has an [override](../../../csharp/language-reference/keywords/override.md) modifier, the accessor modifier must match the accessor of the overridden accessor, if any.</span></span>  
  
-   <span data-ttu-id="2b30a-117">アクセサーのアクセシビリティ レベルは、プロパティまたはインデクサー自体のアクセシビリティ レベルよりも制限されていなければなりません</span><span class="sxs-lookup"><span data-stu-id="2b30a-117">The accessibility level on the accessor must be more restrictive than the accessibility level on the property or indexer itself.</span></span>  
  
## <a name="access-modifiers-on-overriding-accessors"></a><span data-ttu-id="2b30a-118">オーバーライドするアクセサーのアクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="2b30a-118">Access Modifiers on Overriding Accessors</span></span>  
 <span data-ttu-id="2b30a-119">プロパティまたはインデクサーをオーバーライドする場合は、オーバーライドされたアクセサーがオーバーライドするコードにアクセスできなければなりません。</span><span class="sxs-lookup"><span data-stu-id="2b30a-119">When you override a property or indexer, the overridden accessors must be accessible to the overriding code.</span></span> <span data-ttu-id="2b30a-120">プロパティ/インデクサーの両方のアクセシビリティ レベル、およびアクセサーのアクセシビリティレベルが、対応するオーバーライドされるプロパティ/インデクサーおよびアクセサーと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b30a-120">Also, the accessibility level of both the property/indexer, and that of the accessors must match the corresponding overridden property/indexer and the accessors.</span></span> <span data-ttu-id="2b30a-121">例:</span><span class="sxs-lookup"><span data-stu-id="2b30a-121">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_2.cs)]  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="2b30a-122">インターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="2b30a-122">Implementing Interfaces</span></span>  
 <span data-ttu-id="2b30a-123">アクセサーを使用してインターフェイスを実装する場合、アクセサーがアクセス修飾子を持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="2b30a-123">When you use an accessor to implement an interface, the accessor may not have an access modifier.</span></span> <span data-ttu-id="2b30a-124">ただし、`get` などの 1 つのアクセサーを使用してインターフェイスを実装する場合、他のアクセサーは、次の例のように、アクセス修飾子を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="2b30a-124">However, if you implement the interface using one accessor, such as `get`, the other accessor can have an access modifier, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_3.cs)]  
  
## <a name="accessor-accessibility-domain"></a><span data-ttu-id="2b30a-125">アクセサー アクセシビリティ ドメイン</span><span class="sxs-lookup"><span data-stu-id="2b30a-125">Accessor Accessibility Domain</span></span>  
 <span data-ttu-id="2b30a-126">アクセサーでアクセス修飾子を使用する場合、アクセサーの[アクセシビリティ ドメイン](../../../csharp/language-reference/keywords/accessibility-domain.md)はこの修飾子によって決まります。</span><span class="sxs-lookup"><span data-stu-id="2b30a-126">If you use an access modifier on the accessor, the [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md) of the accessor is determined by this modifier.</span></span>  
  
 <span data-ttu-id="2b30a-127">アクセサーでアクセス修飾子を使用しなかった場合、アクセサーのアクセシビリティ ドメインは、プロパティまたはインデクサーのアクセシビリティ レベルによって決まります。</span><span class="sxs-lookup"><span data-stu-id="2b30a-127">If you did not use an access modifier on the accessor, the accessibility domain of the accessor is determined by the accessibility level of the property or indexer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b30a-128">例</span><span class="sxs-lookup"><span data-stu-id="2b30a-128">Example</span></span>  
 <span data-ttu-id="2b30a-129">次の例は、`BaseClass`、`DerivedClass`、および `MainClass` という 3 つのクラスを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="2b30a-129">The following example contains three classes, `BaseClass`, `DerivedClass`, and `MainClass`.</span></span> <span data-ttu-id="2b30a-130">すべてのクラスの `BaseClass`、`Name`、`Id` に 2 つのプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="2b30a-130">There are two properties on the `BaseClass`, `Name` and `Id` on both classes.</span></span> <span data-ttu-id="2b30a-131">この例は、[protected](../../../csharp/language-reference/keywords/protected.md) や [private](../../../csharp/language-reference/keywords/private.md) などの制限アクセス修飾子を使用するときに、`BaseClass` のプロパティ `Id` によって `DerivedClass` のプロパティ `Id` を非表示にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="2b30a-131">The example demonstrates how the property `Id` on `DerivedClass` can be hidden by the property `Id` on `BaseClass` when you use a restrictive access modifier such as [protected](../../../csharp/language-reference/keywords/protected.md) or [private](../../../csharp/language-reference/keywords/private.md).</span></span> <span data-ttu-id="2b30a-132">そのため、このプロパティに値を割り当てるときには、代わりに `BaseClass` クラスのプロパティが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2b30a-132">Therefore, when you assign values to this property, the property on the `BaseClass` class is called instead.</span></span> <span data-ttu-id="2b30a-133">[public](../../../csharp/language-reference/keywords/public.md) によってアクセス修飾子を置き換えると、プロパティがアクセス可能になります。</span><span class="sxs-lookup"><span data-stu-id="2b30a-133">Replacing the access modifier by [public](../../../csharp/language-reference/keywords/public.md) will make the property accessible.</span></span>  
  
 <span data-ttu-id="2b30a-134">この例はまた、`DerivedClass` の `Name` プロパティの `set` アクセサー上の `private` や `protected` などの制限されるアクセス修飾子が、アクセサーへのアクセスを防ぎ、アクセサーに割り当てたときにエラーが生成されることも示しています。</span><span class="sxs-lookup"><span data-stu-id="2b30a-134">The example also demonstrates that a restrictive access modifier, such as `private` or `protected`, on the `set` accessor of the `Name` property in `DerivedClass` prevents access to the accessor and generates an error when you assign to it.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_4.cs)]  
  
## <a name="comments"></a><span data-ttu-id="2b30a-135">コメント</span><span class="sxs-lookup"><span data-stu-id="2b30a-135">Comments</span></span>  
 <span data-ttu-id="2b30a-136">宣言 `new private string Id` を `new public string Id` によって置き換えた場合、次の出力を取得します。</span><span class="sxs-lookup"><span data-stu-id="2b30a-136">Notice that if you replace the declaration `new private string Id` by `new public string Id`, you get the output:</span></span>  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a><span data-ttu-id="2b30a-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b30a-137">See Also</span></span>  
 [<span data-ttu-id="2b30a-138">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="2b30a-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2b30a-139">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2b30a-139">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="2b30a-140">インデクサー</span><span class="sxs-lookup"><span data-stu-id="2b30a-140">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="2b30a-141">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="2b30a-141">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)

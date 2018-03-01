---
title: "override (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 807fae02ca4e6f616c77877cc8815405baaf8428
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="override-c-reference"></a><span data-ttu-id="e74b5-102">override (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="e74b5-102">override (C# Reference)</span></span>
<span data-ttu-id="e74b5-103">`override` 修飾子は、継承したメソッド、プロパティ、インデクサー、またはイベントの抽象実装または仮想実装を拡張したり修飾したりする際に必要です。</span><span class="sxs-lookup"><span data-stu-id="e74b5-103">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e74b5-104">例</span><span class="sxs-lookup"><span data-stu-id="e74b5-104">Example</span></span>  
 <span data-ttu-id="e74b5-105">この例では、`Square` クラスが `Area` のオーバーライドされる実装を提供する必要があります。これは、`Area` が抽象 `ShapesClass` から継承されているためです。</span><span class="sxs-lookup"><span data-stu-id="e74b5-105">In this example, the `Square` class must provide an overridden implementation of `Area` because `Area` is inherited from the abstract `ShapesClass`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]  
  
 <span data-ttu-id="e74b5-106">`override` メソッドは、基底クラスから継承されるメンバーの新しい実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="e74b5-106">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="e74b5-107">`override` 宣言によってオーバーライドされるメソッドを、オーバーライドされる基本メソッドと言います。</span><span class="sxs-lookup"><span data-stu-id="e74b5-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="e74b5-108">オーバーライドされる基本メソッドには、`override` メソッドと同じシグネチャが必要です。</span><span class="sxs-lookup"><span data-stu-id="e74b5-108">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="e74b5-109">継承については、「[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e74b5-109">For information about inheritance, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span>  
  
 <span data-ttu-id="e74b5-110">非仮想メソッドまたは静的メソッドをオーバーライドすることはできません。</span><span class="sxs-lookup"><span data-stu-id="e74b5-110">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="e74b5-111">オーバーライドされる基本メソッドは、`virtual`、`abstract`、`override` のいずれかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="e74b5-111">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>  
  
 <span data-ttu-id="e74b5-112">`override` 宣言は、`virtual` メソッドのアクセシビリティを変更できません。</span><span class="sxs-lookup"><span data-stu-id="e74b5-112">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="e74b5-113">`override` メソッドと `virtual` メソッドの両方に、同じ[アクセス レベル修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)が必要です。</span><span class="sxs-lookup"><span data-stu-id="e74b5-113">Both the `override` method and the `virtual` method must have the same [access level modifier](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="e74b5-114">`override` メソッドの修飾に、修飾子 `new`、`static`、または `virtual` は使用できません。</span><span class="sxs-lookup"><span data-stu-id="e74b5-114">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>  
  
 <span data-ttu-id="e74b5-115">オーバーライドするプロパティの宣言では、継承されるプロパティとまったく同じアクセス修飾子、型、および名前を指定する必要があります。オーバーライドされるプロパティは、`virtual`、`abstract`、または `override` である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e74b5-115">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>  
  
 <span data-ttu-id="e74b5-116">`override` キーワードの使い方の詳細については、「[Override キーワードと New キーワードによるバージョン管理](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)」および「[Override キーワードと New キーワードを使用する場合について](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e74b5-116">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e74b5-117">例</span><span class="sxs-lookup"><span data-stu-id="e74b5-117">Example</span></span>  
 <span data-ttu-id="e74b5-118">この例では、`Employee` という基底クラスと、`SalesEmployee` という派生クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="e74b5-118">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="e74b5-119">`SalesEmployee` クラスには追加のプロパティ `salesbonus` があり、このプロパティを処理に含めるために、`CalculatePay` メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="e74b5-119">The `SalesEmployee` class includes an extra property, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="e74b5-120">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="e74b5-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e74b5-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="e74b5-121">See Also</span></span>  
 [<span data-ttu-id="e74b5-122">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="e74b5-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e74b5-123">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="e74b5-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e74b5-124">継承</span><span class="sxs-lookup"><span data-stu-id="e74b5-124">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [<span data-ttu-id="e74b5-125">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="e74b5-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e74b5-126">修飾子</span><span class="sxs-lookup"><span data-stu-id="e74b5-126">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="e74b5-127">abstract</span><span class="sxs-lookup"><span data-stu-id="e74b5-127">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
 [<span data-ttu-id="e74b5-128">virtual</span><span class="sxs-lookup"><span data-stu-id="e74b5-128">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)  
 [<span data-ttu-id="e74b5-129">new</span><span class="sxs-lookup"><span data-stu-id="e74b5-129">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="e74b5-130">ポリモーフィズム</span><span class="sxs-lookup"><span data-stu-id="e74b5-130">Polymorphism</span></span>](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)

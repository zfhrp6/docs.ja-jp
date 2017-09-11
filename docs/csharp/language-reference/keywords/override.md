---
title: "override (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- override
- override_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
caps.latest.revision: 26
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
ms.openlocfilehash: 0f5a87eaa5894b61187c379c92ad785336aa79b2
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="override-c-reference"></a><span data-ttu-id="50d8f-102">override (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="50d8f-102">override (C# Reference)</span></span>
<span data-ttu-id="50d8f-103">`override` 修飾子は、継承したメソッド、プロパティ、インデクサー、またはイベントの抽象実装または仮想実装を拡張したり修飾したりする際に必要です。</span><span class="sxs-lookup"><span data-stu-id="50d8f-103">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50d8f-104">例</span><span class="sxs-lookup"><span data-stu-id="50d8f-104">Example</span></span>  
 <span data-ttu-id="50d8f-105">この例では、`Square` クラスが `Area` のオーバーライドされる実装を提供する必要があります。これは、`Area` が抽象 `ShapesClass` から継承されているためです。</span><span class="sxs-lookup"><span data-stu-id="50d8f-105">In this example, the `Square` class must provide an overridden implementation of `Area` because `Area` is inherited from the abstract `ShapesClass`:</span></span>  
  
 <span data-ttu-id="50d8f-106">[!code-cs[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="50d8f-106">[!code-cs[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]</span></span>  
  
 <span data-ttu-id="50d8f-107">`override` メソッドは、基底クラスから継承されるメンバーの新しい実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="50d8f-107">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="50d8f-108">`override` 宣言によってオーバーライドされるメソッドを、オーバーライドされる基本メソッドと言います。</span><span class="sxs-lookup"><span data-stu-id="50d8f-108">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="50d8f-109">オーバーライドされる基本メソッドには、`override` メソッドと同じシグネチャが必要です。</span><span class="sxs-lookup"><span data-stu-id="50d8f-109">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="50d8f-110">継承については、「[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50d8f-110">For information about inheritance, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span>  
  
 <span data-ttu-id="50d8f-111">非仮想メソッドまたは静的メソッドをオーバーライドすることはできません。</span><span class="sxs-lookup"><span data-stu-id="50d8f-111">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="50d8f-112">オーバーライドされる基本メソッドは、`virtual`、`abstract`、`override` のいずれかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="50d8f-112">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>  
  
 <span data-ttu-id="50d8f-113">`override` 宣言は、`virtual` メソッドのアクセシビリティを変更できません。</span><span class="sxs-lookup"><span data-stu-id="50d8f-113">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="50d8f-114">`override` メソッドと `virtual` メソッドの両方に、同じ[アクセス レベル修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)が必要です。</span><span class="sxs-lookup"><span data-stu-id="50d8f-114">Both the `override` method and the `virtual` method must have the same [access level modifier](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="50d8f-115">`override` メソッドの修飾に、修飾子 `new`、`static`、または `virtual` は使用できません。</span><span class="sxs-lookup"><span data-stu-id="50d8f-115">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>  
  
 <span data-ttu-id="50d8f-116">オーバーライドするプロパティの宣言では、継承されるプロパティとまったく同じアクセス修飾子、型、および名前を指定する必要があります。オーバーライドされるプロパティは、`virtual`、`abstract`、または `override` である必要があります。</span><span class="sxs-lookup"><span data-stu-id="50d8f-116">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>  
  
 <span data-ttu-id="50d8f-117">`override` キーワードの使い方の詳細については、「[Override キーワードと New キーワードによるバージョン管理](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)」および「[Override キーワードと New キーワードを使用する場合について](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50d8f-117">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="50d8f-118">例</span><span class="sxs-lookup"><span data-stu-id="50d8f-118">Example</span></span>  
 <span data-ttu-id="50d8f-119">この例では、`Employee` という基底クラスと、`SalesEmployee` という派生クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="50d8f-119">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="50d8f-120">`SalesEmployee` クラスには追加のプロパティ `salesbonus` があり、このプロパティを処理に含めるために、`CalculatePay` メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="50d8f-120">The `SalesEmployee` class includes an extra property, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>  
  
 <span data-ttu-id="50d8f-121">[!code-cs[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="50d8f-121">[!code-cs[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="50d8f-122">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="50d8f-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="50d8f-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="50d8f-123">See Also</span></span>  
 <span data-ttu-id="50d8f-124">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="50d8f-124">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="50d8f-125">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="50d8f-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="50d8f-126">[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md) </span><span class="sxs-lookup"><span data-stu-id="50d8f-126">[Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md) </span></span>  
 <span data-ttu-id="50d8f-127">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="50d8f-127">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="50d8f-128">[修飾子](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="50d8f-128">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="50d8f-129">[abstract](../../../csharp/language-reference/keywords/abstract.md) </span><span class="sxs-lookup"><span data-stu-id="50d8f-129">[abstract](../../../csharp/language-reference/keywords/abstract.md) </span></span>  
 <span data-ttu-id="50d8f-130">[virtual](../../../csharp/language-reference/keywords/virtual.md) </span><span class="sxs-lookup"><span data-stu-id="50d8f-130">[virtual](../../../csharp/language-reference/keywords/virtual.md) </span></span>  
 <span data-ttu-id="50d8f-131">[new](../../../csharp/language-reference/keywords/new.md) </span><span class="sxs-lookup"><span data-stu-id="50d8f-131">[new](../../../csharp/language-reference/keywords/new.md) </span></span>  
 [<span data-ttu-id="50d8f-132">ポリモーフィズム</span><span class="sxs-lookup"><span data-stu-id="50d8f-132">Polymorphism</span></span>](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)


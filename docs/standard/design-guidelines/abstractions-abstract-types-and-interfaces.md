---
title: 抽象化 (抽象型およびインターフェイス)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5863b4ae9cad940e4dd47ef93e07763916427f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="abstractions-abstract-types-and-interfaces"></a><span data-ttu-id="bc26f-102">抽象化 (抽象型およびインターフェイス)</span><span class="sxs-lookup"><span data-stu-id="bc26f-102">Abstractions (Abstract Types and Interfaces)</span></span>
<span data-ttu-id="bc26f-103">抽象化では、コントラクトを記述、コントラクトの完全な実装は提供されませんする型です。</span><span class="sxs-lookup"><span data-stu-id="bc26f-103">An abstraction is a type that describes a contract but does not provide a full implementation of the contract.</span></span> <span data-ttu-id="bc26f-104">抽象化は通常インターフェイスまたは抽象クラスとして実装され、適切に定義された一連のコントラクトを実装する型の必要なセマンティクスを説明するリファレンス ドキュメントになります。</span><span class="sxs-lookup"><span data-stu-id="bc26f-104">Abstractions are usually implemented as abstract classes or interfaces, and they come with a well-defined set of reference documentation describing the required semantics of the types implementing the contract.</span></span> <span data-ttu-id="bc26f-105">.NET Framework における最も重要な抽象化のものが<xref:System.IO.Stream>、 <xref:System.Collections.Generic.IEnumerable%601>、および<xref:System.Object>です。</span><span class="sxs-lookup"><span data-stu-id="bc26f-105">Some of the most important abstractions in the .NET Framework include <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, and <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="bc26f-106">抽象化のコントラクトをサポートする具象型を実装して、フレームワーク Api のかかる (で動作している) でこの具象型を使用してフレームワークを拡張することができます、抽象化します。</span><span class="sxs-lookup"><span data-stu-id="bc26f-106">You can extend frameworks by implementing a concrete type that supports the contract of an abstraction and using this concrete type with framework APIs consuming (operating on) the abstraction.</span></span>  
  
 <span data-ttu-id="bc26f-107">時間のテストに耐えることができるわかりやすいで便利な抽象化は、デザインに非常に困難です。</span><span class="sxs-lookup"><span data-stu-id="bc26f-107">A meaningful and useful abstraction that is able to withstand the test of time is very difficult to design.</span></span> <span data-ttu-id="bc26f-108">メインの難易度は適切ないいえが少ないと、メンバーのセットを取得しています。</span><span class="sxs-lookup"><span data-stu-id="bc26f-108">The main difficulty is getting the right set of members, no more and no fewer.</span></span> <span data-ttu-id="bc26f-109">抽象化のメンバーが多すぎる場合は、難しいかを実装することが不可能になります。</span><span class="sxs-lookup"><span data-stu-id="bc26f-109">If an abstraction has too many members, it becomes difficult or even impossible to implement.</span></span> <span data-ttu-id="bc26f-110">約束されていた機能が少なすぎますメンバーがある場合に、多くの興味深いシナリオでは役に立たなくなります。</span><span class="sxs-lookup"><span data-stu-id="bc26f-110">If it has too few members for the promised functionality, it becomes useless in many interesting scenarios.</span></span>  
  
 <span data-ttu-id="bc26f-111">悪影響が多すぎますの抽象化フレームワークでは、フレームワークの使いやすさに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="bc26f-111">Too many abstractions in a framework also negatively affect usability of the framework.</span></span> <span data-ttu-id="bc26f-112">非常に具体的な実装との抽象型で動作している Api の大きい画像に適合する方法を理解することがなく抽象化を理解しにくいは多くの場合です。</span><span class="sxs-lookup"><span data-stu-id="bc26f-112">It is often quite difficult to understand an abstraction without understanding how it fits into the larger picture of the concrete implementations and the APIs operating on the abstraction.</span></span> <span data-ttu-id="bc26f-113">また、抽象化とそのメンバーの名前は抽象的に、する多くの場合にわかりにくいつかめない最初にそれらの使用より広範なコンテキストを理解することがなくです。</span><span class="sxs-lookup"><span data-stu-id="bc26f-113">Also, names of abstractions and their members are necessarily abstract, which often makes them cryptic and unapproachable without first understanding the broader context of their usage.</span></span>  
  
 <span data-ttu-id="bc26f-114">ただし、抽象化は、その他の機能拡張メカニズムできない多くの場合と一致する非常に強力な機能拡張を提供します。</span><span class="sxs-lookup"><span data-stu-id="bc26f-114">However, abstractions provide extremely powerful extensibility that the other extensibility mechanisms cannot often match.</span></span> <span data-ttu-id="bc26f-115">プラグインなど、多くのアーキテクチャのパターンの中核制御の反転 (IoC)、パイプライン、やなど。</span><span class="sxs-lookup"><span data-stu-id="bc26f-115">They are at the core of many architectural patterns, such as plug-ins, inversion of control (IoC), pipelines, and so on.</span></span> <span data-ttu-id="bc26f-116">フレームワークのテストの容易性のきわめて重要です。</span><span class="sxs-lookup"><span data-stu-id="bc26f-116">They are also extremely important for testability of frameworks.</span></span> <span data-ttu-id="bc26f-117">適切な抽象化を使用すれば、単体テストするために大量の依存関係を消去できます。</span><span class="sxs-lookup"><span data-stu-id="bc26f-117">Good abstractions make it possible to stub out heavy dependencies for the purpose of unit testing.</span></span> <span data-ttu-id="bc26f-118">要約すると、抽象化は、最新のオブジェクト指向フレームワークのいる豊富な機能を担当します。</span><span class="sxs-lookup"><span data-stu-id="bc26f-118">In summary, abstractions are responsible for the sought-after richness of the modern object-oriented frameworks.</span></span>  
  
 <span data-ttu-id="bc26f-119">**X しないで**いくつかの具体的な実装と、抽象化を使用する Api を開発してテストする場合を除き、抽象化を提供します。</span><span class="sxs-lookup"><span data-stu-id="bc26f-119">**X DO NOT** provide abstractions unless they are tested by developing several concrete implementations and APIs consuming the abstractions.</span></span>  
  
 <span data-ttu-id="bc26f-120">**✓ しないで**抽象化を設計するときは、抽象クラスとインターフェイス間慎重に選択します。</span><span class="sxs-lookup"><span data-stu-id="bc26f-120">**✓ DO** choose carefully between an abstract class and an interface when designing an abstraction.</span></span>  
  
 <span data-ttu-id="bc26f-121">**✓ を検討してください**抽象クラスの具象実装のテストの参照を提供します。</span><span class="sxs-lookup"><span data-stu-id="bc26f-121">**✓ CONSIDER** providing reference tests for concrete implementations of abstractions.</span></span> <span data-ttu-id="bc26f-122">そのようなテストは、実装では、コントラクトを正しく実装するかどうかをテストするユーザーを許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc26f-122">Such tests should allow users to test whether their implementations correctly implement the contract.</span></span>  
  
 <span data-ttu-id="bc26f-123">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="bc26f-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="bc26f-124">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="bc26f-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc26f-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc26f-125">See Also</span></span>  
 [<span data-ttu-id="bc26f-126">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="bc26f-126">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="bc26f-127">機能拡張のデザイン</span><span class="sxs-lookup"><span data-stu-id="bc26f-127">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)

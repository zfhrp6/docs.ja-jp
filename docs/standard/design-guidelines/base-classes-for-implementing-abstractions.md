---
title: "抽象化の実装用の基本クラス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6c8cd779dba0e7ce559e29af7b16bf04b3d0dc2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="base-classes-for-implementing-abstractions"></a><span data-ttu-id="b7d18-102">抽象化の実装用の基本クラス</span><span class="sxs-lookup"><span data-stu-id="b7d18-102">Base Classes for Implementing Abstractions</span></span>
<span data-ttu-id="b7d18-103">厳密には、別のクラスがそこから派生したときに、クラスは、基本クラスになります。</span><span class="sxs-lookup"><span data-stu-id="b7d18-103">Strictly speaking, a class becomes a base class when another class is derived from it.</span></span> <span data-ttu-id="b7d18-104">このセクションの目的で、基本クラスが主に、共通の抽象化を指定するか、一部を再利用する他のクラスの既定の実装が継承に設計されたクラスです。</span><span class="sxs-lookup"><span data-stu-id="b7d18-104">For the purpose of this section, however, a base class is a class designed mainly to provide a common abstraction or for other classes to reuse some default implementation though inheritance.</span></span> <span data-ttu-id="b7d18-105">基本クラスは、通常、階層のルートに抽象化と下部にいくつかのカスタム実装の間の継承階層の途中で配置できます。</span><span class="sxs-lookup"><span data-stu-id="b7d18-105">Base classes usually sit in the middle of inheritance hierarchies, between an abstraction at the root of a hierarchy and several custom implementations at the bottom.</span></span>  
  
 <span data-ttu-id="b7d18-106">これらは、抽象化を実装するための実装のヘルパーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="b7d18-106">They serve as implementation helpers for implementing abstractions.</span></span> <span data-ttu-id="b7d18-107">たとえば、項目の順序付けられたコレクションのフレームワークの抽象化の 1 つは、<xref:System.Collections.Generic.IList%601>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="b7d18-107">For example, one of the Framework’s abstractions for ordered collections of items is the <xref:System.Collections.Generic.IList%601> interface.</span></span> <span data-ttu-id="b7d18-108">実装する<xref:System.Collections.Generic.IList%601>は重要でとなるため、フレームワーク、いくつかの基底クラスなど<xref:System.Collections.ObjectModel.Collection%601>と<xref:System.Collections.ObjectModel.KeyedCollection%602>、カスタム コレクションを実装するためのヘルパーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="b7d18-108">Implementing <xref:System.Collections.Generic.IList%601> is not trivial, and therefore the Framework provides several base classes, such as <xref:System.Collections.ObjectModel.Collection%601> and <xref:System.Collections.ObjectModel.KeyedCollection%602>, which serve as helpers for implementing custom collections.</span></span>  
  
 <span data-ttu-id="b7d18-109">基底クラスは通常、単独で抽象化として機能するのに適したが多すぎる実装を格納する傾向があるためです。</span><span class="sxs-lookup"><span data-stu-id="b7d18-109">Base classes are usually not suited to serve as abstractions by themselves, because they tend to contain too much implementation.</span></span> <span data-ttu-id="b7d18-110">たとえば、`Collection<T>`基底クラスには、非ジェネリックによって実装されているファクトに関連する実装の多数が含まれている`IList`(非ジェネリック コレクションをより深く統合) へのインターフェイスし、であることを項目のコレクションが格納されています。そのフィールドのいずれかでメモリ。</span><span class="sxs-lookup"><span data-stu-id="b7d18-110">For example, the `Collection<T>` base class contains lots of implementation related to the fact that it implements the nongeneric `IList` interface (to integrate better with nongeneric collections) and to the fact that it is a collection of items stored in memory in one of its fields.</span></span>  
  
 <span data-ttu-id="b7d18-111">前述のとおり、基本クラスは抽象化を実装する必要があるユーザーの貴重なヘルプを提供することができますが、同時に可能性がある重大な責任です。</span><span class="sxs-lookup"><span data-stu-id="b7d18-111">As previously discussed, base classes can provide invaluable help for users who need to implement abstractions, but at the same time they can be a significant liability.</span></span> <span data-ttu-id="b7d18-112">継承階層の深さを向上し、ので概念的フレームワークが複雑になる、サーフェス領域を追加します。</span><span class="sxs-lookup"><span data-stu-id="b7d18-112">They add surface area and increase the depth of inheritance hierarchies and so conceptually complicate the framework.</span></span> <span data-ttu-id="b7d18-113">そのため、フレームワークのユーザーに重要な価値を提供する場合にのみ、基本クラスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="b7d18-113">Therefore, base classes should be used only if they provide significant value to the users of the framework.</span></span> <span data-ttu-id="b7d18-114">これらを基本クラスから継承の代わりに内部実装に大文字に委任する必要があることを検討する framework の実装時にのみ値を提供する場合に避ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7d18-114">They should be avoided if they provide value only to the implementers of the framework, in which case delegation to an internal implementation instead of inheritance from a base class should be strongly considered.</span></span>  
  
 <span data-ttu-id="b7d18-115">**✓ を検討してください**抽象メンバーが含まれている場合でも、基本クラスの抽象です。</span><span class="sxs-lookup"><span data-stu-id="b7d18-115">**✓ CONSIDER** making base classes abstract even if they don’t contain any abstract members.</span></span> <span data-ttu-id="b7d18-116">これをユーザーに明確に伝達するクラスは継承するためだけに設計されています。</span><span class="sxs-lookup"><span data-stu-id="b7d18-116">This clearly communicates to the users that the class is designed solely to be inherited from.</span></span>  
  
 <span data-ttu-id="b7d18-117">**✓ を検討してください**主要なシナリオの種類から別の名前空間の基本クラスを配置することです。</span><span class="sxs-lookup"><span data-stu-id="b7d18-117">**✓ CONSIDER** placing base classes in a separate namespace from the mainline scenario types.</span></span> <span data-ttu-id="b7d18-118">定義では、基底クラスは高度な機能拡張シナリオのためのものし、そのため、大半のユーザーに重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="b7d18-118">By definition, base classes are intended for advanced extensibility scenarios and therefore are not interesting to the majority of users.</span></span>  
  
 <span data-ttu-id="b7d18-119">**避け x**クラスは、パブリック Api で使用する場合は、"Base"サフィックスを持つ基本クラスを名前付けします。</span><span class="sxs-lookup"><span data-stu-id="b7d18-119">**X AVOID** naming base classes with a "Base" suffix if the class is intended for use in public APIs.</span></span>  
  
 <span data-ttu-id="b7d18-120">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="b7d18-120">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b7d18-121">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="b7d18-121">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7d18-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7d18-122">See Also</span></span>  
 [<span data-ttu-id="b7d18-123">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="b7d18-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="b7d18-124">機能拡張のための設計</span><span class="sxs-lookup"><span data-stu-id="b7d18-124">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)

---
title: インターフェイスのデザイン
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dea5877f952869d5c84d6019617fcdc52d8ee0a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573040"
---
# <a name="interface-design"></a><span data-ttu-id="3c054-102">インターフェイスのデザイン</span><span class="sxs-lookup"><span data-stu-id="3c054-102">Interface Design</span></span>
<span data-ttu-id="3c054-103">ほとんどの Api は、クラスと構造体を使用して、最適なモデル化、ある場合、またはインターフェイスがより適切な唯一のオプションします。</span><span class="sxs-lookup"><span data-stu-id="3c054-103">Although most APIs are best modeled using classes and structs, there are cases in which interfaces are more appropriate or are the only option.</span></span>  
  
 <span data-ttu-id="3c054-104">CLR は多重継承をサポートしていません (つまり、CLR クラスは継承できません 1 つ以上の基底クラスから) が、基本クラスから継承するだけでなく、1 つまたは複数のインターフェイスを実装する型。</span><span class="sxs-lookup"><span data-stu-id="3c054-104">The CLR does not support multiple inheritance (i.e., CLR classes cannot inherit from more than one base class), but it does allow types to implement one or more interfaces in addition to inheriting from a base class.</span></span> <span data-ttu-id="3c054-105">そのため、インターフェイスは、複数の継承の効果を実現するためによく使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c054-105">Therefore, interfaces are often used to achieve the effect of multiple inheritance.</span></span> <span data-ttu-id="3c054-106">たとえば、<xref:System.IDisposable>インターフェイスにより、参加する継承階層の独立した disposability をサポートする型です。</span><span class="sxs-lookup"><span data-stu-id="3c054-106">For example, <xref:System.IDisposable> is an interface that allows types to support disposability independent of any other inheritance hierarchy in which they want to participate.</span></span>  
  
 <span data-ttu-id="3c054-107">どのを定義するインターフェイスが適切な他の状況は、いくつかの値の型を含む、いくつかの種類でサポートできる共通のインターフェイスを作成するのにです。</span><span class="sxs-lookup"><span data-stu-id="3c054-107">The other situation in which defining an interface is appropriate is in creating a common interface that can be supported by several types, including some value types.</span></span> <span data-ttu-id="3c054-108">値の型が以外の値の型から継承できません<xref:System.ValueType>インターフェイスを実装することができますが、共通の基本型を提供するための唯一のオプションは、インターフェイスを使用します。</span><span class="sxs-lookup"><span data-stu-id="3c054-108">Value types cannot inherit from types other than <xref:System.ValueType>, but they can implement interfaces, so using an interface is the only option in order to provide a common base type.</span></span>  
  
 <span data-ttu-id="3c054-109">**✓ しないで**いくつかの一般的な API 値の型を含む型のセットでサポートする必要がある場合は、インターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="3c054-109">**✓ DO** define an interface if you need some common API to be supported by a set of types that includes value types.</span></span>  
  
 <span data-ttu-id="3c054-110">**✓ を検討してください**既に他の型を継承する型でその機能をサポートする必要がある場合は、インターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="3c054-110">**✓ CONSIDER** defining an interface if you need to support its functionality on types that already inherit from some other type.</span></span>  
  
 <span data-ttu-id="3c054-111">**避け x**マーカー インターフェイス (メンバーを持たないインターフェイス) を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c054-111">**X AVOID** using marker interfaces (interfaces with no members).</span></span>  
  
 <span data-ttu-id="3c054-112">特定の特性 (マーカー) を持つものとしてクラスをマークする必要がある場合は、一般に、インターフェイスではなく、カスタム属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c054-112">If you need to mark a class as having a specific characteristic (marker), in general, use a custom attribute rather than an interface.</span></span>  
  
 <span data-ttu-id="3c054-113">**✓ しないで**インターフェイスの実装は、少なくとも 1 つの型を提供します。</span><span class="sxs-lookup"><span data-stu-id="3c054-113">**✓ DO** provide at least one type that is an implementation of an interface.</span></span>  
  
 <span data-ttu-id="3c054-114">これにより、インターフェイスの設計を検証するを行っています。</span><span class="sxs-lookup"><span data-stu-id="3c054-114">Doing this helps to validate the design of the interface.</span></span> <span data-ttu-id="3c054-115">たとえば、<xref:System.Collections.Generic.List%601>に実装されて、<xref:System.Collections.Generic.IList%601>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="3c054-115">For example, <xref:System.Collections.Generic.List%601> is an implementation of the <xref:System.Collections.Generic.IList%601> interface.</span></span>  
  
 <span data-ttu-id="3c054-116">**✓ しないで**を定義する各インターフェイスを使用するには、少なくとも 1 つの API を提供 (パラメーターまたはプロパティとして、インターフェイス メソッドは、インターフェイスとして型指定された)。</span><span class="sxs-lookup"><span data-stu-id="3c054-116">**✓ DO** provide at least one API that consumes each interface you define (a method taking the interface as a parameter or a property typed as the interface).</span></span>  
  
 <span data-ttu-id="3c054-117">インターフェイスの設計を検証するには、これによりを行っています。</span><span class="sxs-lookup"><span data-stu-id="3c054-117">Doing this helps to validate the interface design.</span></span> <span data-ttu-id="3c054-118">たとえば、<xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>消費、<xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="3c054-118">For example, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consumes the <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.</span></span>  
  
 <span data-ttu-id="3c054-119">**X しないで**以前に出荷されたインターフェイスにメンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="3c054-119">**X DO NOT** add members to an interface that has previously shipped.</span></span>  
  
 <span data-ttu-id="3c054-120">これにより、インターフェイスの実装の使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="3c054-120">Doing so would break implementations of the interface.</span></span> <span data-ttu-id="3c054-121">バージョン管理の問題を回避するために、新しいインターフェイスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c054-121">You should create a new interface in order to avoid versioning problems.</span></span>  
  
 <span data-ttu-id="3c054-122">を除き、これらのガイドライン」に説明されている場合、マネージ コードの再利用可能なライブラリをデザイン インターフェイスではなく、クラスを選択してください、一般に。</span><span class="sxs-lookup"><span data-stu-id="3c054-122">Except for the situations described in these guidelines, you should, in general, choose classes rather than interfaces in designing managed code reusable libraries.</span></span>  
  
 <span data-ttu-id="3c054-123">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="3c054-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="3c054-124">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="3c054-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c054-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c054-125">See Also</span></span>  
 [<span data-ttu-id="3c054-126">型デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="3c054-126">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="3c054-127">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="3c054-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

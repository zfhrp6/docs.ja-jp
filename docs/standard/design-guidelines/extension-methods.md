---
title: 拡張メソッド
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6247b6d1718f43d4b05d585cc12a05c5e0cc2035
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="extension-methods"></a><span data-ttu-id="605b9-102">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="605b9-102">Extension Methods</span></span>
<span data-ttu-id="605b9-103">拡張メソッドは、言語の機能により、インスタンス メソッドの呼び出し構文を使用して呼び出されるメソッドは静的です。</span><span class="sxs-lookup"><span data-stu-id="605b9-103">Extension methods are a language feature that allows static methods to be called using instance method call syntax.</span></span> <span data-ttu-id="605b9-104">これらのメソッドは、操作するためには、メソッドのインスタンスを表すには、少なくとも 1 つのパラメーターを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="605b9-104">These methods must take at least one parameter, which represents the instance the method is to operate on.</span></span>  
  
 <span data-ttu-id="605b9-105">このような拡張メソッドを定義するクラスが「スポンサー」クラスと呼ばれ、静的な宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="605b9-105">The class that defines such extension methods is referred to as the "sponsor" class, and it must be declared as static.</span></span> <span data-ttu-id="605b9-106">拡張メソッドを使用するには、スポンサー クラスを定義する名前空間をインポートいずれかの必要があります。</span><span class="sxs-lookup"><span data-stu-id="605b9-106">To use extension methods, one must import the namespace defining the sponsor class.</span></span>  
  
 <span data-ttu-id="605b9-107">**避け x**いないこと、お持ちでない型に特に拡張メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="605b9-107">**X AVOID** frivolously defining extension methods, especially on types you don’t own.</span></span>  
  
 <span data-ttu-id="605b9-108">型のソース コードを所有する場合は、通常のインスタンス メソッドを代わりに使用することを検討します。</span><span class="sxs-lookup"><span data-stu-id="605b9-108">If you do own source code of a type, consider using regular instance methods instead.</span></span> <span data-ttu-id="605b9-109">所有していない場合に、メソッドを追加するには、十分に注意します。</span><span class="sxs-lookup"><span data-stu-id="605b9-109">If you don’t own, and you want to add a method, be very careful.</span></span> <span data-ttu-id="605b9-110">拡張メソッドを多めに使用では、これらのメソッドがあるように設計されていない種類の Api に混乱が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="605b9-110">Liberal use of extension methods has the potential of cluttering APIs of types that were not designed to have these methods.</span></span>  
  
 <span data-ttu-id="605b9-111">**✓ を検討してください**拡張メソッドを使用して、次のシナリオのいずれかで。</span><span class="sxs-lookup"><span data-stu-id="605b9-111">**✓ CONSIDER** using extension methods in any of the following scenarios:</span></span>  
  
-   <span data-ttu-id="605b9-112">ヘルパーを提供するには、コア インターフェイスの観点から機能と言われます場合、インターフェイスのすべての実装に関連する機能を記述できます。</span><span class="sxs-lookup"><span data-stu-id="605b9-112">To provide helper functionality relevant to every implementation of an interface, if said functionality can be written in terms of the core interface.</span></span> <span data-ttu-id="605b9-113">具体的な実装は、インターフェイスそれ以外の場合に割り当てることができないためにです。</span><span class="sxs-lookup"><span data-stu-id="605b9-113">This is because concrete implementations cannot otherwise be assigned to interfaces.</span></span> <span data-ttu-id="605b9-114">たとえば、`LINQ to Objects`演算子がすべての拡張メソッドとして実装されて<xref:System.Collections.Generic.IEnumerable%601>型です。</span><span class="sxs-lookup"><span data-stu-id="605b9-114">For example, the `LINQ to Objects` operators are implemented as extension methods for all <xref:System.Collections.Generic.IEnumerable%601> types.</span></span> <span data-ttu-id="605b9-115">したがって、いずれか`IEnumerable<>`実装が自動的に LINQ 有効にします。</span><span class="sxs-lookup"><span data-stu-id="605b9-115">Thus, any `IEnumerable<>` implementation is automatically LINQ-enabled.</span></span>  
  
-   <span data-ttu-id="605b9-116">インスタンス メソッドがいくつかの型への依存関係が、このような依存関係をどのように発生する場合、依存関係の管理規則ができなくなります。</span><span class="sxs-lookup"><span data-stu-id="605b9-116">When an instance method would introduce a dependency on some type, but such a dependency would break dependency management rules.</span></span> <span data-ttu-id="605b9-117">依存関係など、<xref:System.String>に<xref:System.Uri?displayProperty=nameWithType>が許容されない可能性がありますので`String.ToUri()`を返すインスタンス メソッド`System.Uri`依存関係の管理の観点から正しくないデザインになります。</span><span class="sxs-lookup"><span data-stu-id="605b9-117">For example, a dependency from <xref:System.String> to <xref:System.Uri?displayProperty=nameWithType> is probably not desirable, and so `String.ToUri()` instance method returning `System.Uri` would be the wrong design from a dependency management perspective.</span></span> <span data-ttu-id="605b9-118">拡張機能の静的メソッド`Uri.ToUri(this string str)`返す`System.Uri`量より優れた設計になります。</span><span class="sxs-lookup"><span data-stu-id="605b9-118">A static extension method `Uri.ToUri(this string str)` returning `System.Uri` would be a much better design.</span></span>  
  
 <span data-ttu-id="605b9-119">**避け x**で拡張メソッドを定義する<xref:System.Object?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="605b9-119">**X AVOID** defining extension methods on <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="605b9-120">VB のユーザーは拡張メソッド構文を使用してオブジェクト参照でこのようなメソッドを呼び出すことができません。</span><span class="sxs-lookup"><span data-stu-id="605b9-120">VB users will not be able to call such methods on object references using the extension method syntax.</span></span> <span data-ttu-id="605b9-121">VB は vb の場合は参照を宣言するオブジェクトが遅延するすべてのメソッド呼び出しを強制的にバインドされているため、このようなメソッドの呼び出しをサポートしていません (と呼ばれる実際のメンバーは実行時に決定されます) 中、拡張メソッドへのバインドはコンパイル時 (早期に決定されますバインドされている)。</span><span class="sxs-lookup"><span data-stu-id="605b9-121">VB does not support calling such methods because, in VB, declaring a reference as Object forces all method invocations on it to be late bound (actual member called is determined at runtime), while bindings to extension methods are determined at compile-time (early bound).</span></span>  
  
 <span data-ttu-id="605b9-122">ガイドラインは、同じバインド動作が存在するその他の言語に適用されることに注意してください。 または、拡張メソッドはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="605b9-122">Note that the guideline applies to other languages where the same binding behavior is present, or where extension methods are not supported.</span></span>  
  
 <span data-ttu-id="605b9-123">**X しないで**インターフェイスにメソッドを追加または依存関係の管理用である場合を除き、拡張の型と同じ名前空間の拡張メソッドを格納します。</span><span class="sxs-lookup"><span data-stu-id="605b9-123">**X DO NOT** put extension methods in the same namespace as the extended type unless it is for adding methods to interfaces or for dependency management.</span></span>  
  
 <span data-ttu-id="605b9-124">**避け x**異なる名前空間にある場合でも、同じシグネチャを持つ 2 つ以上の拡張メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="605b9-124">**X AVOID** defining two or more extension methods with the same signature, even if they reside in different namespaces.</span></span>  
  
 <span data-ttu-id="605b9-125">**✓ を検討してください**型がインターフェイスで、ほとんどまたはすべてのケースで使用する拡張メソッドは、拡張された型と同じ名前空間に拡張メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="605b9-125">**✓ CONSIDER** defining extension methods in the same namespace as the extended type if the type is an interface and if the extension methods are meant to be used in most or all cases.</span></span>  
  
 <span data-ttu-id="605b9-126">**X しないで**通常その他の機能に関連付けられている名前空間の機能を実装する拡張メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="605b9-126">**X DO NOT** define extension methods implementing a feature in namespaces normally associated with other features.</span></span> <span data-ttu-id="605b9-127">代わりに、所属する機能に関連付けられている名前空間で定義します。</span><span class="sxs-lookup"><span data-stu-id="605b9-127">Instead, define them in the namespace associated with the feature they belong to.</span></span>  
  
 <span data-ttu-id="605b9-128">**避け x**拡張メソッド (たとえば、「拡張」) を専用の名前空間の汎用名前付けします。</span><span class="sxs-lookup"><span data-stu-id="605b9-128">**X AVOID** generic naming of namespaces dedicated to extension methods (e.g., "Extensions").</span></span> <span data-ttu-id="605b9-129">わかりやすい名前 (たとえば、「ルーティング」) 代わりにします。</span><span class="sxs-lookup"><span data-stu-id="605b9-129">Use a descriptive name (e.g., "Routing") instead.</span></span>  
  
 <span data-ttu-id="605b9-130">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="605b9-130">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="605b9-131">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="605b9-131">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="605b9-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="605b9-132">See Also</span></span>  
 [<span data-ttu-id="605b9-133">メンバーのデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="605b9-133">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="605b9-134">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="605b9-134">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

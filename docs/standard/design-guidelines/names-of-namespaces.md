---
title: "名前空間の名前"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4fc0cb9183fde33887a3e84bb30cc3f79892586e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-namespaces"></a><span data-ttu-id="e15d3-102">名前空間の名前</span><span class="sxs-lookup"><span data-stu-id="e15d3-102">Names of Namespaces</span></span>
<span data-ttu-id="e15d3-103">として他の名前付けのガイドラインに目標の名前空間の名前を付けるときを作成するための十分なわかりやすくするためにどのような名前空間のコンテンツがある可能性がすぐにわかるフレームワークを使用するプログラマにとってです。</span><span class="sxs-lookup"><span data-stu-id="e15d3-103">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="e15d3-104">次のテンプレートは、名前空間の名前付けに関する一般的な規則を指定します。</span><span class="sxs-lookup"><span data-stu-id="e15d3-104">The following template specifies the general rule for naming namespaces:</span></span>  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 <span data-ttu-id="e15d3-105">例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e15d3-105">The following are examples:</span></span>  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 <span data-ttu-id="e15d3-106">**✓ しないで**から同じ名前を持つ異なる会社から名前空間を防ぐために、会社名と名前空間名をプレフィックスします。</span><span class="sxs-lookup"><span data-stu-id="e15d3-106">**✓ DO** prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>  
  
 <span data-ttu-id="e15d3-107">**✓ しないで**名前空間の名前の 2 番目のレベルで、安定したバージョンに依存しない製品名を使用します。</span><span class="sxs-lookup"><span data-stu-id="e15d3-107">**✓ DO** use a stable, version-independent product name at the second level of a namespace name.</span></span>  
  
 <span data-ttu-id="e15d3-108">**X しないで**企業内のグループ名は、短時間である傾向があるため、名前空間の階層内の名前の基準として組織階層を使用します。</span><span class="sxs-lookup"><span data-stu-id="e15d3-108">**X DO NOT** use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="e15d3-109">関連するテクノロジのグループの周囲の名前空間の階層を整理します。</span><span class="sxs-lookup"><span data-stu-id="e15d3-109">Organize the hierarchy of namespaces around groups of related technologies.</span></span>  
  
 <span data-ttu-id="e15d3-110">**✓ 操作を行います**をピリオド pascal 表記を使用、および別の名前空間のコンポーネントを使用して (例: `Microsoft.Office.PowerPoint`)。</span><span class="sxs-lookup"><span data-stu-id="e15d3-110">**✓ DO** use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="e15d3-111">会社をブランド化は、従来とは異なる大文字と小文字を使用している場合は、標準の名前空間の大文字と小文字から以上逸脱している場合でも、ブランド名で定義されている大文字小文字の区別に従ってください。</span><span class="sxs-lookup"><span data-stu-id="e15d3-111">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>  
  
 <span data-ttu-id="e15d3-112">**✓ を検討してください**適切な場所に複数形の名前空間の名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="e15d3-112">**✓ CONSIDER** using plural namespace names where appropriate.</span></span>  
  
 <span data-ttu-id="e15d3-113">たとえば、使用して`System.Collections`の代わりに`System.Collection`です。</span><span class="sxs-lookup"><span data-stu-id="e15d3-113">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="e15d3-114">ブランド名や頭字語は、この規則の例外をただしです。</span><span class="sxs-lookup"><span data-stu-id="e15d3-114">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="e15d3-115">たとえば、使用して`System.IO`の代わりに`System.IOs`です。</span><span class="sxs-lookup"><span data-stu-id="e15d3-115">For example, use `System.IO` instead of `System.IOs`.</span></span>  
  
 <span data-ttu-id="e15d3-116">**X しないで**その名前空間、名前空間と型に同じ名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="e15d3-116">**X DO NOT** use the same name for a namespace and a type in that namespace.</span></span>  
  
 <span data-ttu-id="e15d3-117">たとえば、使用しないでください`Debug`、名前空間と名前を指定し、という名前のクラスも提供`Debug`同じ名前空間。</span><span class="sxs-lookup"><span data-stu-id="e15d3-117">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="e15d3-118">いくつかのコンパイラでは、完全に修飾するには、このような型が必要です。</span><span class="sxs-lookup"><span data-stu-id="e15d3-118">Several compilers require such types to be fully qualified.</span></span>  
  
### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="e15d3-119">名前空間と型名の競合</span><span class="sxs-lookup"><span data-stu-id="e15d3-119">Namespaces and Type Name Conflicts</span></span>  
 <span data-ttu-id="e15d3-120">**X しないで**など、ジェネリック型の名前を導入`Element`、 `Node`、 `Log`、および`Message`です。</span><span class="sxs-lookup"><span data-stu-id="e15d3-120">**X DO NOT** introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>  
  
 <span data-ttu-id="e15d3-121">名前を入力する可能性は競合シナリオで共通の非常に高い確率があります。</span><span class="sxs-lookup"><span data-stu-id="e15d3-121">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="e15d3-122">ジェネリック型の名前を修飾する必要があります (`FormElement`、 `XmlNode`、 `EventLog`、 `SoapMessage`)。</span><span class="sxs-lookup"><span data-stu-id="e15d3-122">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>  
  
 <span data-ttu-id="e15d3-123">別のカテゴリの名前空間の型名の競合を回避するための特定のガイドラインがあります。</span><span class="sxs-lookup"><span data-stu-id="e15d3-123">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>  
  
-   <span data-ttu-id="e15d3-124">**アプリケーション モデルの名前空間**</span><span class="sxs-lookup"><span data-stu-id="e15d3-124">**Application model namespaces**</span></span>  
  
     <span data-ttu-id="e15d3-125">1 つのアプリケーション モデルに属している名前空間は、一緒に使用ほとんどの場合が、他のアプリケーション モデルの名前空間を使用することはほぼありません。</span><span class="sxs-lookup"><span data-stu-id="e15d3-125">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="e15d3-126">たとえば、<xref:System.Windows.Forms?displayProperty=nameWithType>と共に名前空間が使用する非常にまれ、<xref:System.Web.UI?displayProperty=nameWithType>名前空間。</span><span class="sxs-lookup"><span data-stu-id="e15d3-126">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="e15d3-127">モデルの名前空間のよく知られているアプリケーション グループの一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e15d3-127">The following is a list of well-known application model namespace groups:</span></span>  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     <span data-ttu-id="e15d3-128">**X しないで**1 つのアプリケーション モデル内の名前空間の型に同じ名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="e15d3-128">**X DO NOT** give the same name to types in namespaces within a single application model.</span></span>  
  
     <span data-ttu-id="e15d3-129">たとえば、という名前の型を追加しない`Page`を<xref:System.Web.UI.Adapters?displayProperty=nameWithType>名前空間、ため、<xref:System.Web.UI?displayProperty=nameWithType>名前空間には既にという名前の型が含まれています`Page`です。</span><span class="sxs-lookup"><span data-stu-id="e15d3-129">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>  
  
-   <span data-ttu-id="e15d3-130">**インフラストラクチャの名前空間**</span><span class="sxs-lookup"><span data-stu-id="e15d3-130">**Infrastructure namespaces**</span></span>  
  
     <span data-ttu-id="e15d3-131">このグループには、ほとんどの一般的なアプリケーションの開発時にインポートされる名前空間が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e15d3-131">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="e15d3-132">たとえば、`.Design`ツール プログラミングを開発する場合は名前空間が主に使用します。</span><span class="sxs-lookup"><span data-stu-id="e15d3-132">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="e15d3-133">これらの名前空間内の型との競合を回避することは、重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="e15d3-133">Avoiding conflicts with types in these namespaces is not critical.</span></span>  
  
-   <span data-ttu-id="e15d3-134">**コア名前空間**</span><span class="sxs-lookup"><span data-stu-id="e15d3-134">**Core namespaces**</span></span>  
  
     <span data-ttu-id="e15d3-135">コア名前空間には、すべてが含まれて`System`名前空間、アプリケーション モデルの名前空間とインフラストラクチャの名前空間を除外します。</span><span class="sxs-lookup"><span data-stu-id="e15d3-135">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="e15d3-136">その他のコア名前空間が含まれます`System`、 `System.IO`、 `System.Xml`、および`System.Net`です。</span><span class="sxs-lookup"><span data-stu-id="e15d3-136">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>  
  
     <span data-ttu-id="e15d3-137">**X しないで**付与がコア名前空間の型と競合する名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="e15d3-137">**X DO NOT** give types names that would conflict with any type in the Core namespaces.</span></span>  
  
     <span data-ttu-id="e15d3-138">たとえば、使用しないで`Stream`型名として。</span><span class="sxs-lookup"><span data-stu-id="e15d3-138">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="e15d3-139">競合する<xref:System.IO.Stream?displayProperty=nameWithType>、非常によく型を使用します。</span><span class="sxs-lookup"><span data-stu-id="e15d3-139">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>  
  
-   <span data-ttu-id="e15d3-140">**テクノロジ名前空間のグループ**</span><span class="sxs-lookup"><span data-stu-id="e15d3-140">**Technology namespace groups**</span></span>  
  
     <span data-ttu-id="e15d3-141">このカテゴリには、同じ最初の 2 つの名前空間ノードを持つすべての名前空間が含まれています。 `(<Company>.<Technology>*`)、など`Microsoft.Build.Utilities`と`Microsoft.Build.Tasks`です。</span><span class="sxs-lookup"><span data-stu-id="e15d3-141">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="e15d3-142">1 つのテクノロジに属している型が互いに競合しないことが重要です。</span><span class="sxs-lookup"><span data-stu-id="e15d3-142">It is important that types belonging to a single technology do not conflict with each other.</span></span>  
  
     <span data-ttu-id="e15d3-143">**X しないで**1 つのテクノロジ内の他の種類と競合する型の名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e15d3-143">**X DO NOT** assign type names that would conflict with other types within a single technology.</span></span>  
  
     <span data-ttu-id="e15d3-144">**X しないで**(場合を除く、テクノロジは、アプリケーション モデルで使用するものではありません) テクノロジの名前空間の型と、アプリケーション モデルの名前空間の型名の競合を紹介します。</span><span class="sxs-lookup"><span data-stu-id="e15d3-144">**X DO NOT** introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>  
  
 <span data-ttu-id="e15d3-145">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="e15d3-145">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e15d3-146">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="e15d3-146">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e15d3-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="e15d3-147">See Also</span></span>  
 [<span data-ttu-id="e15d3-148">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="e15d3-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="e15d3-149">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="e15d3-149">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)

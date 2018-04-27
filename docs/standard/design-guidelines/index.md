---
title: フレームワーク デザインのガイドライン
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
caps.latest.revision: 14
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c54ec4a5cc3c4bef1e6460b2c9971af4e2af983a
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="51be3-102">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="51be3-102">Framework Design Guidelines</span></span>
<span data-ttu-id="51be3-103">このセクションでは、ライブラリを拡張し、.NET Framework との対話をデザインするためのガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="51be3-103">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="51be3-104">目標は、ライブラリのデザイナーが開発に使用するプログラミング言語に関係なく、統一されたプログラミング モデルを提供することで API の一貫性と使いやすさを確認するためです。</span><span class="sxs-lookup"><span data-stu-id="51be3-104">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="51be3-105">クラスと、.NET Framework を拡張するコンポーネントを開発する際に、これらのデザイン ガイドラインに従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="51be3-105">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="51be3-106">一貫性のないライブラリ デザインが悪影響を及ぼす開発者の生産性に影響し、導入を行わないましょう。</span><span class="sxs-lookup"><span data-stu-id="51be3-106">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="51be3-107">ガイドラインは、語句で始まる簡単な推奨事項として編成`Do`、 `Consider`、 `Avoid`、および`Do not`です。</span><span class="sxs-lookup"><span data-stu-id="51be3-107">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="51be3-108">次のガイドラインについては、クラス ライブラリのデザイナーのさまざまなソリューション間のトレードオフを理解するためものです。</span><span class="sxs-lookup"><span data-stu-id="51be3-108">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="51be3-109">適切なライブラリ デザインではこれらのデザイン ガイドラインに違反することが必要な状況である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="51be3-109">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="51be3-110">このような場合はまれで、意思決定の理由を明確かつ説得力のあることが重要です。</span><span class="sxs-lookup"><span data-stu-id="51be3-110">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="51be3-111">次のガイドラインは、ブックからの抜粋です*Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン*は Cwalina Brad Abrams では、します。</span><span class="sxs-lookup"><span data-stu-id="51be3-111">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="51be3-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="51be3-112">In This Section</span></span>  
 [<span data-ttu-id="51be3-113">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="51be3-113">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 <span data-ttu-id="51be3-114">アセンブリ、名前空間、型、およびクラス ライブラリ内のメンバーの名前付けのガイドラインを提供します。</span><span class="sxs-lookup"><span data-stu-id="51be3-114">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="51be3-115">型デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="51be3-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 <span data-ttu-id="51be3-116">静的な抽象クラス、インターフェイス、列挙型、構造体、およびその他の種類を使用するためのガイドラインを提供します。</span><span class="sxs-lookup"><span data-stu-id="51be3-116">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="51be3-117">メンバーのデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="51be3-117">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 <span data-ttu-id="51be3-118">デザインおよびプロパティ、メソッド、コンス トラクター、フィールド、イベント、演算子、およびパラメーターを使用するためのガイドラインを提供します。</span><span class="sxs-lookup"><span data-stu-id="51be3-118">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="51be3-119">機能拡張のデザイン</span><span class="sxs-lookup"><span data-stu-id="51be3-119">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 <span data-ttu-id="51be3-120">イベント、仮想メンバー、およびコールバック関数を使用して、サブクラスなどの機能拡張機構について説明し、フレームワークの要件に最適なメカニズムを選択する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="51be3-120">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="51be3-121">例外のデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="51be3-121">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)  
 <span data-ttu-id="51be3-122">デザイン、スロー、および例外のキャッチのデザイン ガイドラインをについて説明します。</span><span class="sxs-lookup"><span data-stu-id="51be3-122">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="51be3-123">使用方法のガイドライン</span><span class="sxs-lookup"><span data-stu-id="51be3-123">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 <span data-ttu-id="51be3-124">配列、属性、およびコレクションなどの一般的な型を使用して、シリアル化のサポート、等値演算子のオーバー ロードに関するガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="51be3-124">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="51be3-125">共通デザイン パターン</span><span class="sxs-lookup"><span data-stu-id="51be3-125">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 <span data-ttu-id="51be3-126">選択して、依存関係プロパティと、dispose パターンの実装のガイドラインを提供します。</span><span class="sxs-lookup"><span data-stu-id="51be3-126">Provides guidelines for choosing and implementing dependency properties and the dispose pattern.</span></span>  
  
 <span data-ttu-id="51be3-127">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="51be3-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="51be3-128">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="51be3-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51be3-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="51be3-129">See Also</span></span>  
 [<span data-ttu-id="51be3-130">概要</span><span class="sxs-lookup"><span data-stu-id="51be3-130">Overview</span></span>](../../../docs/framework/get-started/overview.md)  
 [<span data-ttu-id="51be3-131">.NET Framework のロードマップ</span><span class="sxs-lookup"><span data-stu-id="51be3-131">Roadmap for the .NET Framework</span></span>](https://msdn.microsoft.com/library/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)  
 [<span data-ttu-id="51be3-132">開発ガイド</span><span class="sxs-lookup"><span data-stu-id="51be3-132">Development Guide</span></span>](../../../docs/framework/development-guide.md)

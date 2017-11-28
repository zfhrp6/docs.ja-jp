---
title: ".NET Framework アプリケーションのグローバライズとローカライズ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- international applications [.NET Framework]
- globalization [.NET Framework], encoding
- global applications
- internationalization
- world-ready applications
- application development [.NET Framework], globalization
- multilingual application development
ms.assetid: 9a59696b-d89b-45bd-946d-c75da4732d02
caps.latest.revision: "42"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f6beb720819a1be4e45bf4cefac3d805d7ee5e7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="globalizing-and-localizing-net-framework-applications"></a><span data-ttu-id="26e27-102">.NET Framework アプリケーションのグローバライズとローカライズ</span><span class="sxs-lookup"><span data-stu-id="26e27-102">Globalizing and Localizing .NET Framework Applications</span></span>
<span data-ttu-id="26e27-103">1 つ以上の言語にローカライズされるアプリケーションなど、[国際対応アプリケーション](http://msdn.microsoft.com/goglobal/bb978433.aspx)を開発するには、グローバリゼーション、ローカライズ対象の確認、およびローカリゼーションの 3 つの手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="26e27-103">Developing a [world-ready application](http://msdn.microsoft.com/goglobal/bb978433.aspx), including an application that can be localized into one or more languages, involves three steps: globalization, localizability review, and localization.</span></span>  
  
 [<span data-ttu-id="26e27-104">グローバリゼーション</span><span class="sxs-lookup"><span data-stu-id="26e27-104">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)  
 <span data-ttu-id="26e27-105">これは、特定のカルチャや言語に依存せず、すべてのユーザーに対して、ローカライズされたユーザー インターフェイスと、その地域に合ったデータをサポートするような、アプリケーションの設計と開発を行う手順です。</span><span class="sxs-lookup"><span data-stu-id="26e27-105">This step involves designing and coding an application that is culture-neutral and language-neutral, and that supports localized user interfaces and regional data for all users.</span></span> <span data-ttu-id="26e27-106">これはカルチャ固有の前提に基づかない決定によって設計とプログラミングを行うことです。</span><span class="sxs-lookup"><span data-stu-id="26e27-106">It involves making design and programming decisions that are not based on culture-specific assumptions.</span></span> <span data-ttu-id="26e27-107">グローバライズされたアプリケーションは、ローカライズされていなくても、後から比較的容易に 1 つ以上の言語にローカライズできるように設計開発されています。</span><span class="sxs-lookup"><span data-stu-id="26e27-107">While a globalized application is not localized, it nevertheless is designed and written so that it can be subsequently localized into one or more languages with relative ease.</span></span>  
  
 [<span data-ttu-id="26e27-108">ローカライズ化の確認</span><span class="sxs-lookup"><span data-stu-id="26e27-108">Localizability Review</span></span>](../../../docs/standard/globalization-localization/localizability-review.md)  
 <span data-ttu-id="26e27-109">この手順により、アプリケーションのコードと設計をレビューして、ローカライズが容易になるようにし、ローカライズのための潜在的な問題点を識別し、アプリケーションの実行可能コードがリソースから分離されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="26e27-109">This step involves reviewing an application's code and design to ensure that it can be localized easily and to identify potential roadblocks for localization, and verifying that the application's executable code is separated from its resources.</span></span> <span data-ttu-id="26e27-110">グローバリゼーションの段階が効果的なものであれば、ローカリゼーション レビューはグローバリゼーションの過程で行われた設計とコーディングの決定を確認するものになります。</span><span class="sxs-lookup"><span data-stu-id="26e27-110">If the globalization stage was effective, the localizability review will confirm the design and coding choices made during globalization.</span></span> <span data-ttu-id="26e27-111">ローカライズ対象の確認の段階では、ローカライズの段階でアプリケーションのソース コードを変更する必要がないように、残っている問題を特定します。</span><span class="sxs-lookup"><span data-stu-id="26e27-111">The localizability stage may also identify any remaining issues so that an application's source code doesn't have to be modified during the localization stage.</span></span>  
  
 [<span data-ttu-id="26e27-112">ローカリゼーション</span><span class="sxs-lookup"><span data-stu-id="26e27-112">Localization</span></span>](../../../docs/standard/globalization-localization/localization.md)  
 <span data-ttu-id="26e27-113">この手順では、特定のカルチャまたは地域に合わせてアプリケーションをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="26e27-113">This step involves customizing an application for specific cultures or regions.</span></span> <span data-ttu-id="26e27-114">グローバリゼーションとローカライズ対象の確認を適切に行うと、ローカリゼーションでは主にユーザー インターフェイスの翻訳作業が行われます。</span><span class="sxs-lookup"><span data-stu-id="26e27-114">If the globalization and localizability steps have been performed correctly, localization consists primarily of translating the user interface.</span></span>  
  
 <span data-ttu-id="26e27-115">この 3 つの手順に従うことにより、次の 2 つの利点があります。</span><span class="sxs-lookup"><span data-stu-id="26e27-115">Following these three steps provides two advantages:</span></span>  
  
-   <span data-ttu-id="26e27-116">米国英語などのような 1 つのカルチャだけをサポートするアプリケーションを、他のカルチャもサポートするように変更する作業を行う必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="26e27-116">It frees you from having to retrofit an application that is designed to support a single culture, such as U.S. English, to support additional cultures.</span></span>  
  
-   <span data-ttu-id="26e27-117">ローカライズされたアプリケーションが、より安定してバグがより少ないものになります。</span><span class="sxs-lookup"><span data-stu-id="26e27-117">It results in localized applications that are more stable and have fewer bugs.</span></span>  
  
 <span data-ttu-id="26e27-118">.NET Framework には、国際対応アプリケーションやローカライズされたアプリケーションの開発の拡張サポートが備わっています。</span><span class="sxs-lookup"><span data-stu-id="26e27-118">The .NET Framework provides extensive support for the development of world-ready and localized applications.</span></span> <span data-ttu-id="26e27-119">特に、.NET Framework クラス ライブラリの多くの型メンバーは、現在のユーザーのカルチャまたは特定のカルチャの規則を表す値を返すことができ、グローバリゼーションに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="26e27-119">In particular, many type members in the .NET Framework class library aid globalization by returning values that reflect the conventions of either the current user's culture or a specified culture.</span></span> <span data-ttu-id="26e27-120">また、.NET Framework はサテライト アセンブリをサポートし、アプリケーションのローカライズ プロセスを容易にします。</span><span class="sxs-lookup"><span data-stu-id="26e27-120">Also, the .NET Framework supports satellite assemblies, which facilitate the process of localizing an application.</span></span>  
  
 <span data-ttu-id="26e27-121">詳細については、「[Go Global Developer Center](http://go.microsoft.com/fwlink/?LinkId=235015)」(グローバル デベロッパー センター) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="26e27-121">For additional information, see the [Go Global Developer Center](http://go.microsoft.com/fwlink/?LinkId=235015).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="26e27-122">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="26e27-122">In This Section</span></span>  
 [<span data-ttu-id="26e27-123">グローバリゼーション</span><span class="sxs-lookup"><span data-stu-id="26e27-123">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)  
 <span data-ttu-id="26e27-124">国際対応アプリケーションを作成するための最初の手順を説明します。カルチャや言語に依存しないアプリケーションの設計とコーディングを行います。</span><span class="sxs-lookup"><span data-stu-id="26e27-124">Discusses the first stage of creating a world-ready application, which involves designing and coding an application that is culture-neutral and language-neutral.</span></span>  
  
 [<span data-ttu-id="26e27-125">ローカライズ化の確認</span><span class="sxs-lookup"><span data-stu-id="26e27-125">Localizability Review</span></span>](../../../docs/standard/globalization-localization/localizability-review.md)  
 <span data-ttu-id="26e27-126">ローカライズされたアプリケーションを作成するための 2 つ目の手順を説明します。ローカライズのための潜在的な問題点を識別します。</span><span class="sxs-lookup"><span data-stu-id="26e27-126">Discusses the second stage of creating a localized application, which involves identifying potential roadblocks to localization.</span></span>  
  
 [<span data-ttu-id="26e27-127">ローカリゼーション</span><span class="sxs-lookup"><span data-stu-id="26e27-127">Localization</span></span>](../../../docs/standard/globalization-localization/localization.md)  
 <span data-ttu-id="26e27-128">ローカライズされたアプリケーションを作成するための最後の手順を説明します。特定の地域またはカルチャのために、アプリケーションのユーザー インターフェイスをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="26e27-128">Discusses the final stage of creating a localized application, which involves customizing an application's user interface for specific regions or cultures.</span></span>  
  
 [<span data-ttu-id="26e27-129">カルチャを認識しない文字列操作</span><span class="sxs-lookup"><span data-stu-id="26e27-129">Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 <span data-ttu-id="26e27-130">既定ではカルチャが識別される .NET Framework のメソッドやクラスを使用して、カルチャが識別されない結果を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="26e27-130">Describes how to use .NET Framework methods and classes that are culture-sensitive by default to obtain culture-insensitive results.</span></span>  
  
 [<span data-ttu-id="26e27-131">推奨される国際対応アプリケーション開発手順</span><span class="sxs-lookup"><span data-stu-id="26e27-131">Best Practices for Developing World-Ready Applications</span></span>](../../../docs/standard/globalization-localization/best-practices-for-developing-world-ready-apps.md)  
 <span data-ttu-id="26e27-132">国際対応 ASP.NET アプリケーションのグローバリゼーション、ローカリゼーション、および開発の推奨手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="26e27-132">Describes the best practices to follow for globalization, localization, and developing world-ready ASP.NET applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="26e27-133">参照</span><span class="sxs-lookup"><span data-stu-id="26e27-133">Reference</span></span>  
 <span data-ttu-id="26e27-134"><xref:System.Globalization?displayProperty=nameWithType> 名前空間</span><span class="sxs-lookup"><span data-stu-id="26e27-134"><xref:System.Globalization?displayProperty=nameWithType> namespace</span></span>  
 <span data-ttu-id="26e27-135">言語、国/地域、使用する暦、日付、通貨、通知の書式パターン、文字列の並べ替え順序など、カルチャ関連の情報を定義するクラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="26e27-135">Contains classes that define culture-related information, including the language, the country/region, the calendars in use, the format patterns for dates, currency, and numbers, and the sort order for strings.</span></span>  
  
 <span data-ttu-id="26e27-136"><xref:System.Resources> 名前空間</span><span class="sxs-lookup"><span data-stu-id="26e27-136"><xref:System.Resources> namespace</span></span>  
 <span data-ttu-id="26e27-137">リソースを作成、操作、および使用するためのクラスが格納されている名前空間です。</span><span class="sxs-lookup"><span data-stu-id="26e27-137">Provides classes for creating, manipulating, and using resources.</span></span>  
  
 <span data-ttu-id="26e27-138"><xref:System.Text> 名前空間</span><span class="sxs-lookup"><span data-stu-id="26e27-138"><xref:System.Text> namespace</span></span>  
 <span data-ttu-id="26e27-139">ASCII、ANSI、Unicode、およびその他の文字エンコーディングを表すクラスが格納されている名前空間です。</span><span class="sxs-lookup"><span data-stu-id="26e27-139">Contains classes representing ASCII, ANSI, Unicode, and other character encodings.</span></span>  
  
 [<span data-ttu-id="26e27-140">Resgen.exe (リソース ファイル ジェネレーター)</span><span class="sxs-lookup"><span data-stu-id="26e27-140">Resgen.exe (Resource File Generator)</span></span>](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)  
 <span data-ttu-id="26e27-141">Resgen.exe を使用して .txt ファイルと XML ベース リソース フォーマット (.resx) ファイルを共通言語ランタイムのバイナリ .resources ファイルに変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="26e27-141">Describes how to use Resgen.exe to convert .txt files and XML-based resource format (.resx) files to common language runtime binary .resources files.</span></span>  
  
 [<span data-ttu-id="26e27-142">Winres.exe (Windows フォーム リソース エディター)</span><span class="sxs-lookup"><span data-stu-id="26e27-142">Winres.exe (Windows Forms Resource Editor)</span></span>](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)  
 <span data-ttu-id="26e27-143">Winres.exe を使用して Windows フォームのフォームをローカライズする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="26e27-143">Describes how to use Winres.exe to localize Windows Forms forms.</span></span>

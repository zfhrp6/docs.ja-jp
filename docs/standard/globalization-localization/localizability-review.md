---
title: "ローカライズ化の確認"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- world-ready applications, localizability
- application development [.NET Framework], localization
- localizability [.NET Framework]
- international applications [.NET Framework], localizability
- globalization [.NET Framework], localizability
- culture, localizability
- localization [.NET Framework], localizability
- global applications, localizability
- localizing resources
ms.assetid: 3aee2fbb-de47-4e37-8fe4-ddebb9719247
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7633c7fe9e99bde96ee108460e983eff48f1c7f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="localizability-review"></a><span data-ttu-id="458f2-102">ローカライズ化の確認</span><span class="sxs-lookup"><span data-stu-id="458f2-102">Localizability Review</span></span>
<span data-ttu-id="458f2-103">ローカライズ化の確認は、国際対応アプリケーションの開発での中間のステップです。</span><span class="sxs-lookup"><span data-stu-id="458f2-103">The localizability review is an intermediate step in the development of a world-ready application.</span></span> <span data-ttu-id="458f2-104">グローバライズされたアプリケーションがローカライズ可能なコードや特別な処理を必要とするようなユーザー インターフェイスの要素を識別することを確認します。</span><span class="sxs-lookup"><span data-stu-id="458f2-104">It verifies that a globalized application is ready for localization and identifies any code or any aspects of the user interface that require special handling.</span></span> <span data-ttu-id="458f2-105">この手順では、こと、ローカリゼーション処理はされていない、機能上の欠陥をアプリケーションにすることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="458f2-105">This step also helps ensure that the localization process will not introduce any functional defects into your application.</span></span> <span data-ttu-id="458f2-106">ローカライズ化の確認で発生したすべての問題が処理された、ときに、アプリケーションはローカライズ可能です。</span><span class="sxs-lookup"><span data-stu-id="458f2-106">When all the issues raised by the localizability review have been addressed, your application is ready for localization.</span></span> <span data-ttu-id="458f2-107">ローカライズ化の確認が完全な場合は、ローカリゼーション処理中にすべてのソース コードを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="458f2-107">If the localizability review is thorough, you should not have to modify any source code during the localization process.</span></span>  
  
 <span data-ttu-id="458f2-108">ローカライズ化の確認は、次の 3 つのチェックで構成されます。</span><span class="sxs-lookup"><span data-stu-id="458f2-108">The localizability review consists of the following three checks:</span></span>  
  
-   [<span data-ttu-id="458f2-109">グローバリゼーションの推奨事項が実装されているか。</span><span class="sxs-lookup"><span data-stu-id="458f2-109">Are the globalization recommendations implemented?</span></span>](#global)  
  
-   [<span data-ttu-id="458f2-110">カルチャに依存した機能が正しく処理されますか。</span><span class="sxs-lookup"><span data-stu-id="458f2-110">Are culture-sensitive features handled correctly?</span></span>](#culture)  
  
-   [<span data-ttu-id="458f2-111">各種言語データを使用してアプリケーションをテストするか。</span><span class="sxs-lookup"><span data-stu-id="458f2-111">Have you tested your application with international data?</span></span>](#test)  
  
<a name="global"></a>   
## <a name="implementing-globalization-recommendations"></a><span data-ttu-id="458f2-112">グローバリゼーションの推奨事項を実装する</span><span class="sxs-lookup"><span data-stu-id="458f2-112">Implementing globalization recommendations</span></span>  
 <span data-ttu-id="458f2-113">推奨事項が説明に従っている場合とデザインおよび注意でのローカライズを使用してアプリケーションを開発するが、[グローバリゼーション](../../../docs/standard/globalization-localization/globalization.md)資料、ローカリゼーション レビューは、品質保証パスに大きく左右されます.</span><span class="sxs-lookup"><span data-stu-id="458f2-113">If you have designed and developed your application with localization in mind, and if you have followed the recommendations discussed in the [Globalization](../../../docs/standard/globalization-localization/globalization.md) article, the localizability review will largely be a quality assurance pass.</span></span> <span data-ttu-id="458f2-114">それ以外の場合、この段階を確認し、に関する推奨事項を実装する[グローバリゼーション](../../../docs/standard/globalization-localization/globalization.md)、およびソース コードのローカライズを妨げるエラーを修正します。</span><span class="sxs-lookup"><span data-stu-id="458f2-114">Otherwise, during this stage you should review and implement the recommendations for [globalization](../../../docs/standard/globalization-localization/globalization.md), and fix the errors in source code that prevent localization.</span></span>  
  
<a name="culture"></a>   
## <a name="handling-culture-sensitive-features"></a><span data-ttu-id="458f2-115">カルチャに依存した機能を処理する</span><span class="sxs-lookup"><span data-stu-id="458f2-115">Handling culture-sensitive features</span></span>  
 <span data-ttu-id="458f2-116">.NET Framework では、多くのカルチャによって大きく異なる点でプログラムによるサポートは提供されません。</span><span class="sxs-lookup"><span data-stu-id="458f2-116">The .NET Framework does not provide programmatic support in a number of areas that vary widely by culture.</span></span> <span data-ttu-id="458f2-117">ほとんどの場合は、次のような機能領域を処理するカスタム コードを記述する必要。</span><span class="sxs-lookup"><span data-stu-id="458f2-117">In most cases, you have to write custom code to handle feature areas like the following:</span></span>  
  
-   <span data-ttu-id="458f2-118">対応します。</span><span class="sxs-lookup"><span data-stu-id="458f2-118">Addresses.</span></span>  
  
-   <span data-ttu-id="458f2-119">電話番号。</span><span class="sxs-lookup"><span data-stu-id="458f2-119">Telephone numbers.</span></span>  
  
-   <span data-ttu-id="458f2-120">用紙のサイズ。</span><span class="sxs-lookup"><span data-stu-id="458f2-120">Paper sizes.</span></span>  
  
-   <span data-ttu-id="458f2-121">長さ、重量、領域、ボリューム、および温度を使用する測定単位です。</span><span class="sxs-lookup"><span data-stu-id="458f2-121">Units of measure used for lengths, weights, area, volume, and temperatures.</span></span> <span data-ttu-id="458f2-122">.NET Framework では、測定単位の間の変換用の組み込みのサポートは提供しません、使用すると、<xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType>プロパティを次の例に示すように、特定の国または地域がメートル法を使用するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="458f2-122">Although the .NET Framework does not offer built-in support for converting between units of measure, you can use the <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> property to determine whether a particular country or region uses the metric system, as the following example illustrates.</span></span>  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## <a name="testing-your-application"></a><span data-ttu-id="458f2-123">アプリケーションをテストする</span><span class="sxs-lookup"><span data-stu-id="458f2-123">Testing your application</span></span>  
 <span data-ttu-id="458f2-124">アプリケーションをローカライズする前に、オペレーティング システムの各国語バージョンの国際対応データを使用してテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="458f2-124">Before you localize your application, you should test it by using international data on international versions of the operating system.</span></span> <span data-ttu-id="458f2-125">この時点で、ユーザー インターフェイスの大部分はローカライズされません、ですが、次などの問題を検出することができます。</span><span class="sxs-lookup"><span data-stu-id="458f2-125">Although most of the user interface will not be localized at this point, you will be able to detect problems such as the following:</span></span>  
  
-   <span data-ttu-id="458f2-126">シリアル化解除できません正しくオペレーティング システムのバージョン間でシリアル化されたデータ。</span><span class="sxs-lookup"><span data-stu-id="458f2-126">Serialized data that does not deserialize correctly across operating system versions.</span></span>  
  
-   <span data-ttu-id="458f2-127">現在のカルチャの規則を反映しない数値のデータです。</span><span class="sxs-lookup"><span data-stu-id="458f2-127">Numeric data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="458f2-128">たとえば、数値は、不正確な桁区切り記号、桁区切り記号、または通貨記号と表示があります。</span><span class="sxs-lookup"><span data-stu-id="458f2-128">For example, numbers may be displayed with inaccurate group separators, decimal separators, or currency symbols.</span></span>  
  
-   <span data-ttu-id="458f2-129">現在のカルチャの規則を反映しない日付と時刻のデータ。</span><span class="sxs-lookup"><span data-stu-id="458f2-129">Date and time data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="458f2-130">たとえば、月と日を表す数字ですが間違った順序で表示される可能性があります、日付の区切り記号が正しくない可能性があります。 またはタイム ゾーン情報が正しくない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="458f2-130">For example, numbers that represent the month and day may appear in the wrong order, date separators may be incorrect, or time zone information may be incorrect.</span></span>  
  
-   <span data-ttu-id="458f2-131">アプリケーションの既定のカルチャが識別されていないため、見つからないリソース。</span><span class="sxs-lookup"><span data-stu-id="458f2-131">Resources that cannot be found because you have not identified a default culture for your application.</span></span>  
  
-   <span data-ttu-id="458f2-132">特定のカルチャの異常な順序で表示される文字列。</span><span class="sxs-lookup"><span data-stu-id="458f2-132">Strings that are displayed in an unusual order for the specific culture.</span></span>  
  
-   <span data-ttu-id="458f2-133">文字列の比較または予期しない結果を返すの等価比較。</span><span class="sxs-lookup"><span data-stu-id="458f2-133">String comparisons or comparisons for equality that return unexpected results.</span></span>  
  
 <span data-ttu-id="458f2-134">次の手順に進むことができる場合は、アプリケーションを開発するときに、グローバリゼーションの推奨事項を後に、カルチャに依存した機能が正しく、処理しを識別して発生し、テスト中にあるローカライズに関する問題を解決、 [ローカリゼーション](../../../docs/standard/globalization-localization/localization.md)です。</span><span class="sxs-lookup"><span data-stu-id="458f2-134">If you've followed the globalization recommendations when developing your application, handled culture-sensitive features correctly, and identified and addressed the localization issues that arose during testing, you can proceed to the next step, [Localization](../../../docs/standard/globalization-localization/localization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="458f2-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="458f2-135">See Also</span></span>  
 [<span data-ttu-id="458f2-136">グローバライズとローカライズ</span><span class="sxs-lookup"><span data-stu-id="458f2-136">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)  
 [<span data-ttu-id="458f2-137">ローカリゼーション</span><span class="sxs-lookup"><span data-stu-id="458f2-137">Localization</span></span>](../../../docs/standard/globalization-localization/localization.md)  
 [<span data-ttu-id="458f2-138">グローバリゼーション</span><span class="sxs-lookup"><span data-stu-id="458f2-138">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)  
 [<span data-ttu-id="458f2-139">デスクトップ アプリケーションのリソース</span><span class="sxs-lookup"><span data-stu-id="458f2-139">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)

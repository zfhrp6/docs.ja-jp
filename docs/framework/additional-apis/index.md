---
title: "追加のクラス ライブラリと API"
ms.custom: 
ms.date: 01/29/2018
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d9ceb1ad24d4ba87fab7713ba61fed91eef26c4d
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="cfc60-102">追加のクラス ライブラリと API</span><span class="sxs-lookup"><span data-stu-id="cfc60-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="cfc60-103">.NET Framework は、絶えず進化を続けています。クロスプラットフォーム開発を強化するために、またはお客様にいち早く新しい機能を紹介するために、マイクロソフトは新機能のアウトオブバウンド (OOB) をリリースします。</span><span class="sxs-lookup"><span data-stu-id="cfc60-103">The .NET Framework is constantly evolving and in order to improve cross-platform development or to introduce new functionality early to our customers, we release new features out of band (OOB).</span></span> <span data-ttu-id="cfc60-104">ここでは、ドキュメントが用意されている OOB プロジェクトの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="cfc60-104">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="cfc60-105">さらに、いくつかのライブラリは、特定のプラットフォームまたは .NET Framework の実装を対象にしています。</span><span class="sxs-lookup"><span data-stu-id="cfc60-105">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="cfc60-106">たとえば、<xref:System.Text.CodePagesEncodingProvider>クラスは、コード ページ エンコーディングを .NET Framework を使用して開発された UWP アプリで利用できます。</span><span class="sxs-lookup"><span data-stu-id="cfc60-106">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="cfc60-107">ここでは、これらのライブラリの一覧も示します。</span><span class="sxs-lookup"><span data-stu-id="cfc60-107">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="cfc60-108">OOB プロジェクト</span><span class="sxs-lookup"><span data-stu-id="cfc60-108">OOB projects</span></span>
  
| <span data-ttu-id="cfc60-109">プロジェクト</span><span class="sxs-lookup"><span data-stu-id="cfc60-109">Project</span></span> | <span data-ttu-id="cfc60-110">説明</span><span class="sxs-lookup"><span data-stu-id="cfc60-110">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="cfc60-111">スレッド セーフであり、内容が変更されないことが保証されているコレクションを提供します。</span><span class="sxs-lookup"><span data-stu-id="cfc60-111">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="cfc60-112">Windows の WinHTTP インターフェイスに基づいた <xref:System.Net.Http.HttpClient> のメッセージ ハンドラーを提供します。</span><span class="sxs-lookup"><span data-stu-id="cfc60-112">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| [<span data-ttu-id="cfc60-113">System.Numerics.Vectors</span><span class="sxs-lookup"><span data-stu-id="cfc60-113">System.Numerics.Vectors</span></span>](https://msdn.microsoft.com/library/mt452176.aspx) | <span data-ttu-id="cfc60-114">SIMD ハードウェア ベースのアクセラレータを利用できるベクター型のライブラリを提供します。</span><span class="sxs-lookup"><span data-stu-id="cfc60-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="cfc60-115">TPL データフロー ライブラリはデータ フロー コンポーネントを提供し、同時実行対応アプリケーションの堅牢性を強化します。</span><span class="sxs-lookup"><span data-stu-id="cfc60-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="cfc60-116">プラットフォーム固有のライブラリ</span><span class="sxs-lookup"><span data-stu-id="cfc60-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="cfc60-117">プロジェクト</span><span class="sxs-lookup"><span data-stu-id="cfc60-117">Project</span></span> | <span data-ttu-id="cfc60-118">説明</span><span class="sxs-lookup"><span data-stu-id="cfc60-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="cfc60-119">拡張、<xref:System.Text.EncodingProvider>コード ページ エンコーディングをユニバーサル Windows プラットフォームを対象とするアプリを利用できるようにするクラス。</span><span class="sxs-lookup"><span data-stu-id="cfc60-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="cfc60-120">プライベート API</span><span class="sxs-lookup"><span data-stu-id="cfc60-120">Private APIs</span></span>  

<span data-ttu-id="cfc60-121">この API は製品インフラストラクチャをサポートします。コードから直接使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="cfc60-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
| <span data-ttu-id="cfc60-122">API 名</span><span class="sxs-lookup"><span data-stu-id="cfc60-122">API Name</span></span> |
| -------- |
| [<span data-ttu-id="cfc60-123">System.Net.Connection クラス</span><span class="sxs-lookup"><span data-stu-id="cfc60-123">System.Net.Connection Class</span></span>](../../../docs/framework/additional-apis/connection.md) |
| [<span data-ttu-id="cfc60-124">System.Net.Connection.m\_WriteList フィールド</span><span class="sxs-lookup"><span data-stu-id="cfc60-124">System.Net.Connection.m\_WriteList Field</span></span>](../../../docs/framework/additional-apis/m_writelist.md) |
| [<span data-ttu-id="cfc60-125">System.Net.ConnectionGroup クラス</span><span class="sxs-lookup"><span data-stu-id="cfc60-125">System.Net.ConnectionGroup Class</span></span>](../../../docs/framework/additional-apis/connectiongroup.md) |
| [<span data-ttu-id="cfc60-126">System.Net.ConnectionGroup.m\_ConnectionList Field</span><span class="sxs-lookup"><span data-stu-id="cfc60-126">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](../../../docs/framework/additional-apis/m_connectionlist.md) |
| [<span data-ttu-id="cfc60-127">System.Net.CoreResponseData クラス</span><span class="sxs-lookup"><span data-stu-id="cfc60-127">System.Net.CoreResponseData Class</span></span>](../../../docs/framework/additional-apis/coreresponsedata.md) |
| [<span data-ttu-id="cfc60-128">System.Net.CoreResponseData.m\_ResponseHeaders Field</span><span class="sxs-lookup"><span data-stu-id="cfc60-128">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](../../../docs/framework/additional-apis/coreresponsedata_m_responseheaders.md) |
| [<span data-ttu-id="cfc60-129">System.Net.CoreResponseData.m\_StatusCode フィールド</span><span class="sxs-lookup"><span data-stu-id="cfc60-129">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](../../../docs/framework/additional-apis/coreresponsedata_m_statuscode.md) |
| [<span data-ttu-id="cfc60-130">System.Net.HttpWebRequest です。\_AutoRedirects フィールド</span><span class="sxs-lookup"><span data-stu-id="cfc60-130">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](../../../docs/framework/additional-apis/_autoredirects.md) |
| [<span data-ttu-id="cfc60-131">System.Net.HttpWebRequest です。\_CoreResponse フィールド</span><span class="sxs-lookup"><span data-stu-id="cfc60-131">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](../../../docs/framework/additional-apis/httpwebrequest__coreresponse.md) |
| [<span data-ttu-id="cfc60-132">System.Net.HttpWebRequest です。\_HttpResponse フィールド</span><span class="sxs-lookup"><span data-stu-id="cfc60-132">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](../../../docs/framework/additional-apis/_httpresponse.md) |
| [<span data-ttu-id="cfc60-133">System.Net.ServicePoint.m\_ConnectionGroupList Field</span><span class="sxs-lookup"><span data-stu-id="cfc60-133">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](../../../docs/framework/additional-apis/m_connectiongrouplist.md) |
| [<span data-ttu-id="cfc60-134">System.Net.ServicePointManager.s\_ServicePointTable Field</span><span class="sxs-lookup"><span data-stu-id="cfc60-134">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](../../../docs/framework/additional-apis/s_servicepointtable.md) |
| [<span data-ttu-id="cfc60-135">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span><span class="sxs-lookup"><span data-stu-id="cfc60-135">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [<span data-ttu-id="cfc60-136">System.Windows.Forms.Design.DataMemberFieldEditor Class</span><span class="sxs-lookup"><span data-stu-id="cfc60-136">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |
| [<span data-ttu-id="cfc60-137">System.Windows.Forms.Design.DataMemberListEditor Class</span><span class="sxs-lookup"><span data-stu-id="cfc60-137">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |
  
## <a name="see-also"></a><span data-ttu-id="cfc60-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="cfc60-138">See also</span></span>

[<span data-ttu-id="cfc60-139">NET Framework および特別なリリース</span><span class="sxs-lookup"><span data-stu-id="cfc60-139">The .NET Framework and Out-of-Band Releases</span></span>](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)

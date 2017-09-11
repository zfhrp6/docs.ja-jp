---
title: "追加のクラス ライブラリと API | Microsoft Docs"
ms.custom: 
ms.date: 04/12/2017
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
caps.latest.revision: 12
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: b53b8acc2a6c56db6a9d8a9b7c685a2d400a53e1
ms.openlocfilehash: 34815268b707aa70d174a1bbc04c32276db8412d
ms.contentlocale: ja-jp
ms.lasthandoff: 05/02/2017

---

# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="4fa5e-102">追加のクラス ライブラリと API</span><span class="sxs-lookup"><span data-stu-id="4fa5e-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="4fa5e-103">.NET Framework は、絶えず進化を続けています。クロスプラットフォーム開発を強化するために、またはお客様にいち早く新しい機能を紹介するために、マイクロソフトは新機能のアウトオブバウンド (OOB) をリリースします。</span><span class="sxs-lookup"><span data-stu-id="4fa5e-103">The .NET Framework is constantly evolving and in order to improve cross-platform development or to introduce new functionality early to our customers, we release new features out of band (OOB).</span></span> <span data-ttu-id="4fa5e-104">ここでは、ドキュメントが用意されている OOB プロジェクトの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="4fa5e-104">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="4fa5e-105">さらに、いくつかのライブラリは、特定のプラットフォームまたは .NET Framework の実装を対象にしています。</span><span class="sxs-lookup"><span data-stu-id="4fa5e-105">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="4fa5e-106">たとえば、<xref:System.Text.CodePagesEncodingProvider> クラスを使用すると、.NET Framework で開発した UWP アプリでコード ページ エンコーディングを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="4fa5e-106">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="4fa5e-107">ここでは、これらのライブラリの一覧も示します。</span><span class="sxs-lookup"><span data-stu-id="4fa5e-107">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="4fa5e-108">OOB プロジェクト</span><span class="sxs-lookup"><span data-stu-id="4fa5e-108">OOB projects</span></span>
  
| <span data-ttu-id="4fa5e-109">プロジェクト</span><span class="sxs-lookup"><span data-stu-id="4fa5e-109">Project</span></span> | <span data-ttu-id="4fa5e-110">説明</span><span class="sxs-lookup"><span data-stu-id="4fa5e-110">Description</span></span> |  
| ------- | ----------- |  
| <span data-ttu-id="4fa5e-111"><xref:System.Collections.Immutable></span><span class="sxs-lookup"><span data-stu-id="4fa5e-111"><xref:System.Collections.Immutable></span></span> | <span data-ttu-id="4fa5e-112">スレッド セーフであり、内容が変更されないことが保証されているコレクションを提供します。</span><span class="sxs-lookup"><span data-stu-id="4fa5e-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <span data-ttu-id="4fa5e-113"><xref:System.Net.Http.WinHttpHandler></span><span class="sxs-lookup"><span data-stu-id="4fa5e-113"><xref:System.Net.Http.WinHttpHandler></span></span> | <span data-ttu-id="4fa5e-114">Windows の WinHTTP インターフェイスに基づいた <xref:System.Net.Http.HttpClient> のメッセージ ハンドラーを提供します。</span><span class="sxs-lookup"><span data-stu-id="4fa5e-114">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| [<span data-ttu-id="4fa5e-115">System.Numerics.Vectors</span><span class="sxs-lookup"><span data-stu-id="4fa5e-115">System.Numerics.Vectors</span></span>](https://msdn.microsoft.com/library/mt452176.aspx) | <span data-ttu-id="4fa5e-116">SIMD ハードウェア ベースのアクセラレータを利用できるベクター型のライブラリを提供します。</span><span class="sxs-lookup"><span data-stu-id="4fa5e-116">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <span data-ttu-id="4fa5e-117"><xref:System.Threading.Tasks.Dataflow></span><span class="sxs-lookup"><span data-stu-id="4fa5e-117"><xref:System.Threading.Tasks.Dataflow></span></span> | <span data-ttu-id="4fa5e-118">TPL データフロー ライブラリはデータ フロー コンポーネントを提供し、同時実行対応アプリケーションの堅牢性を強化します。</span><span class="sxs-lookup"><span data-stu-id="4fa5e-118">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="4fa5e-119">プラットフォーム固有のライブラリ</span><span class="sxs-lookup"><span data-stu-id="4fa5e-119">Platform-specific libraries</span></span>
  
| <span data-ttu-id="4fa5e-120">プロジェクト</span><span class="sxs-lookup"><span data-stu-id="4fa5e-120">Project</span></span> | <span data-ttu-id="4fa5e-121">説明</span><span class="sxs-lookup"><span data-stu-id="4fa5e-121">Description</span></span> |  
| ------- | ----------- |  
| <span data-ttu-id="4fa5e-122"><xref:System.Text.CodePagesEncodingProvider></span><span class="sxs-lookup"><span data-stu-id="4fa5e-122"><xref:System.Text.CodePagesEncodingProvider></span></span> | <span data-ttu-id="4fa5e-123"><xref:System.Text.EncodingProvider> クラスを拡張し、ユニバーサル Windows プラットフォームを対象とするアプリでコード ページ エンコーディングを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="4fa5e-123">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="4fa5e-124">プライベート API</span><span class="sxs-lookup"><span data-stu-id="4fa5e-124">Private APIs</span></span>  

<span data-ttu-id="4fa5e-125">この API は製品インフラストラクチャをサポートします。コードから直接使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="4fa5e-125">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
| <span data-ttu-id="4fa5e-126">API 名</span><span class="sxs-lookup"><span data-stu-id="4fa5e-126">API Name</span></span> |  
| -------- |  
| [<span data-ttu-id="4fa5e-127">s_isDebuggerCheckDisabledForTestPurposes フィールド</span><span class="sxs-lookup"><span data-stu-id="4fa5e-127">s_isDebuggerCheckDisabledForTestPurposes Field</span></span>](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |  
| [<span data-ttu-id="4fa5e-128">DataMemberFieldEditor クラス</span><span class="sxs-lookup"><span data-stu-id="4fa5e-128">DataMemberFieldEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |  
| [<span data-ttu-id="4fa5e-129">DataMemberListEditor クラス</span><span class="sxs-lookup"><span data-stu-id="4fa5e-129">DataMemberListEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |  
  
## <a name="see-also"></a><span data-ttu-id="4fa5e-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="4fa5e-130">See also</span></span>

[<span data-ttu-id="4fa5e-131">NET Framework および特別なリリース</span><span class="sxs-lookup"><span data-stu-id="4fa5e-131">The .NET Framework and Out-of-Band Releases</span></span>](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)


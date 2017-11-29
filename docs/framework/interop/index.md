---
title: "アンマネージ コードとの相互運用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2db5b8c2425637e24086f54e8ef69b0e5aac3633
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="307ea-102">アンマネージ コードとの相互運用</span><span class="sxs-lookup"><span data-stu-id="307ea-102">Interoperating with Unmanaged Code</span></span>
<span data-ttu-id="307ea-103">.NET Framework は、COM コンポーネント、COM+ サービス、外部のタイプ ライブラリ、各種のオペレーティング システム サービスとの相互運用を促進します。</span><span class="sxs-lookup"><span data-stu-id="307ea-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="307ea-104">データ型、メソッド署名、およびエラー処理機構は、マネージ オブジェクト モデルとアンマネージ オブジェクト モデルでは異なります。</span><span class="sxs-lookup"><span data-stu-id="307ea-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="307ea-105">.NET Framework コンポーネントとアンマネージ コードの間の相互運用を簡素化し、移行パスを簡単にするために、共通言語ランタイムがクライアントとサーバーの両方からこれらのオブジェクト モデルの違いを隠します。</span><span class="sxs-lookup"><span data-stu-id="307ea-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>  
  
 <span data-ttu-id="307ea-106">ランタイムの制御下で実行されるコードは、マネージ コードと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="307ea-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="307ea-107">逆に、ランタイムの外部で実行されるコードはアンマネージ コードと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="307ea-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="307ea-108">アンマネージ コードの例としては、COM コンポーネント、ActiveX インターフェイス、Win32 API 関数があります。</span><span class="sxs-lookup"><span data-stu-id="307ea-108">COM components, ActiveX interfaces, and Win32 API functions are examples of unmanaged code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="307ea-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="307ea-109">In This Section</span></span>  
 [<span data-ttu-id="307ea-110">アンマネージ コードとの相互運用性に関する方法</span><span class="sxs-lookup"><span data-stu-id="307ea-110">Interoperating with Unmanaged Code How-to Topics</span></span>](http://msdn.microsoft.com/en-us/ec21c6e1-e233-4cd9-95ae-b9b9cf807f9d)  
 <span data-ttu-id="307ea-111">アンマネージ コードとの相互運用の概念に関するドキュメントに用意されているすべての方法トピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="307ea-111">Provides links to all How-to topics found in the conceptual documentation for interoperating with unmanaged code.</span></span>  
  
 [<span data-ttu-id="307ea-112">.NET Framework への COM コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="307ea-112">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)  
 <span data-ttu-id="307ea-113">.NET Framework アプリケーションから COM コンポーネントを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="307ea-113">Describes how to use COM components from .NET Framework applications.</span></span>  
  
 [<span data-ttu-id="307ea-114">COM への .NET Framework コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="307ea-114">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="307ea-115">COM アプリケーションから .NET Framework コンポーネントを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="307ea-115">Describes how to use .NET Framework components from COM applications.</span></span>  
  
 [<span data-ttu-id="307ea-116">アンマネージ DLL 関数の処理</span><span class="sxs-lookup"><span data-stu-id="307ea-116">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="307ea-117">プラットフォーム呼び出しを使用して、アンマネージ DLL 関数を呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="307ea-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="307ea-118">相互運用のためのデザインの考慮事項</span><span class="sxs-lookup"><span data-stu-id="307ea-118">Design Considerations for Interoperation</span></span>](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)  
 <span data-ttu-id="307ea-119">統合 COM コンポーネントを記述するためのヒントを示します。</span><span class="sxs-lookup"><span data-stu-id="307ea-119">Provides tips for writing integrated COM components.</span></span>  
  
 [<span data-ttu-id="307ea-120">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="307ea-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)  
 <span data-ttu-id="307ea-121">COM 相互運用機能とプラットフォーム呼び出しのマーシャリングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="307ea-121">Describes marshaling for COM interop and platform invoke.</span></span>  
  
 [<span data-ttu-id="307ea-122">方法: HRESULT に例外を割り当てる</span><span class="sxs-lookup"><span data-stu-id="307ea-122">How to: Map HRESULTs and Exceptions</span></span>](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)  
 <span data-ttu-id="307ea-123">例外と HRESULT の間のマッピングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="307ea-123">Describes the mapping between exceptions and HRESULTs.</span></span>  
  
 [<span data-ttu-id="307ea-124">ジェネリック型を使用する相互運用</span><span class="sxs-lookup"><span data-stu-id="307ea-124">Interoperating Using Generic Types</span></span>](http://msdn.microsoft.com/en-us/26b88e03-085b-4b53-94ba-a5a9c709ce58)  
 <span data-ttu-id="307ea-125">COM 相互運用で使用する場合の、ジェネリック型の動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="307ea-125">Describes the behavior of generic types when used in COM interop.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="307ea-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="307ea-126">Related Sections</span></span>  
 [<span data-ttu-id="307ea-127">高度な COM 相互運用性</span><span class="sxs-lookup"><span data-stu-id="307ea-127">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 <span data-ttu-id="307ea-128">.NET Framework アプリケーションに COM コンポーネントを組み込む方法についての詳細情報へのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="307ea-128">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>

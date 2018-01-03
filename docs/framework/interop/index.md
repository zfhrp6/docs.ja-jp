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
ms.workload: dotnet
ms.openlocfilehash: f475877bcb7a794d1a58ef9202735e016363678b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="5b1e7-102">アンマネージ コードとの相互運用</span><span class="sxs-lookup"><span data-stu-id="5b1e7-102">Interoperating with Unmanaged Code</span></span>
<span data-ttu-id="5b1e7-103">.NET Framework は、COM コンポーネント、COM+ サービス、外部のタイプ ライブラリ、各種のオペレーティング システム サービスとの相互運用を促進します。</span><span class="sxs-lookup"><span data-stu-id="5b1e7-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="5b1e7-104">データ型、メソッド署名、およびエラー処理機構は、マネージ オブジェクト モデルとアンマネージ オブジェクト モデルでは異なります。</span><span class="sxs-lookup"><span data-stu-id="5b1e7-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="5b1e7-105">.NET Framework コンポーネントとアンマネージ コードの間の相互運用を簡素化し、移行パスを簡単にするために、共通言語ランタイムがクライアントとサーバーの両方からこれらのオブジェクト モデルの違いを隠します。</span><span class="sxs-lookup"><span data-stu-id="5b1e7-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>  
  
 <span data-ttu-id="5b1e7-106">ランタイムの制御下で実行されるコードは、マネージ コードと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="5b1e7-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="5b1e7-107">逆に、ランタイムの外部で実行されるコードはアンマネージ コードと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="5b1e7-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="5b1e7-108">アンマネージ コードの例としては、COM コンポーネント、ActiveX インターフェイス、Win32 API 関数があります。</span><span class="sxs-lookup"><span data-stu-id="5b1e7-108">COM components, ActiveX interfaces, and Win32 API functions are examples of unmanaged code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5b1e7-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5b1e7-109">In This Section</span></span>  
 [<span data-ttu-id="5b1e7-110">アンマネージ コードとの相互運用性に関する方法</span><span class="sxs-lookup"><span data-stu-id="5b1e7-110">Interoperating with Unmanaged Code How-to Topics</span></span>](http://msdn.microsoft.com/en-us/ec21c6e1-e233-4cd9-95ae-b9b9cf807f9d)  
 <span data-ttu-id="5b1e7-111">アンマネージ コードとの相互運用の概念に関するドキュメントに用意されているすべての方法トピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="5b1e7-111">Provides links to all How-to topics found in the conceptual documentation for interoperating with unmanaged code.</span></span>  
  
 [<span data-ttu-id="5b1e7-112">.NET Framework への COM コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="5b1e7-112">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)  
 <span data-ttu-id="5b1e7-113">.NET Framework アプリケーションから COM コンポーネントを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5b1e7-113">Describes how to use COM components from .NET Framework applications.</span></span>  
  
 [<span data-ttu-id="5b1e7-114">COM への .NET Framework コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="5b1e7-114">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="5b1e7-115">COM アプリケーションから .NET Framework コンポーネントを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5b1e7-115">Describes how to use .NET Framework components from COM applications.</span></span>  
  
 [<span data-ttu-id="5b1e7-116">アンマネージ DLL 関数の処理</span><span class="sxs-lookup"><span data-stu-id="5b1e7-116">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="5b1e7-117">プラットフォーム呼び出しを使用して、アンマネージ DLL 関数を呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5b1e7-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="5b1e7-118">相互運用のためのデザインの考慮事項</span><span class="sxs-lookup"><span data-stu-id="5b1e7-118">Design Considerations for Interoperation</span></span>](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)  
 <span data-ttu-id="5b1e7-119">統合 COM コンポーネントを記述するためのヒントを示します。</span><span class="sxs-lookup"><span data-stu-id="5b1e7-119">Provides tips for writing integrated COM components.</span></span>  
  
 [<span data-ttu-id="5b1e7-120">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="5b1e7-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)  
 <span data-ttu-id="5b1e7-121">COM 相互運用機能とプラットフォーム呼び出しのマーシャリングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5b1e7-121">Describes marshaling for COM interop and platform invoke.</span></span>  
  
 [<span data-ttu-id="5b1e7-122">方法: HRESULT に例外を割り当てる</span><span class="sxs-lookup"><span data-stu-id="5b1e7-122">How to: Map HRESULTs and Exceptions</span></span>](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)  
 <span data-ttu-id="5b1e7-123">例外と HRESULT の間のマッピングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5b1e7-123">Describes the mapping between exceptions and HRESULTs.</span></span>  
  
 [<span data-ttu-id="5b1e7-124">ジェネリック型を使用する相互運用</span><span class="sxs-lookup"><span data-stu-id="5b1e7-124">Interoperating Using Generic Types</span></span>](http://msdn.microsoft.com/en-us/26b88e03-085b-4b53-94ba-a5a9c709ce58)  
 <span data-ttu-id="5b1e7-125">COM 相互運用で使用する場合の、ジェネリック型の動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="5b1e7-125">Describes the behavior of generic types when used in COM interop.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5b1e7-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b1e7-126">Related Sections</span></span>  
 [<span data-ttu-id="5b1e7-127">高度な COM 相互運用性</span><span class="sxs-lookup"><span data-stu-id="5b1e7-127">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 <span data-ttu-id="5b1e7-128">.NET Framework アプリケーションに COM コンポーネントを組み込む方法についての詳細情報へのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="5b1e7-128">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>

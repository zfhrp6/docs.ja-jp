---
title: failedQI MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 87fe67e1e64d69912095e1d9587d277805a3eb80
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="failedqi-mda"></a><span data-ttu-id="d65f5-102">failedQI MDA</span><span class="sxs-lookup"><span data-stu-id="d65f5-102">failedQI MDA</span></span>
<span data-ttu-id="d65f5-103">`failedQI` マネージ デバッグ アシスタント (MDA: Managed Debugging Asssitant) は、ランタイムがランタイム呼び出し可能ラッパー (RCW: Runtime Callable Wrapper) の代わりに COM インターフェイス ポインター上の `QueryInterface` を呼び出し、その `QueryInterface` 呼び出しに失敗するとアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="d65f5-103">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d65f5-104">症状</span><span class="sxs-lookup"><span data-stu-id="d65f5-104">Symptoms</span></span>  
 <span data-ttu-id="d65f5-105">RCW でのキャストに失敗します。または、RCW からの COM 呼び出しが予期せず失敗します。</span><span class="sxs-lookup"><span data-stu-id="d65f5-105">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d65f5-106">原因</span><span class="sxs-lookup"><span data-stu-id="d65f5-106">Cause</span></span>  
  
-   <span data-ttu-id="d65f5-107">正しくないコンテキストから呼び出しが実行されました。</span><span class="sxs-lookup"><span data-stu-id="d65f5-107">The call is made from the wrong context.</span></span>  
  
-   <span data-ttu-id="d65f5-108">呼び出しが正しくないコンテキストで試行されたため、登録されたプロキシが `QueryInterface` 呼び出しに失敗しています。</span><span class="sxs-lookup"><span data-stu-id="d65f5-108">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
-   <span data-ttu-id="d65f5-109">OLE 所有のプロキシがエラー HRESULT を返しました。</span><span class="sxs-lookup"><span data-stu-id="d65f5-109">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d65f5-110">解像度</span><span class="sxs-lookup"><span data-stu-id="d65f5-110">Resolution</span></span>  
 <span data-ttu-id="d65f5-111">COM 規則についての MSDN ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d65f5-111">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d65f5-112">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="d65f5-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="d65f5-113">`QueryInterface` 呼び出しに失敗すると、コンテキストが切り替えられ、エラー時に正しくないコンテキストであったことを確認するために、`QueryInterface` 呼び出しが再試行されます。</span><span class="sxs-lookup"><span data-stu-id="d65f5-113">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d65f5-114">出力</span><span class="sxs-lookup"><span data-stu-id="d65f5-114">Output</span></span>  
 <span data-ttu-id="d65f5-115">インターフェイスのマネージ名、インターフェイスの GUID、およびエラー HRESULT です。</span><span class="sxs-lookup"><span data-stu-id="d65f5-115">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d65f5-116">構成</span><span class="sxs-lookup"><span data-stu-id="d65f5-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d65f5-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="d65f5-117">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="d65f5-118">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="d65f5-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="d65f5-119">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="d65f5-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)

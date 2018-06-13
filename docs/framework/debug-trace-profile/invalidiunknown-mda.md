---
title: invalidIUnknown MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
author: mairaw
ms.author: mairaw
ms.openlocfilehash: db360a3b7c5f70596d5d5855b8e38dae5d484c42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390176"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="5e8fc-102">invalidIUnknown MDA</span><span class="sxs-lookup"><span data-stu-id="5e8fc-102">invalidIUnknown MDA</span></span>
<span data-ttu-id="5e8fc-103">`invalidIUnknown` マネージ デバッグ アシスタント (MDA: Managed Debugging Assistant) は、無効な `IUnknown` ポインターがネイティブ コードからマネージ コードに渡されるとアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="5e8fc-103">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="5e8fc-104">`IUnknown` インターフェイスが照会されたときに、`IUnknown` は、成功したことを返すことができませんでした。</span><span class="sxs-lookup"><span data-stu-id="5e8fc-104">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5e8fc-105">症状</span><span class="sxs-lookup"><span data-stu-id="5e8fc-105">Symptoms</span></span>  
 <span data-ttu-id="5e8fc-106">引数のマーシャリング中に COM インターフェイス ポインターをマーシャリングすると、予期しないエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="5e8fc-106">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5e8fc-107">原因</span><span class="sxs-lookup"><span data-stu-id="5e8fc-107">Cause</span></span>  
 <span data-ttu-id="5e8fc-108">CLR に渡された COM インターフェイスで、`QueryInterface` の実装が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="5e8fc-108">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5e8fc-109">解像度</span><span class="sxs-lookup"><span data-stu-id="5e8fc-109">Resolution</span></span>  
 <span data-ttu-id="5e8fc-110">`QueryInterface` の実装を修正します。</span><span class="sxs-lookup"><span data-stu-id="5e8fc-110">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5e8fc-111">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="5e8fc-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="5e8fc-112">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="5e8fc-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5e8fc-113">出力</span><span class="sxs-lookup"><span data-stu-id="5e8fc-113">Output</span></span>  
 <span data-ttu-id="5e8fc-114">エラーの説明です。</span><span class="sxs-lookup"><span data-stu-id="5e8fc-114">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5e8fc-115">構成</span><span class="sxs-lookup"><span data-stu-id="5e8fc-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e8fc-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e8fc-116">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="5e8fc-117">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="5e8fc-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="5e8fc-118">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="5e8fc-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)

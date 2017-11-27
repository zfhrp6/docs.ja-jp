---
title: invalidFunctionPointerInDelegate MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- invalidFunctionPointerInDelegate MDA
- managed debugging assistants (MDAs), invalid function pointer to delegates
- MDAs (managed debugging assistants), invalid function pointer to delegates
- function pointers, invalid
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- invalid function pointers
ms.assetid: 99ae44f1-783e-49a9-9009-24f54bbd0f09
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5e9fd1faacc7be5b95e2bab0d8fdbee105e35498
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="bfd60-102">invalidFunctionPointerInDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="bfd60-102">invalidFunctionPointerInDelegate MDA</span></span>
<span data-ttu-id="bfd60-103">ネイティブ関数ポインターに対するデリゲートを作成するときに、無効な関数ポインターが渡されると、`invalidFunctionPointerInDelegate` マネージ デバッグ アシスタント (MDA) がアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="bfd60-103">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="bfd60-104">症状</span><span class="sxs-lookup"><span data-stu-id="bfd60-104">Symptoms</span></span>  
 <span data-ttu-id="bfd60-105">関数ポインターでデリゲートを使用すると、アクセス違反または予期しないメモリの破損が発生します。</span><span class="sxs-lookup"><span data-stu-id="bfd60-105">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="bfd60-106">原因</span><span class="sxs-lookup"><span data-stu-id="bfd60-106">Cause</span></span>  
 <span data-ttu-id="bfd60-107">無効な関数ポインターが指定されました。</span><span class="sxs-lookup"><span data-stu-id="bfd60-107">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="bfd60-108">解決策</span><span class="sxs-lookup"><span data-stu-id="bfd60-108">Resolution</span></span>  
 <span data-ttu-id="bfd60-109">有効な関数ポインターを指定します。</span><span class="sxs-lookup"><span data-stu-id="bfd60-109">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="bfd60-110">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="bfd60-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="bfd60-111">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="bfd60-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="bfd60-112">出力</span><span class="sxs-lookup"><span data-stu-id="bfd60-112">Output</span></span>  
 <span data-ttu-id="bfd60-113">無効な関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="bfd60-113">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="bfd60-114">構成</span><span class="sxs-lookup"><span data-stu-id="bfd60-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bfd60-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="bfd60-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="bfd60-116">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="bfd60-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="bfd60-117">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="bfd60-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)

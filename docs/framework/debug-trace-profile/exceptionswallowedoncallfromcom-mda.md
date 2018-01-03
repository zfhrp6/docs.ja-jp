---
title: exceptionSwallowedOnCallFromCom MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c20c4e0b6c1c711b2044bc3ba32d00447220cb8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="9d664-102">exceptionSwallowedOnCallFromCom MDA</span><span class="sxs-lookup"><span data-stu-id="9d664-102">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="9d664-103">アンマネージ HRESULT 戻り値型を持たないメソッドを介して COM から呼び出された 共通言語ランタイム (CLR) コードから、例外がスローされると、`exceptionSwallowedOnCallFromCOM` マネージ デバッグ アシスタント (MDA) がアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="9d664-103">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="9d664-104">症状</span><span class="sxs-lookup"><span data-stu-id="9d664-104">Symptoms</span></span>  
 <span data-ttu-id="9d664-105">COM からマネージ コンポーネントを呼び出すと、値 FALSE または 0 が返されます。</span><span class="sxs-lookup"><span data-stu-id="9d664-105">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="9d664-106">あるいは、メソッドの戻り値の型が void の場合、メソッド実行中に例外がスローされたという通知がない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9d664-106">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="9d664-107">この場合、例外は自動的にキャッチされ、COM 呼び出し元に実行が戻ります。</span><span class="sxs-lookup"><span data-stu-id="9d664-107">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="9d664-108">原因</span><span class="sxs-lookup"><span data-stu-id="9d664-108">Cause</span></span>  
 <span data-ttu-id="9d664-109">例外がスローされましたが、それを報告する有効な方法がありません。</span><span class="sxs-lookup"><span data-stu-id="9d664-109">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="9d664-110">解決策</span><span class="sxs-lookup"><span data-stu-id="9d664-110">Resolution</span></span>  
 <span data-ttu-id="9d664-111">情報提供専用です。必ずしもバグを示すものではありません。</span><span class="sxs-lookup"><span data-stu-id="9d664-111">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9d664-112">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="9d664-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="9d664-113">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="9d664-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="9d664-114">自動的にキャッチされた例外を報告するだけです。</span><span class="sxs-lookup"><span data-stu-id="9d664-114">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9d664-115">出力</span><span class="sxs-lookup"><span data-stu-id="9d664-115">Output</span></span>  
 <span data-ttu-id="9d664-116">メソッド名、型名、例外メッセージが含まれている情報メッセージ。</span><span class="sxs-lookup"><span data-stu-id="9d664-116">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9d664-117">構成</span><span class="sxs-lookup"><span data-stu-id="9d664-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d664-118">参照</span><span class="sxs-lookup"><span data-stu-id="9d664-118">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="9d664-119">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="9d664-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="9d664-120">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="9d664-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)

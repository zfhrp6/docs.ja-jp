---
title: gcUnmanagedToManaged MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GC unmanaged to managed
- transitioning threads unmanaged to managed code
- GcUnmanagedToManaged MDA
- threading [.NET Framework], garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
- unmanaged to managed garbage collection
ms.assetid: 103eb3a3-1cf0-4406-8a9a-a7798fdc22d1
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e8d2391ba9ba1d17f2cbce54f52863f74a5dc646
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="afe8d-102">gcUnmanagedToManaged MDA</span><span class="sxs-lookup"><span data-stu-id="afe8d-102">gcUnmanagedToManaged MDA</span></span>
<span data-ttu-id="afe8d-103">`gcUnmanagedToManaged` マネージ デバッグ アシスタント (MDA: Managed Debugging Assistant) は、スレッドがアンマネージ コードからマネージ コードに遷移する時に、毎回ガベージ コレクションが行われるようにします。</span><span class="sxs-lookup"><span data-stu-id="afe8d-103">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="afe8d-104">症状</span><span class="sxs-lookup"><span data-stu-id="afe8d-104">Symptoms</span></span>  
 <span data-ttu-id="afe8d-105">COM およびプラットフォーム呼び出しを使用してアンマネージ ユーザー コンポーネントを実行中のアプリケーションによって、CLR で非確定的なアクセス違反が発生します。</span><span class="sxs-lookup"><span data-stu-id="afe8d-105">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="afe8d-106">原因</span><span class="sxs-lookup"><span data-stu-id="afe8d-106">Cause</span></span>  
 <span data-ttu-id="afe8d-107">アプリケーションがアンマネージ ユーザー コンポーネントを実行中の場合、それらのコンポーネントによって、ガベージ コレクトされたヒープが破損された可能性があります。</span><span class="sxs-lookup"><span data-stu-id="afe8d-107">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="afe8d-108">これが原因で、ガベージ コレクターがオブジェクト グラフをウォークしようとしたときに、CLR でアクセス違反が発生します。</span><span class="sxs-lookup"><span data-stu-id="afe8d-108">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="afe8d-109">解像度</span><span class="sxs-lookup"><span data-stu-id="afe8d-109">Resolution</span></span>  
 <span data-ttu-id="afe8d-110">このアシスタントを有効にすると、各マネージ遷移の前にガベージ コレクションが必ず行われるようになるため、アンマネージ コンポーネントがガベージ コレクトされたヒープを破損してから、アクセス違反が発生するまでの時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="afe8d-110">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="afe8d-111">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="afe8d-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="afe8d-112">スレッドがアンマネージ コードからマネージ コードに遷移する時に、毎回ガベージ コレクションが行われるようになります。</span><span class="sxs-lookup"><span data-stu-id="afe8d-112">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="afe8d-113">出力</span><span class="sxs-lookup"><span data-stu-id="afe8d-113">Output</span></span>  
 <span data-ttu-id="afe8d-114">この MDA は、出力を生成しません。</span><span class="sxs-lookup"><span data-stu-id="afe8d-114">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="afe8d-115">構成</span><span class="sxs-lookup"><span data-stu-id="afe8d-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="afe8d-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="afe8d-116">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="afe8d-117">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="afe8d-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="afe8d-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="afe8d-118">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)  
 [<span data-ttu-id="afe8d-119">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="afe8d-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)

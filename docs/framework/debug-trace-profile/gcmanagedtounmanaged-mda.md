---
title: gcManagedToUnmanaged MDA
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
- GcManagedToUnmanaged MDA
- GC managed to unmanaged
- transitioning threads managed to unmanaged code
- threading [.NET Framework], garbage collection
- managed to unmanaged garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
ms.assetid: 7417f837-805e-4fed-a430-ca919c8421dc
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d461ff702f756df6d599d7082edc6c5c4719c537
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="gcmanagedtounmanaged-mda"></a><span data-ttu-id="56216-102">gcManagedToUnmanaged MDA</span><span class="sxs-lookup"><span data-stu-id="56216-102">gcManagedToUnmanaged MDA</span></span>
<span data-ttu-id="56216-103">`gcManagedToUnmanaged` マネージ デバッグ アシスタント (MDA: Managed Debugging Assistant) は、スレッドがマネージ コードからアンマネージ コードに遷移する時に、毎回ガベージ コレクションがなされるようにします。</span><span class="sxs-lookup"><span data-stu-id="56216-103">The `gcManagedToUnmanaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="56216-104">症状</span><span class="sxs-lookup"><span data-stu-id="56216-104">Symptoms</span></span>  
 <span data-ttu-id="56216-105">アンマネージ ユーザー コンポーネントは、COM に公開されたマネージ オブジェクトを使おうとすると、アクセス違反をスローします。</span><span class="sxs-lookup"><span data-stu-id="56216-105">An unmanaged user component throws an access violation when trying to use a managed object that had been exposed to COM.</span></span> <span data-ttu-id="56216-106">COM オブジェクトはリリース済みのように表示されます。</span><span class="sxs-lookup"><span data-stu-id="56216-106">The COM object appears to have been released.</span></span> <span data-ttu-id="56216-107">アクセス違反は非確定です。</span><span class="sxs-lookup"><span data-stu-id="56216-107">The access violation is nondeterministic.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="56216-108">原因</span><span class="sxs-lookup"><span data-stu-id="56216-108">Cause</span></span>  
 <span data-ttu-id="56216-109">アンマネージ コンポーネントがマネージ COM オブジェクトを正しくカウントする参照でない場合、ランタイムは、アンマネージ コンポーネントがオブジェクトへの参照を保持していると、COM に公開されたマネージ オブジェクトを収集できます。</span><span class="sxs-lookup"><span data-stu-id="56216-109">If an unmanaged component is not reference counting a managed COM object correctly, then the runtime could collect a managed object exposed to COM when the unmanaged component still holds a reference to the object.</span></span> <span data-ttu-id="56216-110">ランタイムはガベージ コレクション中に <xref:System.Runtime.InteropServices.Marshal.Release%2A> を呼び出すので、ユーザー コンポーネントがガベージ コレクションの発生前にオブジェクトを使用すると、それは収集されないことになります。</span><span class="sxs-lookup"><span data-stu-id="56216-110">The runtime calls <xref:System.Runtime.InteropServices.Marshal.Release%2A> during garbage collections, so if the user component uses the object before the garbage collection occurs, then it will not yet have been collected.</span></span> <span data-ttu-id="56216-111">これが非確定の原因です。</span><span class="sxs-lookup"><span data-stu-id="56216-111">This is the source of the nondeterminism.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="56216-112">解決策</span><span class="sxs-lookup"><span data-stu-id="56216-112">Resolution</span></span>  
 <span data-ttu-id="56216-113">このアシスタントを有効にすると、オブジェクトが収集の対象になってから <xref:System.Runtime.InteropServices.Marshal.Release%2A> が呼び出されるまでの時間が短縮し、収集されるオブジェクトへのアクセスを最初に試みるアンマネージ コンポーネントの追跡に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="56216-113">Enabling this assistant reduces the time between when the object is eligible for collection and <xref:System.Runtime.InteropServices.Marshal.Release%2A> is called, helping to track down which unmanaged component first tries to access the collected object.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="56216-114">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="56216-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="56216-115">スレッドがマネージ コードからアンマネージ コードに遷移する時に、毎回ガベージ コレクションがなされるようになります。</span><span class="sxs-lookup"><span data-stu-id="56216-115">Causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="56216-116">出力</span><span class="sxs-lookup"><span data-stu-id="56216-116">Output</span></span>  
 <span data-ttu-id="56216-117">この MDA は、出力を生成しません。</span><span class="sxs-lookup"><span data-stu-id="56216-117">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="56216-118">構成</span><span class="sxs-lookup"><span data-stu-id="56216-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="56216-119">参照</span><span class="sxs-lookup"><span data-stu-id="56216-119">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="56216-120">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="56216-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="56216-121">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="56216-121">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)  
 [<span data-ttu-id="56216-122">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="56216-122">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)

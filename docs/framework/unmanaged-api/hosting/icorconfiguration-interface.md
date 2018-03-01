---
title: "ICorConfiguration インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorConfiguration
helpviewer_keywords:
- ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: af9a7d4bb1d38fd4a81e954074b074325409ee5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="47eb3-102">ICorConfiguration インターフェイス</span><span class="sxs-lookup"><span data-stu-id="47eb3-102">ICorConfiguration Interface</span></span>
<span data-ttu-id="47eb3-103">共通言語ランタイム (CLR) を構成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="47eb3-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="47eb3-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="47eb3-104">Methods</span></span>  
  
|<span data-ttu-id="47eb3-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="47eb3-105">Method</span></span>|<span data-ttu-id="47eb3-106">説明</span><span class="sxs-lookup"><span data-stu-id="47eb3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="47eb3-107">AddDebuggerSpecialThread メソッド</span><span class="sxs-lookup"><span data-stu-id="47eb3-107">AddDebuggerSpecialThread Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="47eb3-108">デバッグ サービスを特定のスレッドがデバッガーがマネージまたはアンマネージ デバッグ シナリオの中に停止したアプリケーションの実行を続行できることを示します。</span><span class="sxs-lookup"><span data-stu-id="47eb3-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="47eb3-109">SetDebuggerThreadControl メソッド</span><span class="sxs-lookup"><span data-stu-id="47eb3-109">SetDebuggerThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="47eb3-110">デバッグ サービスは CLR スレッドをブロックまたはブロック解除されたデバッグときに呼び出すコールバック インターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="47eb3-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="47eb3-111">SetGCHostControl メソッド</span><span class="sxs-lookup"><span data-stu-id="47eb3-111">SetGCHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="47eb3-112">仮想メモリの制限を変更するホストに要求、ガベージ コレクターが使用するコールバック インターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="47eb3-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="47eb3-113">SetGCThreadControl メソッド</span><span class="sxs-lookup"><span data-stu-id="47eb3-113">SetGCThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="47eb3-114">それ以外の場合のみがブロックされるガベージ コレクションの非ランタイム タスクのスレッドのスケジュールのコールバック インターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="47eb3-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="47eb3-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="47eb3-115">Requirements</span></span>  
 <span data-ttu-id="47eb3-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="47eb3-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47eb3-117">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="47eb3-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="47eb3-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="47eb3-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47eb3-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47eb3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47eb3-120">参照</span><span class="sxs-lookup"><span data-stu-id="47eb3-120">See Also</span></span>  
 [<span data-ttu-id="47eb3-121">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="47eb3-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="47eb3-122">CorRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="47eb3-122">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)

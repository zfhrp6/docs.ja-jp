---
title: "ICorDebugStackWalk インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk
helpviewer_keywords: ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 018ed69e52efd21ca25029284c70f1c8493d877f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="2aed5-102">ICorDebugStackWalk インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2aed5-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="2aed5-103">スレッドのスタック上のマネージ メソッド (フレーム) を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="2aed5-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2aed5-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="2aed5-104">Methods</span></span>  
  
|<span data-ttu-id="2aed5-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="2aed5-105">Method</span></span>|<span data-ttu-id="2aed5-106">説明</span><span class="sxs-lookup"><span data-stu-id="2aed5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2aed5-107">GetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="2aed5-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="2aed5-108">現在のフレームのコンテキストを返します、`ICorDebugStackWalk`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="2aed5-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="2aed5-109">SetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="2aed5-109">SetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="2aed5-110">セット、`ICorDebugStackWalk`オブジェクトの現在のコンテキストのスレッドの有効なコンテキストにします。</span><span class="sxs-lookup"><span data-stu-id="2aed5-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="2aed5-111">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="2aed5-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|<span data-ttu-id="2aed5-112">移動、`ICorDebugStackWalk`次のフレームにオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="2aed5-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="2aed5-113">GetFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="2aed5-113">GetFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|<span data-ttu-id="2aed5-114">内の現在のフレームを取得、`ICorDebugStackWalk`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="2aed5-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2aed5-115">コメント</span><span class="sxs-lookup"><span data-stu-id="2aed5-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2aed5-116">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="2aed5-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2aed5-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="2aed5-117">Requirements</span></span>  
 <span data-ttu-id="2aed5-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2aed5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2aed5-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2aed5-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2aed5-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2aed5-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2aed5-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2aed5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aed5-122">参照</span><span class="sxs-lookup"><span data-stu-id="2aed5-122">See Also</span></span>  
 [<span data-ttu-id="2aed5-123">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2aed5-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2aed5-124">デバッグ</span><span class="sxs-lookup"><span data-stu-id="2aed5-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

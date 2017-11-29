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
ms.openlocfilehash: 0c8a4421b716614081368755388bd2ab8d8fe22e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="a631a-102">ICorDebugStackWalk インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a631a-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="a631a-103">スレッドのスタック上のマネージ メソッド (フレーム) を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a631a-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a631a-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="a631a-104">Methods</span></span>  
  
|<span data-ttu-id="a631a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a631a-105">Method</span></span>|<span data-ttu-id="a631a-106">説明</span><span class="sxs-lookup"><span data-stu-id="a631a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a631a-107">GetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="a631a-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="a631a-108">現在のフレームのコンテキストを返します、`ICorDebugStackWalk`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a631a-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="a631a-109">SetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="a631a-109">SetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="a631a-110">セット、`ICorDebugStackWalk`オブジェクトの現在のコンテキストのスレッドの有効なコンテキストにします。</span><span class="sxs-lookup"><span data-stu-id="a631a-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="a631a-111">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="a631a-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|<span data-ttu-id="a631a-112">移動、`ICorDebugStackWalk`次のフレームにオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a631a-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="a631a-113">GetFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="a631a-113">GetFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|<span data-ttu-id="a631a-114">内の現在のフレームを取得、`ICorDebugStackWalk`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a631a-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a631a-115">コメント</span><span class="sxs-lookup"><span data-stu-id="a631a-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a631a-116">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="a631a-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a631a-117">要件</span><span class="sxs-lookup"><span data-stu-id="a631a-117">Requirements</span></span>  
 <span data-ttu-id="a631a-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a631a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a631a-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a631a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a631a-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a631a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a631a-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a631a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a631a-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="a631a-122">See Also</span></span>  
 [<span data-ttu-id="a631a-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a631a-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a631a-124">デバッグ</span><span class="sxs-lookup"><span data-stu-id="a631a-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

---
title: "ICorDebugThread3 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread3
helpviewer_keywords: ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6cfb3267637210567f3df9fa08bb75135dc585ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="86a78-102">ICorDebugThread3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="86a78-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="86a78-103">エントリ ポイントを提供、 [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)と対応するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="86a78-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="86a78-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="86a78-104">Methods</span></span>  
  
|<span data-ttu-id="86a78-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="86a78-105">Method</span></span>|<span data-ttu-id="86a78-106">説明</span><span class="sxs-lookup"><span data-stu-id="86a78-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="86a78-107">CreateStackWalk メソッド</span><span class="sxs-lookup"><span data-stu-id="86a78-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="86a78-108">作成、 [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)のスレッドがスタックをアンワインドするオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="86a78-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="86a78-109">GetActiveInternalFrames メソッド</span><span class="sxs-lookup"><span data-stu-id="86a78-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="86a78-110">内部フレームの配列を返します ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)オブジェクト)、スタックにします。</span><span class="sxs-lookup"><span data-stu-id="86a78-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86a78-111">コメント</span><span class="sxs-lookup"><span data-stu-id="86a78-111">Remarks</span></span>  
 <span data-ttu-id="86a78-112">`ICorDebugThread3`ICorDebugThread インターフェイスを論理的な拡張です。</span><span class="sxs-lookup"><span data-stu-id="86a78-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86a78-113">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="86a78-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86a78-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="86a78-114">Requirements</span></span>  
 <span data-ttu-id="86a78-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="86a78-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86a78-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86a78-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86a78-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86a78-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86a78-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86a78-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86a78-119">参照</span><span class="sxs-lookup"><span data-stu-id="86a78-119">See Also</span></span>  
 [<span data-ttu-id="86a78-120">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="86a78-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="86a78-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="86a78-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

---
title: ICorDebugThread3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugThread3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3
helpviewer_keywords:
- ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9cb9217282af53d9788190844e4e52d5405ee2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422777"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="9dbc5-102">ICorDebugThread3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9dbc5-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="9dbc5-103">エントリ ポイントを提供、 [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)と対応するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="9dbc5-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9dbc5-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="9dbc5-104">Methods</span></span>  
  
|<span data-ttu-id="9dbc5-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9dbc5-105">Method</span></span>|<span data-ttu-id="9dbc5-106">説明</span><span class="sxs-lookup"><span data-stu-id="9dbc5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9dbc5-107">CreateStackWalk メソッド</span><span class="sxs-lookup"><span data-stu-id="9dbc5-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="9dbc5-108">作成、 [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)のスレッドがスタックをアンワインドするオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="9dbc5-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="9dbc5-109">GetActiveInternalFrames メソッド</span><span class="sxs-lookup"><span data-stu-id="9dbc5-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="9dbc5-110">内部フレームの配列を返します ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)オブジェクト)、スタックにします。</span><span class="sxs-lookup"><span data-stu-id="9dbc5-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9dbc5-111">コメント</span><span class="sxs-lookup"><span data-stu-id="9dbc5-111">Remarks</span></span>  
 <span data-ttu-id="9dbc5-112">`ICorDebugThread3` ICorDebugThread インターフェイスを論理的な拡張です。</span><span class="sxs-lookup"><span data-stu-id="9dbc5-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9dbc5-113">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="9dbc5-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dbc5-114">要件</span><span class="sxs-lookup"><span data-stu-id="9dbc5-114">Requirements</span></span>  
 <span data-ttu-id="9dbc5-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9dbc5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dbc5-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9dbc5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9dbc5-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9dbc5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9dbc5-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dbc5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dbc5-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="9dbc5-119">See Also</span></span>  
 [<span data-ttu-id="9dbc5-120">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9dbc5-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9dbc5-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="9dbc5-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

---
title: "ICorDebugManagedCallback3 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback3
helpviewer_keywords: ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d2f24cc8fbd8533ef6717bc1dcd1baab0ea9ab45
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="5f691-102">ICorDebugManagedCallback3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f691-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="5f691-103">有効なカスタムのデバッガー通知が発生したことを示すコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="5f691-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5f691-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="5f691-104">Methods</span></span>  
  
|<span data-ttu-id="5f691-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="5f691-105">Method</span></span>|<span data-ttu-id="5f691-106">説明</span><span class="sxs-lookup"><span data-stu-id="5f691-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5f691-107">CustomNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="5f691-107">CustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="5f691-108">有効なカスタムのデバッガー通知が発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="5f691-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f691-109">コメント</span><span class="sxs-lookup"><span data-stu-id="5f691-109">Remarks</span></span>  
 <span data-ttu-id="5f691-110">このインターフェイスは、論理的に拡張、 [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)と[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="5f691-110">This interface is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f691-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="5f691-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f691-112">要件</span><span class="sxs-lookup"><span data-stu-id="5f691-112">Requirements</span></span>  
 <span data-ttu-id="5f691-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5f691-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f691-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f691-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f691-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f691-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f691-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f691-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f691-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f691-117">See Also</span></span>  
 [<span data-ttu-id="5f691-118">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f691-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 [<span data-ttu-id="5f691-119">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f691-119">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="5f691-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f691-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="5f691-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="5f691-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

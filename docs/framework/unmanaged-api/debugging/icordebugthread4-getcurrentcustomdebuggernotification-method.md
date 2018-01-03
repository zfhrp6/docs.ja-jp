---
title: "ICorDebugThread4::GetCurrentCustomDebuggerNotification メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread4.GetCurrentCustomDebuggerNotification Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread4::GetCurrentCustomDebuggerNotification
helpviewer_keywords:
- GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
- ICorDebugThread4::GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
ms.assetid: 57e0f2d2-5f0e-4e2d-99ec-3f26632eb693
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a408e011a2eff6a10a6ce1db03a6282c45044a37
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="3d083-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="3d083-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>
<span data-ttu-id="3d083-103">現在の取得[icordebugmanagedcallback 3::customnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)現在のスレッド上のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="3d083-103">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d083-104">構文</span><span class="sxs-lookup"><span data-stu-id="3d083-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentCustomDebuggerNotification(  
    [out] ICorDebugValue **ppNotificationObject  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d083-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3d083-105">Parameters</span></span>  
 `ppNOtificationObject`  
 <span data-ttu-id="3d083-106">[out]現在へのポインター`ICorDebugManagedCallback3::CustomNotification`現在のスレッド上のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="3d083-106">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d083-107">コメント</span><span class="sxs-lookup"><span data-stu-id="3d083-107">Remarks</span></span>  
 <span data-ttu-id="3d083-108">値`ppNotificationObject`内から、メソッドが呼び出されない場合は null、`ICorDebugManagedCallback3::CustomNotification`コールバック、現在の通知オブジェクトが存在しない場合またはします。</span><span class="sxs-lookup"><span data-stu-id="3d083-108">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d083-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="3d083-109">Requirements</span></span>  
 <span data-ttu-id="3d083-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3d083-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d083-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d083-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d083-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d083-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d083-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d083-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d083-114">参照</span><span class="sxs-lookup"><span data-stu-id="3d083-114">See Also</span></span>  
 [<span data-ttu-id="3d083-115">ICorDebugThread4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d083-115">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="3d083-116">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d083-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="3d083-117">デバッグ</span><span class="sxs-lookup"><span data-stu-id="3d083-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

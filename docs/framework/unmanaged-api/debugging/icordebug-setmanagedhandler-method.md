---
title: "ICorDebug::SetManagedHandler メソッド"
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
- ICorDebug.SetManagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dde32b6a8251474c4254e35a3a1ba3ba3bafcb8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="24378-102">ICorDebug::SetManagedHandler メソッド</span><span class="sxs-lookup"><span data-stu-id="24378-102">ICorDebug::SetManagedHandler Method</span></span>
<span data-ttu-id="24378-103">マネージ イベントのイベント ハンドラー オブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="24378-103">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24378-104">構文</span><span class="sxs-lookup"><span data-stu-id="24378-104">Syntax</span></span>  
  
```  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24378-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="24378-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="24378-106">[in]ポインター、 [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)イベント ハンドラー オブジェクトであるオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="24378-106">[in] A pointer to an [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24378-107">コメント</span><span class="sxs-lookup"><span data-stu-id="24378-107">Remarks</span></span>  
 <span data-ttu-id="24378-108">`SetManagedHandler`作成時に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="24378-108">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="24378-109">場合、`ICorDebugManagedCallback`実装には、デバッグ中、アプリケーションのデバッグ イベントを処理するための十分なインターフェイスが含まれていない`SetManagedHandler`HRESULT の E_NOINTERFACE を返します。</span><span class="sxs-lookup"><span data-stu-id="24378-109">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24378-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="24378-110">Requirements</span></span>  
 <span data-ttu-id="24378-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="24378-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24378-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24378-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24378-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24378-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24378-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24378-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24378-115">参照</span><span class="sxs-lookup"><span data-stu-id="24378-115">See Also</span></span>  
 [<span data-ttu-id="24378-116">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="24378-116">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

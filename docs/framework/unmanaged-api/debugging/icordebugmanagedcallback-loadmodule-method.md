---
title: ICorDebugManagedCallback::LoadModule メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbf538f066058b4f80d8cfd6cdf1a79683c79be9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="7be94-102">ICorDebugManagedCallback::LoadModule メソッド</span><span class="sxs-lookup"><span data-stu-id="7be94-102">ICorDebugManagedCallback::LoadModule Method</span></span>
<span data-ttu-id="7be94-103">共通言語ランタイム (CLR) モジュールが正常に読み込まれたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="7be94-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7be94-104">構文</span><span class="sxs-lookup"><span data-stu-id="7be94-104">Syntax</span></span>  
  
```  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7be94-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7be94-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="7be94-106">[in]ICorDebugAppDomain を表すオブジェクトをモジュールが読み込まれて、アプリケーション ドメインへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7be94-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="7be94-107">[in]CLR モジュールを表す ICorDebugModule オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7be94-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7be94-108">コメント</span><span class="sxs-lookup"><span data-stu-id="7be94-108">Remarks</span></span>  
 <span data-ttu-id="7be94-109">`LoadModule`コールバックは、モジュールのメタデータを調べて、・ イン タイム (JIT) コンパイラ フラグを設定または有効または無効にクラス、モジュールのコールバックを読み込み適切な時間を提供します。</span><span class="sxs-lookup"><span data-stu-id="7be94-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7be94-110">要件</span><span class="sxs-lookup"><span data-stu-id="7be94-110">Requirements</span></span>  
 <span data-ttu-id="7be94-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7be94-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7be94-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7be94-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7be94-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7be94-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7be94-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7be94-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7be94-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="7be94-115">See Also</span></span>  
 [<span data-ttu-id="7be94-116">UnloadModule メソッド</span><span class="sxs-lookup"><span data-stu-id="7be94-116">UnloadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)  
 [<span data-ttu-id="7be94-117">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7be94-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

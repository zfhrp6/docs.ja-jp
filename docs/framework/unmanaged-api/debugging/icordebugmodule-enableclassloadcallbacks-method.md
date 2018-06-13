---
title: ICorDebugModule::EnableClassLoadCallbacks メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableClassLoadCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 950790b246094c71900a5fb4da7d92be7d24aba2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421617"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="8fc43-102">ICorDebugModule::EnableClassLoadCallbacks メソッド</span><span class="sxs-lookup"><span data-stu-id="8fc43-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="8fc43-103">コントロールかどうか、 [icordebugmanagedcallback::loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)と[icordebugmanagedcallback::unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)このモジュールのコールバックが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8fc43-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fc43-104">構文</span><span class="sxs-lookup"><span data-stu-id="8fc43-104">Syntax</span></span>  
  
```  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8fc43-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8fc43-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="8fc43-106">[in]この値を設定`true`を共通言語ランタイム (CLR) を呼び出すを有効にする、`ICorDebugManagedCallback::LoadClass`と`ICorDebugManagedCallback::UnloadClass`関連するイベントが発生したときの方法です。</span><span class="sxs-lookup"><span data-stu-id="8fc43-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="8fc43-107">既定値は`false`非動的モジュール。</span><span class="sxs-lookup"><span data-stu-id="8fc43-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="8fc43-108">値は常に`true`動的モジュールを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="8fc43-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fc43-109">コメント</span><span class="sxs-lookup"><span data-stu-id="8fc43-109">Remarks</span></span>  
 <span data-ttu-id="8fc43-110">`ICorDebugManagedCallback::LoadClass`と`ICorDebugManagedCallback::UnloadClass`コールバックが動的モジュールが常に有効し、無効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="8fc43-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fc43-111">要件</span><span class="sxs-lookup"><span data-stu-id="8fc43-111">Requirements</span></span>  
 <span data-ttu-id="8fc43-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8fc43-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fc43-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8fc43-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8fc43-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8fc43-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fc43-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fc43-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc43-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="8fc43-116">See Also</span></span>  
    
 

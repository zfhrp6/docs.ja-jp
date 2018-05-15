---
title: ICorDebugManagedCallback::UnloadClass メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e70a1c66baff2d91554dea47e248a7003e30c498
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="44cfb-102">ICorDebugManagedCallback::UnloadClass メソッド</span><span class="sxs-lookup"><span data-stu-id="44cfb-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="44cfb-103">クラスがアンロードされることをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="44cfb-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44cfb-104">構文</span><span class="sxs-lookup"><span data-stu-id="44cfb-104">Syntax</span></span>  
  
```  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="44cfb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="44cfb-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="44cfb-106">[in]クラスを含む、アプリケーション ドメインを表す ICorDebugAppDomain オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="44cfb-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="44cfb-107">[in]クラスを表す ICorDebugClass オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="44cfb-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44cfb-108">コメント</span><span class="sxs-lookup"><span data-stu-id="44cfb-108">Remarks</span></span>  
 <span data-ttu-id="44cfb-109">クラスは、この呼び出しの後は参照できません。</span><span class="sxs-lookup"><span data-stu-id="44cfb-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44cfb-110">要件</span><span class="sxs-lookup"><span data-stu-id="44cfb-110">Requirements</span></span>  
 <span data-ttu-id="44cfb-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="44cfb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44cfb-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44cfb-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44cfb-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44cfb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44cfb-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44cfb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44cfb-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="44cfb-115">See Also</span></span>  
 [<span data-ttu-id="44cfb-116">LoadClass メソッド</span><span class="sxs-lookup"><span data-stu-id="44cfb-116">LoadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)  
 [<span data-ttu-id="44cfb-117">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="44cfb-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

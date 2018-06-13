---
title: ICorDebugManagedCallback::UnloadModule メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadModule
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadModule method [.NET Framework debugging]
- UnloadModule method [.NET Framework debugging]
ms.assetid: b12bfcd9-1e29-48bf-9a3d-44bfae5df5e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 02ca9ed57e62d2c066de2d7c1a1e4b57094dbc0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413356"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="a4cc9-102">ICorDebugManagedCallback::UnloadModule メソッド</span><span class="sxs-lookup"><span data-stu-id="a4cc9-102">ICorDebugManagedCallback::UnloadModule Method</span></span>
<span data-ttu-id="a4cc9-103">共通言語ランタイム モジュール (DLL) がアンロードされたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="a4cc9-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4cc9-104">構文</span><span class="sxs-lookup"><span data-stu-id="a4cc9-104">Syntax</span></span>  
  
```  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4cc9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a4cc9-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="a4cc9-106">[in]モジュールに含まれるアプリケーション ドメインを表す ICorDebugAppDomain オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a4cc9-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="a4cc9-107">[in]モジュールを表す ICorDebugModule オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a4cc9-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4cc9-108">コメント</span><span class="sxs-lookup"><span data-stu-id="a4cc9-108">Remarks</span></span>  
 <span data-ttu-id="a4cc9-109">モジュールは、この呼び出しの後は使用できません。</span><span class="sxs-lookup"><span data-stu-id="a4cc9-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4cc9-110">要件</span><span class="sxs-lookup"><span data-stu-id="a4cc9-110">Requirements</span></span>  
 <span data-ttu-id="a4cc9-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a4cc9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4cc9-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a4cc9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4cc9-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4cc9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4cc9-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4cc9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4cc9-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4cc9-115">See Also</span></span>  
 [<span data-ttu-id="a4cc9-116">LoadModule メソッド</span><span class="sxs-lookup"><span data-stu-id="a4cc9-116">LoadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)  
 [<span data-ttu-id="a4cc9-117">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a4cc9-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

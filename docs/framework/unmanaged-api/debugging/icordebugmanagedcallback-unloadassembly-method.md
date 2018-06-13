---
title: ICorDebugManagedCallback::UnloadAssembly メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a892012e872dcf44512adbe0d6890812d84ed899
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412595"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="acb7c-102">ICorDebugManagedCallback::UnloadAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="acb7c-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="acb7c-103">共通言語ランタイム アセンブリがアンロードされたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="acb7c-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acb7c-104">構文</span><span class="sxs-lookup"><span data-stu-id="acb7c-104">Syntax</span></span>  
  
```  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="acb7c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="acb7c-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="acb7c-106">[in]アセンブリに含まれるアプリケーション ドメインを表す ICorDebugAppDomain オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="acb7c-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="acb7c-107">[in]アセンブリを表す ICorDebugAssembly オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="acb7c-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acb7c-108">コメント</span><span class="sxs-lookup"><span data-stu-id="acb7c-108">Remarks</span></span>  
 <span data-ttu-id="acb7c-109">アセンブリは、このコールバック後は使用できません。</span><span class="sxs-lookup"><span data-stu-id="acb7c-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acb7c-110">要件</span><span class="sxs-lookup"><span data-stu-id="acb7c-110">Requirements</span></span>  
 <span data-ttu-id="acb7c-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="acb7c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acb7c-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="acb7c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="acb7c-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="acb7c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acb7c-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acb7c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acb7c-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="acb7c-115">See Also</span></span>  
 [<span data-ttu-id="acb7c-116">LoadAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="acb7c-116">LoadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)  
 [<span data-ttu-id="acb7c-117">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="acb7c-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

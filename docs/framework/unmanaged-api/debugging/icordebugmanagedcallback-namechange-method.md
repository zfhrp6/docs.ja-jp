---
title: ICorDebugManagedCallback::NameChange メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.NameChange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a7ef478fed697f4152a6348931ddf3b4b4b2885
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415010"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="6e64b-102">ICorDebugManagedCallback::NameChange メソッド</span><span class="sxs-lookup"><span data-stu-id="6e64b-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="6e64b-103">アプリケーション ドメインまたはスレッドのいずれかの名前が変更されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="6e64b-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e64b-104">構文</span><span class="sxs-lookup"><span data-stu-id="6e64b-104">Syntax</span></span>  
  
```  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e64b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e64b-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="6e64b-106">[in]または名前の変更があったか、アプリケーション ドメインを表す ICorDebugAppDomain オブジェクトへのポインターには、名前の変更のあるスレッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6e64b-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="6e64b-107">[in]名前の変更のあるスレッドを表す ICorDebugThread オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6e64b-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e64b-108">要件</span><span class="sxs-lookup"><span data-stu-id="6e64b-108">Requirements</span></span>  
 <span data-ttu-id="6e64b-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6e64b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e64b-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e64b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e64b-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e64b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e64b-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e64b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e64b-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="6e64b-113">See Also</span></span>  
 [<span data-ttu-id="6e64b-114">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6e64b-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

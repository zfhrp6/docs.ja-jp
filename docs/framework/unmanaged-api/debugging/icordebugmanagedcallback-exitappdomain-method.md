---
title: ICorDebugManagedCallback::ExitAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitAppDomain
helpviewer_keywords:
- ICorDebugManagedCallback::ExitAppDomain method [.NET Framework debugging]
- ExitAppDomain method [.NET Framework debugging]
ms.assetid: d815486e-b3bd-4fe8-ba28-02abdb4d67ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f909eddde182a73709be9ca5cafec6285db46b4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412855"
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="2ba43-102">ICorDebugManagedCallback::ExitAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="2ba43-102">ICorDebugManagedCallback::ExitAppDomain Method</span></span>
<span data-ttu-id="2ba43-103">アプリケーション ドメインが終了していることをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="2ba43-103">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ba43-104">構文</span><span class="sxs-lookup"><span data-stu-id="2ba43-104">Syntax</span></span>  
  
```  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ba43-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2ba43-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="2ba43-106">[in]特定のアプリケーション ドメインが含まれるプロセスを表す ICorDebugProcess オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2ba43-106">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="2ba43-107">[in]ICorDebugAppDomain を表すオブジェクトが終了してアプリケーション ドメインへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2ba43-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ba43-108">要件</span><span class="sxs-lookup"><span data-stu-id="2ba43-108">Requirements</span></span>  
 <span data-ttu-id="2ba43-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2ba43-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ba43-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ba43-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ba43-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ba43-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ba43-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ba43-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ba43-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ba43-113">See Also</span></span>  
 [<span data-ttu-id="2ba43-114">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2ba43-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

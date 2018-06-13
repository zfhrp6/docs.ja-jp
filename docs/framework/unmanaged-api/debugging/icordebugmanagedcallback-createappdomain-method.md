---
title: ICorDebugManagedCallback::CreateAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateAppDomain
helpviewer_keywords:
- CreateAppDomain method [.NET Framework debugging]
- ICorDebugManagedCallback::CreateAppDomain method [.NET Framework debugging]
ms.assetid: 48d410d7-6749-4125-a8fd-f9562c7088e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdac4b5b7a4a64a5fc939a7d35718ef276717fe7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415429"
---
# <a name="icordebugmanagedcallbackcreateappdomain-method"></a><span data-ttu-id="c08db-102">ICorDebugManagedCallback::CreateAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="c08db-102">ICorDebugManagedCallback::CreateAppDomain Method</span></span>
<span data-ttu-id="c08db-103">アプリケーション ドメインが作成されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="c08db-103">Notifies the debugger that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c08db-104">構文</span><span class="sxs-lookup"><span data-stu-id="c08db-104">Syntax</span></span>  
  
```  
HRESULT CreateAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c08db-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c08db-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="c08db-106">[in]アプリケーション ドメインが作成されたプロセスを表す ICorDebugProcess オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c08db-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the application domain was created.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="c08db-107">[in]ICorDebugAppDomain を表すオブジェクトが作成されたアプリケーション ドメインへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c08db-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has been created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c08db-108">要件</span><span class="sxs-lookup"><span data-stu-id="c08db-108">Requirements</span></span>  
 <span data-ttu-id="c08db-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c08db-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c08db-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c08db-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c08db-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c08db-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c08db-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c08db-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c08db-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c08db-113">See Also</span></span>  
 [<span data-ttu-id="c08db-114">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c08db-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

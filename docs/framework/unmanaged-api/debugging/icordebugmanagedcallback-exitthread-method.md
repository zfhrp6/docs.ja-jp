---
title: "ICorDebugManagedCallback::ExitThread メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.ExitThread
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::ExitThread
helpviewer_keywords:
- ExitThread method [.NET Framework debugging]
- ICorDebugManagedCallback::ExitThread method [.NET Framework debugging]
ms.assetid: 62db708b-6cf0-45c5-b897-4b5c75bd2505
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c39a8c92a8c0be8d0607663a833ac7307ca26d3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="7a776-102">ICorDebugManagedCallback::ExitThread メソッド</span><span class="sxs-lookup"><span data-stu-id="7a776-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="7a776-103">マネージ コードが実行しているスレッドが終了していることをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="7a776-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a776-104">構文</span><span class="sxs-lookup"><span data-stu-id="7a776-104">Syntax</span></span>  
  
```  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a776-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7a776-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="7a776-106">[in]マネージ スレッドを含む、アプリケーション ドメインを表す ICorDebugAppDomain オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7a776-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="7a776-107">[in]マネージ スレッドを表す ICorDebugThread オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7a776-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a776-108">コメント</span><span class="sxs-lookup"><span data-stu-id="7a776-108">Remarks</span></span>  
 <span data-ttu-id="7a776-109">1 回、`ExitThread`コールバックが発生した、スレッドはスレッドの列挙体では表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="7a776-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a776-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="7a776-110">Requirements</span></span>  
 <span data-ttu-id="7a776-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7a776-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a776-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a776-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a776-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a776-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a776-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a776-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a776-115">参照</span><span class="sxs-lookup"><span data-stu-id="7a776-115">See Also</span></span>  
 [<span data-ttu-id="7a776-116">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7a776-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

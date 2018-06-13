---
title: ICorDebugManagedCallback::ExitThread メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitThread
helpviewer_keywords:
- ExitThread method [.NET Framework debugging]
- ICorDebugManagedCallback::ExitThread method [.NET Framework debugging]
ms.assetid: 62db708b-6cf0-45c5-b897-4b5c75bd2505
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24b01fecc7947d14e36b4411a58d200667b0f2a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415543"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="8a5e6-102">ICorDebugManagedCallback::ExitThread メソッド</span><span class="sxs-lookup"><span data-stu-id="8a5e6-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="8a5e6-103">マネージ コードが実行しているスレッドが終了していることをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="8a5e6-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a5e6-104">構文</span><span class="sxs-lookup"><span data-stu-id="8a5e6-104">Syntax</span></span>  
  
```  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a5e6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a5e6-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="8a5e6-106">[in]マネージ スレッドを含む、アプリケーション ドメインを表す ICorDebugAppDomain オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8a5e6-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="8a5e6-107">[in]マネージ スレッドを表す ICorDebugThread オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8a5e6-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a5e6-108">コメント</span><span class="sxs-lookup"><span data-stu-id="8a5e6-108">Remarks</span></span>  
 <span data-ttu-id="8a5e6-109">1 回、`ExitThread`コールバックが発生した、スレッドはスレッドの列挙体では表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="8a5e6-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a5e6-110">要件</span><span class="sxs-lookup"><span data-stu-id="8a5e6-110">Requirements</span></span>  
 <span data-ttu-id="8a5e6-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8a5e6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a5e6-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a5e6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a5e6-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a5e6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a5e6-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a5e6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a5e6-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a5e6-115">See Also</span></span>  
 [<span data-ttu-id="8a5e6-116">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8a5e6-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

---
title: ICorDebugManagedCallback::CreateThread メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateThread method
helpviewer_keywords:
- ICorDebugManagedCallback::CreateThread method [.NET Framework debugging]
- CreateThread method [.NET Framework debugging]
ms.assetid: 6b961728-21c4-4e8d-ae81-197458be62f4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9721d88c8ce138b19c98f113d9eb034c5e1c55dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417691"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="1fb34-102">ICorDebugManagedCallback::CreateThread メソッド</span><span class="sxs-lookup"><span data-stu-id="1fb34-102">ICorDebugManagedCallback::CreateThread Method</span></span>
<span data-ttu-id="1fb34-103">スレッドがマネージ コードの実行を開始したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="1fb34-103">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fb34-104">構文</span><span class="sxs-lookup"><span data-stu-id="1fb34-104">Syntax</span></span>  
  
```  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1fb34-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1fb34-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="1fb34-106">[in]ICorDebugAppDomain を表すオブジェクトをスレッドを含むアプリケーション ドメインへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1fb34-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="1fb34-107">[in]スレッドを表す ICorDebugThread オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1fb34-107">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1fb34-108">コメント</span><span class="sxs-lookup"><span data-stu-id="1fb34-108">Remarks</span></span>  
 <span data-ttu-id="1fb34-109">スレッドは、実行されるマネージ コードの最初の命令に配置されます。</span><span class="sxs-lookup"><span data-stu-id="1fb34-109">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fb34-110">要件</span><span class="sxs-lookup"><span data-stu-id="1fb34-110">Requirements</span></span>  
 <span data-ttu-id="1fb34-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1fb34-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fb34-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1fb34-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1fb34-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1fb34-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1fb34-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fb34-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fb34-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="1fb34-115">See Also</span></span>  
 [<span data-ttu-id="1fb34-116">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1fb34-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

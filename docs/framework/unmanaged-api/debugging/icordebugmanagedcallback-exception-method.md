---
title: ICorDebugManagedCallback::Exception メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf6152c643395fe52a43424cab33f527d577b5bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413890"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="3f85a-102">ICorDebugManagedCallback::Exception メソッド</span><span class="sxs-lookup"><span data-stu-id="3f85a-102">ICorDebugManagedCallback::Exception Method</span></span>
<span data-ttu-id="3f85a-103">マネージ コードから例外がスローされたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="3f85a-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f85a-104">構文</span><span class="sxs-lookup"><span data-stu-id="3f85a-104">Syntax</span></span>  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f85a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3f85a-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="3f85a-106">[in]例外がスローされたアプリケーション ドメインを表す ICorDebugAppDomain オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3f85a-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="3f85a-107">[in]例外がスローされたスレッドを表す ICorDebugThread オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3f85a-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="3f85a-108">[in]この値が場合`false`例外がまだそれ以外のアプリケーションによって処理されると、例外が処理されないと、プロセスが終了します。</span><span class="sxs-lookup"><span data-stu-id="3f85a-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f85a-109">コメント</span><span class="sxs-lookup"><span data-stu-id="3f85a-109">Remarks</span></span>  
 <span data-ttu-id="3f85a-110">特定の例外は、スレッド オブジェクトから取得できます。</span><span class="sxs-lookup"><span data-stu-id="3f85a-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f85a-111">要件</span><span class="sxs-lookup"><span data-stu-id="3f85a-111">Requirements</span></span>  
 <span data-ttu-id="3f85a-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3f85a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f85a-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3f85a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f85a-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f85a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f85a-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f85a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f85a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f85a-116">See Also</span></span>  
 [<span data-ttu-id="3f85a-117">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3f85a-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

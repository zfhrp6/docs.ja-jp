---
title: "ICorDebugManagedCallback2::ExceptionUnwind メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.ExceptionUnwind
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45b9f5838e4bc98e3f269a2cebd575abfe998a2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="7bf6b-102">ICorDebugManagedCallback2::ExceptionUnwind メソッド</span><span class="sxs-lookup"><span data-stu-id="7bf6b-102">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>
<span data-ttu-id="7bf6b-103">例外のアンワインド処理中に状態の通知を提供します。</span><span class="sxs-lookup"><span data-stu-id="7bf6b-103">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bf6b-104">構文</span><span class="sxs-lookup"><span data-stu-id="7bf6b-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7bf6b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7bf6b-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="7bf6b-106">[in]ICorDebugAppDomain を表すオブジェクトを含む例外がスローされたスレッドのアプリケーション ドメインへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7bf6b-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="7bf6b-107">[in]例外がスローされたスレッドを表す ICorDebugThread オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7bf6b-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="7bf6b-108">[in]アンワインド フェーズ中にコールバックによって通知されるイベントを指定する CorDebugExceptionUnwindCallbackType 列挙型の値です。</span><span class="sxs-lookup"><span data-stu-id="7bf6b-108">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="7bf6b-109">[in]値、 [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)例外に関する追加情報を指定する列挙です。</span><span class="sxs-lookup"><span data-stu-id="7bf6b-109">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7bf6b-110">コメント</span><span class="sxs-lookup"><span data-stu-id="7bf6b-110">Remarks</span></span>  
 <span data-ttu-id="7bf6b-111">`ExceptionUnwind`例外処理プロセスのアンワインド フェーズ中にさまざまな時点で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="7bf6b-111">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="7bf6b-112">`ExceptionUnwind`1 つの例外のアンワインド中に複数回呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="7bf6b-112">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="7bf6b-113">場合`dwEventType`= DEBUG_EXCEPTION_INTERCEPTED、する前にシーケンス ポイントで、スレッドのリーフ フレームで、命令ポインターになります (これは、前にいくつかの手順をなる可能性があります) に、例外を引き起こした命令します。</span><span class="sxs-lookup"><span data-stu-id="7bf6b-113">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bf6b-114">要件</span><span class="sxs-lookup"><span data-stu-id="7bf6b-114">Requirements</span></span>  
 <span data-ttu-id="7bf6b-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7bf6b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bf6b-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7bf6b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7bf6b-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7bf6b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bf6b-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bf6b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bf6b-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="7bf6b-119">See Also</span></span>  
 [<span data-ttu-id="7bf6b-120">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7bf6b-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="7bf6b-121">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7bf6b-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

---
title: "ICorDebugManagedCallback3::CustomNotification メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback3.CustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3::CustomNotification
helpviewer_keywords:
- ICorDebugManagedCallback3::CustomNotification method [.NET Framework debugging]
- CustomNotification method [.NET Framework debugging]
ms.assetid: 5e5422ac-afa1-403d-a894-2d7348673e38
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9c42443b0d1e355d4233909357c341763298160e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="a913f-102">ICorDebugManagedCallback3::CustomNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="a913f-102">ICorDebugManagedCallback3::CustomNotification Method</span></span>
<span data-ttu-id="a913f-103">カスタムのデバッガー通知が発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="a913f-103">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a913f-104">構文</span><span class="sxs-lookup"><span data-stu-id="a913f-104">Syntax</span></span>  
  
```  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a913f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a913f-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="a913f-106">[in]通知を発生させたスレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a913f-106">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="a913f-107">[in]通知を発生させた、スレッドがあるアプリケーション ドメインへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a913f-107">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a913f-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="a913f-108">Return Value</span></span>  
 <span data-ttu-id="a913f-109">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="a913f-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a913f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a913f-110">HRESULT</span></span>|<span data-ttu-id="a913f-111">説明</span><span class="sxs-lookup"><span data-stu-id="a913f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a913f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a913f-112">S_OK</span></span>|<span data-ttu-id="a913f-113">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="a913f-113">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="a913f-114">例外</span><span class="sxs-lookup"><span data-stu-id="a913f-114">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a913f-115">コメント</span><span class="sxs-lookup"><span data-stu-id="a913f-115">Remarks</span></span>  
 <span data-ttu-id="a913f-116">後続の呼び出し、 [icordebugthread 4::getcurrentcustomdebuggernotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md)メソッドに渡されたスレッド オブジェクトを取得、<xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a913f-116">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a913f-117">スレッド オブジェクトの種類あります以前有効になっているを呼び出して、 [icordebugprocess 3::setenablecustomnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a913f-117">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="a913f-118">デバッガーは、スレッド オブジェクトのフィールドを型固有のパラメーターを読み取ることができ、フィールドに応答を格納することができます。</span><span class="sxs-lookup"><span data-stu-id="a913f-118">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="a913f-119">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)インターフェイスは、通知またはその内容の種類のポリシーはありませんし、通知のセマンティクスは、デバッガー、アプリケーション、および .NET Framework 間のコントラクトでは厳密にします。</span><span class="sxs-lookup"><span data-stu-id="a913f-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a913f-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="a913f-120">Requirements</span></span>  
 <span data-ttu-id="a913f-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a913f-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a913f-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a913f-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a913f-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a913f-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a913f-124">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a913f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a913f-125">参照</span><span class="sxs-lookup"><span data-stu-id="a913f-125">See Also</span></span>  
 [<span data-ttu-id="a913f-126">ICorDebugManagedCallback3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a913f-126">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 [<span data-ttu-id="a913f-127">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a913f-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a913f-128">デバッグ</span><span class="sxs-lookup"><span data-stu-id="a913f-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

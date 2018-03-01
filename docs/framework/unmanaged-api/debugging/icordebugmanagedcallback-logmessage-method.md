---
title: "ICorDebugManagedCallback::LogMessage メソッド"
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
- ICorDebugManagedCallback.LogMessage
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogMessage
helpviewer_keywords:
- ICorDebugManagedCallback::LogMessage method [.NET Framework debugging]
- LogMessage method [.NET Framework debugging]
ms.assetid: d218554a-bf42-4d88-833d-ede30de67a53
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d62204e8fb2e1fabae4183bbcf7b4d42b832d2b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="01bfb-102">ICorDebugManagedCallback::LogMessage メソッド</span><span class="sxs-lookup"><span data-stu-id="01bfb-102">ICorDebugManagedCallback::LogMessage Method</span></span>
<span data-ttu-id="01bfb-103">共通言語ランタイム (CLR) によって管理されるスレッドがメソッドを呼び出すことをデバッガーに通知、<xref:System.Diagnostics.EventLog>クラス イベント ログに記録します。</span><span class="sxs-lookup"><span data-stu-id="01bfb-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01bfb-104">構文</span><span class="sxs-lookup"><span data-stu-id="01bfb-104">Syntax</span></span>  
  
```  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="01bfb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="01bfb-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="01bfb-106">[in]イベントを記録したマネージ スレッドを含む、アプリケーション ドメインを表す ICorDebugAppDomain オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="01bfb-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="01bfb-107">[in]マネージ スレッドを表す ICorDebugThread オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="01bfb-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="01bfb-108">[in]値、 [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)をイベント ログに書き込まれた説明メッセージの重大度レベルを示す列挙体です。</span><span class="sxs-lookup"><span data-stu-id="01bfb-108">[in] A value of the [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="01bfb-109">[in]トレース スイッチの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="01bfb-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="01bfb-110">[in]イベント ログに書き込まれたメッセージへのポインター。</span><span class="sxs-lookup"><span data-stu-id="01bfb-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01bfb-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="01bfb-111">Requirements</span></span>  
 <span data-ttu-id="01bfb-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="01bfb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01bfb-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01bfb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01bfb-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01bfb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01bfb-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01bfb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01bfb-116">参照</span><span class="sxs-lookup"><span data-stu-id="01bfb-116">See Also</span></span>  
 [<span data-ttu-id="01bfb-117">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="01bfb-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

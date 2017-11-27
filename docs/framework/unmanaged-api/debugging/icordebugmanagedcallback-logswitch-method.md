---
title: "ICorDebugManagedCallback::LogSwitch メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.LogSwitch
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::LogSwitch
helpviewer_keywords:
- LogSwitch method [.NET Framework debugging]
- ICorDebugManagedCallback::LogSwitch method [.NET Framework debugging]
ms.assetid: 0ac59d27-783f-4a87-b7a8-baa3ccc54582
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9480b3123abceb6a108e2e00c7304829188cd162
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="31e8b-102">ICorDebugManagedCallback::LogSwitch メソッド</span><span class="sxs-lookup"><span data-stu-id="31e8b-102">ICorDebugManagedCallback::LogSwitch Method</span></span>
<span data-ttu-id="31e8b-103">共通言語ランタイム (CLR) によって管理されるスレッドがメソッドを呼び出すことをデバッガーに通知、<xref:System.Diagnostics.Switch>クラスを作成、変更、またはデバッグとトレース スイッチを削除します。</span><span class="sxs-lookup"><span data-stu-id="31e8b-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31e8b-104">構文</span><span class="sxs-lookup"><span data-stu-id="31e8b-104">Syntax</span></span>  
  
```  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31e8b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="31e8b-105">Parameters</span></span>  
 `PAppDomain`  
 <span data-ttu-id="31e8b-106">[in]ICorDebugAppDomain を表すオブジェクトを作成、変更、またはデバッグ/トレース スイッチを削除するマネージ スレッドを含む、アプリケーション ドメインへのポインター。</span><span class="sxs-lookup"><span data-stu-id="31e8b-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="31e8b-107">[in]マネージ スレッドを表す ICorDebugThread オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="31e8b-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="31e8b-108">[in]イベント ログに書き込まれた説明メッセージの重大度レベルを示す値です。</span><span class="sxs-lookup"><span data-stu-id="31e8b-108">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="31e8b-109">[in]値、 [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)デバッグとトレース スイッチの操作を示す列挙を実行します。</span><span class="sxs-lookup"><span data-stu-id="31e8b-109">[in] A value of the [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="31e8b-110">[in]デバッグとトレース スイッチの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="31e8b-110">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="31e8b-111">[in]デバッグとトレース スイッチの親の名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="31e8b-111">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31e8b-112">要件</span><span class="sxs-lookup"><span data-stu-id="31e8b-112">Requirements</span></span>  
 <span data-ttu-id="31e8b-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="31e8b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31e8b-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="31e8b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31e8b-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31e8b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31e8b-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31e8b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31e8b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="31e8b-117">See Also</span></span>  
 [<span data-ttu-id="31e8b-118">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="31e8b-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

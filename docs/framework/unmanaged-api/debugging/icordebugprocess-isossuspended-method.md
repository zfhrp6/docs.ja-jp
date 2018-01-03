---
title: "ICorDebugProcess::IsOSSuspended メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.IsOSSuspended
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 97c394e3084007227cf157c62a12df3f5cfac8e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="b4c72-102">ICorDebugProcess::IsOSSuspended メソッド</span><span class="sxs-lookup"><span data-stu-id="b4c72-102">ICorDebugProcess::IsOSSuspended Method</span></span>
<span data-ttu-id="b4c72-103">デバッガーがこのプロセスを停止したため、指定したスレッドが中断されたかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="b4c72-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4c72-104">構文</span><span class="sxs-lookup"><span data-stu-id="b4c72-104">Syntax</span></span>  
  
```  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4c72-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b4c72-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="b4c72-106">[in]対象のスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="b4c72-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="b4c72-107">[out]ブール値へのポインター`true`中断です。 それ以外の場合、指定されたスレッドがあった場合 *`pbSuspended`は`false`します。</span><span class="sxs-lookup"><span data-stu-id="b4c72-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise *`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4c72-108">コメント</span><span class="sxs-lookup"><span data-stu-id="b4c72-108">Remarks</span></span>  
 <span data-ttu-id="b4c72-109">デバッガーがこのプロセスを停止したため、指定されたスレッドが中断されたときに、指定されたスレッドの Win32 の中断カウントが 1 ずつインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="b4c72-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="b4c72-110">デバッガー ユーザー インターフェイス (UI) がオペレーティング システムを表示する場合に、アカウントには、この情報を取得することがあります (OS) がユーザーに、スレッドの数を中断します。</span><span class="sxs-lookup"><span data-stu-id="b4c72-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="b4c72-111">`IsOSSuspended`メソッドは、アンマネージ デバッグのコンテキストでのみ意味します。</span><span class="sxs-lookup"><span data-stu-id="b4c72-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="b4c72-112">マネージ デバッグ中には、スレッドは、協調的な中断ではなく OS 中断がします。</span><span class="sxs-lookup"><span data-stu-id="b4c72-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4c72-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="b4c72-113">Requirements</span></span>  
 <span data-ttu-id="b4c72-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b4c72-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4c72-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4c72-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4c72-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4c72-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4c72-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4c72-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

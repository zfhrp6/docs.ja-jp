---
title: "ICorDebugThread2::GetTaskID メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2.GetTaskID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b94478a0dfb8cc4d90dea611620238024634799
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="061a1-102">ICorDebugThread2::GetTaskID メソッド</span><span class="sxs-lookup"><span data-stu-id="061a1-102">ICorDebugThread2::GetTaskID Method</span></span>
<span data-ttu-id="061a1-103">このスレッドで実行中のタスクの識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="061a1-103">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="061a1-104">構文</span><span class="sxs-lookup"><span data-stu-id="061a1-104">Syntax</span></span>  
  
```  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="061a1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="061a1-105">Parameters</span></span>  
 `pTaskId`  
 <span data-ttu-id="061a1-106">[out]この ICorDebugThread2 オブジェクトによって表される、スレッドで実行中のタスクの識別子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="061a1-106">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="061a1-107">コメント</span><span class="sxs-lookup"><span data-stu-id="061a1-107">Remarks</span></span>  
 <span data-ttu-id="061a1-108">タスクは、スレッドが接続に関連付けられている場合のスレッドでは実行のみです。</span><span class="sxs-lookup"><span data-stu-id="061a1-108">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="061a1-109">`GetTaskID`0 が返されます`pTaskId`スレッドは、接続に関連付けられていない場合。</span><span class="sxs-lookup"><span data-stu-id="061a1-109">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="061a1-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="061a1-110">Requirements</span></span>  
 <span data-ttu-id="061a1-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="061a1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="061a1-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="061a1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="061a1-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="061a1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="061a1-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="061a1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

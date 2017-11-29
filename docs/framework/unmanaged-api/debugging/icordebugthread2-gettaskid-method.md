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
ms.openlocfilehash: 0e2d5a845b7047949618bed4176e6d24fee43c14
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="a77d8-102">ICorDebugThread2::GetTaskID メソッド</span><span class="sxs-lookup"><span data-stu-id="a77d8-102">ICorDebugThread2::GetTaskID Method</span></span>
<span data-ttu-id="a77d8-103">このスレッドで実行中のタスクの識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="a77d8-103">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a77d8-104">構文</span><span class="sxs-lookup"><span data-stu-id="a77d8-104">Syntax</span></span>  
  
```  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a77d8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a77d8-105">Parameters</span></span>  
 `pTaskId`  
 <span data-ttu-id="a77d8-106">[out]この ICorDebugThread2 オブジェクトによって表される、スレッドで実行中のタスクの識別子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a77d8-106">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a77d8-107">コメント</span><span class="sxs-lookup"><span data-stu-id="a77d8-107">Remarks</span></span>  
 <span data-ttu-id="a77d8-108">タスクは、スレッドが接続に関連付けられている場合のスレッドでは実行のみです。</span><span class="sxs-lookup"><span data-stu-id="a77d8-108">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="a77d8-109">`GetTaskID`0 が返されます`pTaskId`スレッドは、接続に関連付けられていない場合。</span><span class="sxs-lookup"><span data-stu-id="a77d8-109">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a77d8-110">要件</span><span class="sxs-lookup"><span data-stu-id="a77d8-110">Requirements</span></span>  
 <span data-ttu-id="a77d8-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a77d8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a77d8-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a77d8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a77d8-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a77d8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a77d8-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a77d8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

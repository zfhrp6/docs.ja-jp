---
title: "ICorDebugThread::GetID メソッド"
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
- ICorDebugThread.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetID
helpviewer_keywords:
- ICorDebugThread::GetID method [.NET Framework debugging]
- GetID method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: f1de4584-92df-42f3-9da4-fca03a1c6821
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cab889761c204204e7eda46fde0df42f31b89fbc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgetid-method"></a><span data-ttu-id="82081-102">ICorDebugThread::GetID メソッド</span><span class="sxs-lookup"><span data-stu-id="82081-102">ICorDebugThread::GetID Method</span></span>
<span data-ttu-id="82081-103">この ICorDebugThread のアクティブな部分の現在のオペレーティング システムの識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="82081-103">Gets the current operating system identifier of the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82081-104">構文</span><span class="sxs-lookup"><span data-stu-id="82081-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82081-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="82081-105">Parameters</span></span>  
 `pdwThreadId`  
 <span data-ttu-id="82081-106">[out]スレッドの識別子。</span><span class="sxs-lookup"><span data-stu-id="82081-106">[out] The identifier of the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82081-107">コメント</span><span class="sxs-lookup"><span data-stu-id="82081-107">Remarks</span></span>  
 <span data-ttu-id="82081-108">オペレーティング システム識別子は、プロセスの実行中に変更できます可能性があると、別のスレッドのさまざまな部分の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="82081-108">The operating system identifier can potentially change during execution of a process, and can be a different value for different parts of the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82081-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="82081-109">Requirements</span></span>  
 <span data-ttu-id="82081-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="82081-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82081-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82081-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82081-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82081-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82081-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82081-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

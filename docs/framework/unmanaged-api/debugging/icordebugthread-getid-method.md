---
title: ICorDebugThread::GetID メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52962ea7d2cf3dd1822b1a36cc6cfcb56bc427f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417194"
---
# <a name="icordebugthreadgetid-method"></a><span data-ttu-id="27472-102">ICorDebugThread::GetID メソッド</span><span class="sxs-lookup"><span data-stu-id="27472-102">ICorDebugThread::GetID Method</span></span>
<span data-ttu-id="27472-103">この ICorDebugThread のアクティブな部分の現在のオペレーティング システムの識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="27472-103">Gets the current operating system identifier of the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27472-104">構文</span><span class="sxs-lookup"><span data-stu-id="27472-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27472-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="27472-105">Parameters</span></span>  
 `pdwThreadId`  
 <span data-ttu-id="27472-106">[out]スレッドの識別子。</span><span class="sxs-lookup"><span data-stu-id="27472-106">[out] The identifier of the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27472-107">コメント</span><span class="sxs-lookup"><span data-stu-id="27472-107">Remarks</span></span>  
 <span data-ttu-id="27472-108">オペレーティング システム識別子は、プロセスの実行中に変更できます可能性があると、別のスレッドのさまざまな部分の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="27472-108">The operating system identifier can potentially change during execution of a process, and can be a different value for different parts of the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27472-109">要件</span><span class="sxs-lookup"><span data-stu-id="27472-109">Requirements</span></span>  
 <span data-ttu-id="27472-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="27472-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27472-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27472-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27472-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27472-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27472-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27472-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

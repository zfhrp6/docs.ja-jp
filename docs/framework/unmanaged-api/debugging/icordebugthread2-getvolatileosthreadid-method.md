---
title: "ICorDebugThread2::GetVolatileOSThreadID メソッド"
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
- ICorDebugThread2.GetVolatileOSThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetVolatileOSThreadID
helpviewer_keywords:
- GetVolatileOSThreadID method [.NET Framework debugging]
- ICorDebugThread2::GetVolatileOSThreadID method [.NET Framework debugging]
ms.assetid: f0922545-c2cf-40c8-9ef6-ca033563e682
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd15407e0e2866cf7b177c936b172d06ba76d83b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread2getvolatileosthreadid-method"></a><span data-ttu-id="4b412-102">ICorDebugThread2::GetVolatileOSThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="4b412-102">ICorDebugThread2::GetVolatileOSThreadID Method</span></span>
<span data-ttu-id="4b412-103">この ICorDebugThread2 のオペレーティング システムのスレッド識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="4b412-103">Gets the operating system thread identifier for this ICorDebugThread2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b412-104">構文</span><span class="sxs-lookup"><span data-stu-id="4b412-104">Syntax</span></span>  
  
```  
HRESULT GetVolatileOSThreadID (  
    [out] DWORD    *pdwTid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b412-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4b412-105">Parameters</span></span>  
 `pdwTid`  
 <span data-ttu-id="4b412-106">[out]このスレッドのオペレーティング システム スレッドの識別子。</span><span class="sxs-lookup"><span data-stu-id="4b412-106">[out] The operating system thread identifier for this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b412-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="4b412-107">Requirements</span></span>  
 <span data-ttu-id="4b412-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4b412-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b412-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b412-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b412-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b412-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b412-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b412-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

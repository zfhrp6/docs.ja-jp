---
title: ICorDebugThread2::GetVolatileOSThreadID メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e6798c2574167ec1a013429b380d8fa6c878dad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416564"
---
# <a name="icordebugthread2getvolatileosthreadid-method"></a><span data-ttu-id="02c80-102">ICorDebugThread2::GetVolatileOSThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="02c80-102">ICorDebugThread2::GetVolatileOSThreadID Method</span></span>
<span data-ttu-id="02c80-103">この ICorDebugThread2 のオペレーティング システムのスレッド識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="02c80-103">Gets the operating system thread identifier for this ICorDebugThread2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02c80-104">構文</span><span class="sxs-lookup"><span data-stu-id="02c80-104">Syntax</span></span>  
  
```  
HRESULT GetVolatileOSThreadID (  
    [out] DWORD    *pdwTid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="02c80-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="02c80-105">Parameters</span></span>  
 `pdwTid`  
 <span data-ttu-id="02c80-106">[out]このスレッドのオペレーティング システム スレッドの識別子。</span><span class="sxs-lookup"><span data-stu-id="02c80-106">[out] The operating system thread identifier for this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02c80-107">要件</span><span class="sxs-lookup"><span data-stu-id="02c80-107">Requirements</span></span>  
 <span data-ttu-id="02c80-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="02c80-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02c80-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02c80-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02c80-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02c80-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02c80-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02c80-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

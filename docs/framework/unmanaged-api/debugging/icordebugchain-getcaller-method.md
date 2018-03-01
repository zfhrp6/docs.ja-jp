---
title: "ICorDebugChain::GetCaller メソッド"
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
- ICorDebugChain.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 17c55358a1d502ce5946617556222282ac4c4fca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="5e7cd-102">ICorDebugChain::GetCaller メソッド</span><span class="sxs-lookup"><span data-stu-id="5e7cd-102">ICorDebugChain::GetCaller Method</span></span>
<span data-ttu-id="5e7cd-103">このチェーンと呼ばれる、チェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="5e7cd-103">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e7cd-104">構文</span><span class="sxs-lookup"><span data-stu-id="5e7cd-104">Syntax</span></span>  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e7cd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5e7cd-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="5e7cd-106">[out]呼び出しチェーンを表す ICorDebugChain オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5e7cd-106">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="5e7cd-107">このチェーンが自発的に呼び出された場合 (このチェーンまたはデバッガーに呼び出し履歴が初期化される場合、ケースになります) として、`ppChain`は null になります。</span><span class="sxs-lookup"><span data-stu-id="5e7cd-107">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e7cd-108">コメント</span><span class="sxs-lookup"><span data-stu-id="5e7cd-108">Remarks</span></span>  
 <span data-ttu-id="5e7cd-109">呼び出しは、スレッド間でマーシャ リングされた場合、別のスレッドで呼び出しチェーンがあります。</span><span class="sxs-lookup"><span data-stu-id="5e7cd-109">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e7cd-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="5e7cd-110">Requirements</span></span>  
 <span data-ttu-id="5e7cd-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5e7cd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e7cd-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e7cd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e7cd-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e7cd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e7cd-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e7cd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

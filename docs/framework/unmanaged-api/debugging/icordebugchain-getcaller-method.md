---
title: ICorDebugChain::GetCaller メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a0b5d702e9718ce6ac537beae67fc190b152b9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405144"
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="3065d-102">ICorDebugChain::GetCaller メソッド</span><span class="sxs-lookup"><span data-stu-id="3065d-102">ICorDebugChain::GetCaller Method</span></span>
<span data-ttu-id="3065d-103">このチェーンと呼ばれる、チェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="3065d-103">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3065d-104">構文</span><span class="sxs-lookup"><span data-stu-id="3065d-104">Syntax</span></span>  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3065d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3065d-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="3065d-106">[out]呼び出しチェーンを表す ICorDebugChain オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3065d-106">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="3065d-107">このチェーンが自発的に呼び出された場合 (このチェーンまたはデバッガーに呼び出し履歴が初期化される場合、ケースになります) として、`ppChain`は null になります。</span><span class="sxs-lookup"><span data-stu-id="3065d-107">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3065d-108">コメント</span><span class="sxs-lookup"><span data-stu-id="3065d-108">Remarks</span></span>  
 <span data-ttu-id="3065d-109">呼び出しは、スレッド間でマーシャ リングされた場合、別のスレッドで呼び出しチェーンがあります。</span><span class="sxs-lookup"><span data-stu-id="3065d-109">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3065d-110">要件</span><span class="sxs-lookup"><span data-stu-id="3065d-110">Requirements</span></span>  
 <span data-ttu-id="3065d-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3065d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3065d-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3065d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3065d-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3065d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3065d-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3065d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

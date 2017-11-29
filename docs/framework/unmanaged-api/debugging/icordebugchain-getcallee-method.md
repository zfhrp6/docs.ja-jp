---
title: "ICorDebugChain::GetCallee メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetCallee
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ed2bf8d8e91799fd0b01012d5d6e212d26a526be
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="ba8f5-102">ICorDebugChain::GetCallee メソッド</span><span class="sxs-lookup"><span data-stu-id="ba8f5-102">ICorDebugChain::GetCallee Method</span></span>
<span data-ttu-id="ba8f5-103">このチェーンによって呼び出されたチェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="ba8f5-103">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba8f5-104">構文</span><span class="sxs-lookup"><span data-stu-id="ba8f5-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba8f5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ba8f5-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="ba8f5-106">[out]呼び出されたチェーンを表す ICorDebugChain オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ba8f5-106">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="ba8f5-107">場合 (つまり、このチェーンを返すと呼ばれるチェーンが待機していない) 場合、このチェーンが現在実行中、`ppChain`は null になります。</span><span class="sxs-lookup"><span data-stu-id="ba8f5-107">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba8f5-108">コメント</span><span class="sxs-lookup"><span data-stu-id="ba8f5-108">Remarks</span></span>  
 <span data-ttu-id="ba8f5-109">このチェーンと呼ばれるチェーンの実行を再開する前に戻るには待機します。</span><span class="sxs-lookup"><span data-stu-id="ba8f5-109">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="ba8f5-110">スレッド間のマーシャ リングされた呼び出しの場合、別のスレッドで呼び出されたチェーンがあります。</span><span class="sxs-lookup"><span data-stu-id="ba8f5-110">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba8f5-111">要件</span><span class="sxs-lookup"><span data-stu-id="ba8f5-111">Requirements</span></span>  
 <span data-ttu-id="ba8f5-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ba8f5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba8f5-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba8f5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba8f5-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba8f5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba8f5-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba8f5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

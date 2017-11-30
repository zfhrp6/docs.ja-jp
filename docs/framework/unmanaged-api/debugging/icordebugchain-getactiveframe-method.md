---
title: "ICorDebugChain::GetActiveFrame メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetActiveFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b5de327c1579d05f6ae4a440fc76a3fb9ee99b13
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="16f7b-102">ICorDebugChain::GetActiveFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="16f7b-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="16f7b-103">アクティブなを取得 (つまり、最新) のフレーム チェーンをします。</span><span class="sxs-lookup"><span data-stu-id="16f7b-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16f7b-104">構文</span><span class="sxs-lookup"><span data-stu-id="16f7b-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16f7b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="16f7b-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="16f7b-106">[out]アクティブなを表す ICorDebugFrame オブジェクトのアドレスへのポインター (つまり、最新) のフレーム チェーンをします。</span><span class="sxs-lookup"><span data-stu-id="16f7b-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16f7b-107">コメント</span><span class="sxs-lookup"><span data-stu-id="16f7b-107">Remarks</span></span>  
 <span data-ttu-id="16f7b-108">マネージ スタック フレームが使用できない場合`ppFrame`設定を null にします。</span><span class="sxs-lookup"><span data-stu-id="16f7b-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="16f7b-109">アクティブなフレームが使用できない場合、呼び出しが成功し、`ppFrame`は null になります。</span><span class="sxs-lookup"><span data-stu-id="16f7b-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="16f7b-110">アクティブなフレームはチェーン CHAIN_ENTER_UNMANAGED、により開始されるのと CHAIN_CLASS_INIT により開始されるいくつかのチェーンを利用できません。</span><span class="sxs-lookup"><span data-stu-id="16f7b-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="16f7b-111">CorDebugChainReason 列挙型を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16f7b-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16f7b-112">要件</span><span class="sxs-lookup"><span data-stu-id="16f7b-112">Requirements</span></span>  
 <span data-ttu-id="16f7b-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="16f7b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16f7b-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16f7b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16f7b-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16f7b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16f7b-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16f7b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
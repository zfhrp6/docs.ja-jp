---
title: ICorDebugChain::GetActiveFrame メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a104d4d3cc74a6c1cb343818c9b0b3e8978b97df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402800"
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="cac0f-102">ICorDebugChain::GetActiveFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="cac0f-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="cac0f-103">アクティブなを取得 (つまり、最新) のフレーム チェーンをします。</span><span class="sxs-lookup"><span data-stu-id="cac0f-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cac0f-104">構文</span><span class="sxs-lookup"><span data-stu-id="cac0f-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cac0f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cac0f-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="cac0f-106">[out]アクティブなを表す ICorDebugFrame オブジェクトのアドレスへのポインター (つまり、最新) のフレーム チェーンをします。</span><span class="sxs-lookup"><span data-stu-id="cac0f-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cac0f-107">コメント</span><span class="sxs-lookup"><span data-stu-id="cac0f-107">Remarks</span></span>  
 <span data-ttu-id="cac0f-108">マネージ スタック フレームが使用できない場合`ppFrame`設定を null にします。</span><span class="sxs-lookup"><span data-stu-id="cac0f-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="cac0f-109">アクティブなフレームが使用できない場合、呼び出しが成功し、`ppFrame`は null になります。</span><span class="sxs-lookup"><span data-stu-id="cac0f-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="cac0f-110">アクティブなフレームはチェーン CHAIN_ENTER_UNMANAGED、により開始されるのと CHAIN_CLASS_INIT により開始されるいくつかのチェーンを利用できません。</span><span class="sxs-lookup"><span data-stu-id="cac0f-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="cac0f-111">CorDebugChainReason 列挙型を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cac0f-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cac0f-112">要件</span><span class="sxs-lookup"><span data-stu-id="cac0f-112">Requirements</span></span>  
 <span data-ttu-id="cac0f-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cac0f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cac0f-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cac0f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cac0f-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cac0f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cac0f-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cac0f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

---
title: ICorDebugChain::GetReason メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- GetReason
helpviewer_keywords:
- GetReason method [.NET Framework debugging]
- ICorDebugChain::GetReason method [.NET Framework debugging]
ms.assetid: 9f9f62b9-113a-4a98-8f9b-b593cef27b03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d02a68e80e34be906e9fe09f3457a0f2214c6f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405068"
---
# <a name="icordebugchaingetreason-method"></a><span data-ttu-id="64ae5-102">ICorDebugChain::GetReason メソッド</span><span class="sxs-lookup"><span data-stu-id="64ae5-102">ICorDebugChain::GetReason Method</span></span>
<span data-ttu-id="64ae5-103">この呼び出しチェーンの生成の理由を取得します。</span><span class="sxs-lookup"><span data-stu-id="64ae5-103">Gets the reason for the genesis of this calling chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64ae5-104">構文</span><span class="sxs-lookup"><span data-stu-id="64ae5-104">Syntax</span></span>  
  
```  
HRESULT GetReason (  
    [out] CorDebugChainReason *pReason  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64ae5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="64ae5-105">Parameters</span></span>  
 `pReason`  
 <span data-ttu-id="64ae5-106">[out]この呼び出しチェーンの生成の原因を示す CorDebugChainReason 列挙型の値 (ビットごとの組み合わせ) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="64ae5-106">[out] A pointer to a value (a bitwise combination) of the CorDebugChainReason enumeration that indicates the reason for the genesis of this calling chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64ae5-107">要件</span><span class="sxs-lookup"><span data-stu-id="64ae5-107">Requirements</span></span>  
 <span data-ttu-id="64ae5-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="64ae5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64ae5-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64ae5-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64ae5-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64ae5-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64ae5-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64ae5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

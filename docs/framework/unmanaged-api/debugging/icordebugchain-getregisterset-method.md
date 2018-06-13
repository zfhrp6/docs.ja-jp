---
title: ICorDebugChain::GetRegisterSet メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetRegisterSet
helpviewer_keywords:
- ICorDebugChain::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: bc4288b6-3331-4ae3-990d-e1d6e62ecb67
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bfdde1f29300fcdc0f4e267949fdc3f6fd9917ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401409"
---
# <a name="icordebugchaingetregisterset-method"></a><span data-ttu-id="9928e-102">ICorDebugChain::GetRegisterSet メソッド</span><span class="sxs-lookup"><span data-stu-id="9928e-102">ICorDebugChain::GetRegisterSet Method</span></span>
<span data-ttu-id="9928e-103">このチェーンのアクティブな部分のレジスタ セットを取得します。</span><span class="sxs-lookup"><span data-stu-id="9928e-103">Gets the register set for the active part of this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9928e-104">構文</span><span class="sxs-lookup"><span data-stu-id="9928e-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9928e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9928e-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="9928e-106">[out]アドレスへのポインター、 [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)レジスタを表すオブジェクトをこのチェーンのアクティブな部分を設定します。</span><span class="sxs-lookup"><span data-stu-id="9928e-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for the active part of this chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9928e-107">要件</span><span class="sxs-lookup"><span data-stu-id="9928e-107">Requirements</span></span>  
 <span data-ttu-id="9928e-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9928e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9928e-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9928e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9928e-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9928e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9928e-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9928e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

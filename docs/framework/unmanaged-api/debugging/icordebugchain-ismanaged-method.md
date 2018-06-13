---
title: ICorDebugChain::IsManaged メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::IsManaged
helpviewer_keywords:
- ICorDebugChain::IsManaged method [.NET Framework debugging]
- IsManaged method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 17b389a0-1a4d-4e8a-8613-9bc1769930f9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c8c61cc12e438c0786b6e093b8bb1ea288a42e3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401168"
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="727ca-102">ICorDebugChain::IsManaged メソッド</span><span class="sxs-lookup"><span data-stu-id="727ca-102">ICorDebugChain::IsManaged Method</span></span>
<span data-ttu-id="727ca-103">このチェーンがマネージ コードを実行しているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="727ca-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="727ca-104">構文</span><span class="sxs-lookup"><span data-stu-id="727ca-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="727ca-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="727ca-105">Parameters</span></span>  
 `pManaged`  
 <span data-ttu-id="727ca-106">[out]`true`このチェーンには、マネージ コードが実行されている場合は、それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="727ca-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="727ca-107">要件</span><span class="sxs-lookup"><span data-stu-id="727ca-107">Requirements</span></span>  
 <span data-ttu-id="727ca-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="727ca-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="727ca-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="727ca-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="727ca-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="727ca-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="727ca-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="727ca-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

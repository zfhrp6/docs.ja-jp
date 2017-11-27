---
title: "ICorDebugChain::IsManaged メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.IsManaged
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::IsManaged
helpviewer_keywords:
- ICorDebugChain::IsManaged method [.NET Framework debugging]
- IsManaged method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 17b389a0-1a4d-4e8a-8613-9bc1769930f9
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fe5736a1ca420eb361e062743ed93982e7ec3f29
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="ae2dc-102">ICorDebugChain::IsManaged メソッド</span><span class="sxs-lookup"><span data-stu-id="ae2dc-102">ICorDebugChain::IsManaged Method</span></span>
<span data-ttu-id="ae2dc-103">このチェーンがマネージ コードを実行しているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="ae2dc-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae2dc-104">構文</span><span class="sxs-lookup"><span data-stu-id="ae2dc-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae2dc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ae2dc-105">Parameters</span></span>  
 `pManaged`  
 <span data-ttu-id="ae2dc-106">[out]`true`このチェーンには、マネージ コードが実行されている場合は、それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="ae2dc-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae2dc-107">要件</span><span class="sxs-lookup"><span data-stu-id="ae2dc-107">Requirements</span></span>  
 <span data-ttu-id="ae2dc-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ae2dc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae2dc-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae2dc-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae2dc-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae2dc-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae2dc-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae2dc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

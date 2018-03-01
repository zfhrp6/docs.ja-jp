---
title: "ICorDebugEnum::Clone メソッド"
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
- ICorDebugEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Clone
helpviewer_keywords:
- Clone method, ICorDebugEnum interface [.NET Framework debugging]
- ICorDebugEnum::Clone method [.NET Framework debugging]
ms.assetid: 57eefaf3-75cf-4496-bc94-88c0706861b7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5ddd7d82b6eb2944b1d2a5d7a83f0ccc9f255e45
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="e178d-102">ICorDebugEnum::Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="e178d-102">ICorDebugEnum::Clone Method</span></span>
<span data-ttu-id="e178d-103">この ICorDebugEnum オブジェクトのコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="e178d-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e178d-104">構文</span><span class="sxs-lookup"><span data-stu-id="e178d-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e178d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e178d-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="e178d-106">[out]アドレスへのポインター、`ICorDebugEnum`のこのコピーであるオブジェクトを`ICorDebugEnum`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e178d-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e178d-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="e178d-107">Requirements</span></span>  
 <span data-ttu-id="e178d-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e178d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e178d-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e178d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e178d-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e178d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e178d-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e178d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

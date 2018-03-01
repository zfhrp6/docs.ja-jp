---
title: "ICorDebugEnum::GetCount メソッド"
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
- ICorDebugEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::GetCount
helpviewer_keywords:
- ICorDebugEnum::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: d8a74304-1cb2-4977-a21d-e1af48c563ff
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b2be2e198007e15a0bae3ba0d3dd0cf1cf9983c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugenumgetcount-method"></a><span data-ttu-id="29d3d-102">ICorDebugEnum::GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="29d3d-102">ICorDebugEnum::GetCount Method</span></span>
<span data-ttu-id="29d3d-103">列挙に含まれる項目の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="29d3d-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29d3d-104">構文</span><span class="sxs-lookup"><span data-stu-id="29d3d-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG *pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29d3d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="29d3d-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="29d3d-106">[out]列挙に含まれる項目数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="29d3d-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29d3d-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="29d3d-107">Requirements</span></span>  
 <span data-ttu-id="29d3d-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="29d3d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29d3d-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29d3d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29d3d-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29d3d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29d3d-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29d3d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

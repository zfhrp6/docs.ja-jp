---
title: "ICorDebugType::GetRank メソッド"
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
- ICorDebugType.GetRank
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetRank
helpviewer_keywords:
- GetRank method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetRank method [.NET Framework debugging]
ms.assetid: 72d3d927-f590-4f2d-8f60-448f3dfb96af
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: af481f01202d8a864c5258720f06e67d0bbd1e2b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegetrank-method"></a><span data-ttu-id="16f56-102">ICorDebugType::GetRank メソッド</span><span class="sxs-lookup"><span data-stu-id="16f56-102">ICorDebugType::GetRank Method</span></span>
<span data-ttu-id="16f56-103">配列型の次元数を取得します。</span><span class="sxs-lookup"><span data-stu-id="16f56-103">Gets the number of dimensions in an array type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16f56-104">構文</span><span class="sxs-lookup"><span data-stu-id="16f56-104">Syntax</span></span>  
  
```  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16f56-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="16f56-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="16f56-106">[out]次元数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="16f56-106">[out] A pointer to the number of dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16f56-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="16f56-107">Requirements</span></span>  
 <span data-ttu-id="16f56-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="16f56-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16f56-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16f56-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16f56-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16f56-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16f56-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16f56-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

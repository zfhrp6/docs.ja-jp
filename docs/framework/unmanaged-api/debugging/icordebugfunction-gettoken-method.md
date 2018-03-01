---
title: "ICorDebugFunction::GetToken メソッド"
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
- ICorDebugFunction.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetToken
helpviewer_keywords:
- ICorDebugFunction::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: c6bbf479-062e-48e9-9c70-0f92e293e36a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7edf1f9dadafd989197170123cb3cb470a5ea908
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="bc259-102">ICorDebugFunction::GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="bc259-102">ICorDebugFunction::GetToken Method</span></span>
<span data-ttu-id="bc259-103">この関数のメタデータ トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="bc259-103">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc259-104">構文</span><span class="sxs-lookup"><span data-stu-id="bc259-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc259-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bc259-105">Parameters</span></span>  
 `pMethodDef`  
 <span data-ttu-id="bc259-106">[out]ポインター、`mdMethodDef`この関数のメタデータを参照するトークン。</span><span class="sxs-lookup"><span data-stu-id="bc259-106">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc259-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="bc259-107">Requirements</span></span>  
 <span data-ttu-id="bc259-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bc259-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc259-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc259-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc259-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc259-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc259-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc259-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

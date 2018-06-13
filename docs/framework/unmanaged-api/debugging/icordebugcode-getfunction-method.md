---
title: ICorDebugCode::GetFunction メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetFunction method [.NET Framework debugging]
ms.assetid: c568b737-fdb2-4816-accd-051f5ab760f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8d0e7f20be3f18e49dcc1b986460d5da0c3d7777
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401941"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="034d8-102">ICorDebugCode::GetFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="034d8-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="034d8-103">この"ICorDebugCode"に関連付けられている"ICorDebugFunction"を取得します。</span><span class="sxs-lookup"><span data-stu-id="034d8-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="034d8-104">構文</span><span class="sxs-lookup"><span data-stu-id="034d8-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="034d8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="034d8-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="034d8-106">[out]関数のアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="034d8-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="034d8-107">コメント</span><span class="sxs-lookup"><span data-stu-id="034d8-107">Remarks</span></span>  
 <span data-ttu-id="034d8-108">`ICorDebugCode` および`ICorDebugFunction`一対一の関係を維持します。</span><span class="sxs-lookup"><span data-stu-id="034d8-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="034d8-109">要件</span><span class="sxs-lookup"><span data-stu-id="034d8-109">Requirements</span></span>  
 <span data-ttu-id="034d8-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="034d8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="034d8-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="034d8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="034d8-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="034d8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="034d8-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="034d8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="034d8-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="034d8-114">See Also</span></span>  
 

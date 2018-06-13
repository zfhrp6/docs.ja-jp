---
title: ICorDebugEval::IsActive メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::IsActive method [.NET Framework debugging]
ms.assetid: bf2bba24-d278-43bd-b1c5-35680e748d3e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fe29b3e35d2fbd42fac2d9ec1d1c594abe1239c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411159"
---
# <a name="icordebugevalisactive-method"></a><span data-ttu-id="239a4-102">ICorDebugEval::IsActive メソッド</span><span class="sxs-lookup"><span data-stu-id="239a4-102">ICorDebugEval::IsActive Method</span></span>
<span data-ttu-id="239a4-103">この ICorDebugEval オブジェクトが現在実行されているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="239a4-103">Gets a value that indicates whether this ICorDebugEval object is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="239a4-104">構文</span><span class="sxs-lookup"><span data-stu-id="239a4-104">Syntax</span></span>  
  
```  
HRESULT IsActive (  
    [out] BOOL              *pbActive  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="239a4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="239a4-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="239a4-106">[out]この評価がアクティブかどうかを示す値を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="239a4-106">[out] Pointer to a value that indicates whether this evaluation is active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="239a4-107">要件</span><span class="sxs-lookup"><span data-stu-id="239a4-107">Requirements</span></span>  
 <span data-ttu-id="239a4-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="239a4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="239a4-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="239a4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="239a4-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="239a4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="239a4-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="239a4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

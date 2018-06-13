---
title: ICorDebugEval::GetResult メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e160eddf667b542929c8dd3790de666a8e8bb77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413060"
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="191d4-102">ICorDebugEval::GetResult メソッド</span><span class="sxs-lookup"><span data-stu-id="191d4-102">ICorDebugEval::GetResult Method</span></span>
<span data-ttu-id="191d4-103">この評価の結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="191d4-103">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="191d4-104">構文</span><span class="sxs-lookup"><span data-stu-id="191d4-104">Syntax</span></span>  
  
```  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="191d4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="191d4-105">Parameters</span></span>  
 `ppResult`  
 <span data-ttu-id="191d4-106">[out]評価が正常に完了した場合は、この評価の結果を表す ICorDebugValue オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="191d4-106">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="191d4-107">コメント</span><span class="sxs-lookup"><span data-stu-id="191d4-107">Remarks</span></span>  
 <span data-ttu-id="191d4-108">`GetResult`メソッドが有効では、評価が完了した後のみです。</span><span class="sxs-lookup"><span data-stu-id="191d4-108">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="191d4-109">通常、評価が完了すると`ppResult`結果を指定します。</span><span class="sxs-lookup"><span data-stu-id="191d4-109">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="191d4-110">例外で終了した場合にスローされる例外になります。</span><span class="sxs-lookup"><span data-stu-id="191d4-110">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="191d4-111">新しいオブジェクトの評価であった場合、新しいオブジェクトへの参照になります。</span><span class="sxs-lookup"><span data-stu-id="191d4-111">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="191d4-112">要件</span><span class="sxs-lookup"><span data-stu-id="191d4-112">Requirements</span></span>  
 <span data-ttu-id="191d4-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="191d4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="191d4-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="191d4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="191d4-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="191d4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="191d4-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="191d4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

---
title: "ICorDebugILCode::GetEHClauses メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILCode.GetEHClauses
api_location: mscordbi.dll
api_type: COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 39d30ef572423d8cb988c074971de095f1709e8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="d1aad-102">ICorDebugILCode::GetEHClauses メソッド</span><span class="sxs-lookup"><span data-stu-id="d1aad-102">ICorDebugILCode::GetEHClauses Method</span></span>
<span data-ttu-id="d1aad-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="d1aad-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d1aad-104">この中間言語 (IL) に対して定義されている例外処理 (EH) 句のリストへのポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="d1aad-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1aad-105">構文</span><span class="sxs-lookup"><span data-stu-id="d1aad-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1aad-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d1aad-106">Parameters</span></span>  
 `cClauses`  
 <span data-ttu-id="d1aad-107">[in] `clauses` アレイの記憶容量。</span><span class="sxs-lookup"><span data-stu-id="d1aad-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="d1aad-108">詳細については、次の「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1aad-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="d1aad-109">[out] 情報が `clauses` アレイに書き込まれる場合に、対象となる句の数。</span><span class="sxs-lookup"><span data-stu-id="d1aad-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="d1aad-110">clauses</span><span class="sxs-lookup"><span data-stu-id="d1aad-110">clauses</span></span>  
 <span data-ttu-id="d1aad-111">[out]配列[CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)例外処理句のこの IL に対して定義されている情報を含むオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d1aad-111">[out] An array of [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1aad-112">コメント</span><span class="sxs-lookup"><span data-stu-id="d1aad-112">Remarks</span></span>  
 <span data-ttu-id="d1aad-113">場合`cClauses`0 と`pcClauses`以外**null**、`pcClauses`が利用可能な例外処理句の数に設定します。</span><span class="sxs-lookup"><span data-stu-id="d1aad-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="d1aad-114">`cClauses` が 0 以外の場合は、`clauses` アレイの記憶容量を表します。</span><span class="sxs-lookup"><span data-stu-id="d1aad-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="d1aad-115">メソッドが戻るとき、`clauses` には、`cClauses` の最大項目が含まれ、`pcClauses` は、実際に`clauses` アレイに書き込まれる句の数が設定されます。</span><span class="sxs-lookup"><span data-stu-id="d1aad-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1aad-116">要件</span><span class="sxs-lookup"><span data-stu-id="d1aad-116">Requirements</span></span>  
 <span data-ttu-id="d1aad-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d1aad-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1aad-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1aad-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1aad-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1aad-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1aad-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1aad-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1aad-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1aad-121">See Also</span></span>  
 [<span data-ttu-id="d1aad-122">ICorDebugILCode インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d1aad-122">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 [<span data-ttu-id="d1aad-123">CorDebugEHClause 構造体</span><span class="sxs-lookup"><span data-stu-id="d1aad-123">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 [<span data-ttu-id="d1aad-124">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d1aad-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
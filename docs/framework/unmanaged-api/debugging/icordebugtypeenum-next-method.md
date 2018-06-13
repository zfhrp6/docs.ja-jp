---
title: ICorDebugTypeEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugTypeEnum::Next
helpviewer_keywords:
- ICorDebugTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: d0fdeba3-c195-4ece-8caf-79b1f40025d2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9812fa4248533ccb898c98082e42e288c091f776
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420587"
---
# <a name="icordebugtypeenumnext-method"></a><span data-ttu-id="3cc0f-102">ICorDebugTypeEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="3cc0f-102">ICorDebugTypeEnum::Next Method</span></span>
<span data-ttu-id="3cc0f-103">指定された"ICorDebugType"インスタンスの数を取得`celt`列挙体の現在位置にあるからです。</span><span class="sxs-lookup"><span data-stu-id="3cc0f-103">Gets the number of "ICorDebugType" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cc0f-104">構文</span><span class="sxs-lookup"><span data-stu-id="3cc0f-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3cc0f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3cc0f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="3cc0f-106">[in]数`ICorDebugType`を取得するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="3cc0f-106">[in] The number of `ICorDebugType` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="3cc0f-107">[out]それぞれが指すポインターの配列、`ICorDebugType`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="3cc0f-107">[out] An array of pointers, each of which points to an `ICorDebugType` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="3cc0f-108">[out]数へのポインター`ICorDebugType`実際に返されるインスタンス。</span><span class="sxs-lookup"><span data-stu-id="3cc0f-108">[out] Pointer to the number of `ICorDebugType` instances actually returned.</span></span> <span data-ttu-id="3cc0f-109">この値を null にすることがある場合`celt`は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="3cc0f-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cc0f-110">要件</span><span class="sxs-lookup"><span data-stu-id="3cc0f-110">Requirements</span></span>  
 <span data-ttu-id="3cc0f-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3cc0f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cc0f-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3cc0f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3cc0f-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3cc0f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3cc0f-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cc0f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cc0f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="3cc0f-115">See Also</span></span>  
 

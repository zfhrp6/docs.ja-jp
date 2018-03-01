---
title: "ICorDebugObjectEnum::Next メソッド"
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
- ICorDebugObjectEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c8edc9273710a843b4e99568097646825fc52a09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="744e4-102">ICorDebugObjectEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="744e4-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="744e4-103">列挙体の現在位置から指定した数のオブジェクトの相対仮想アドレス (Rva) を取得します。</span><span class="sxs-lookup"><span data-stu-id="744e4-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="744e4-104">構文</span><span class="sxs-lookup"><span data-stu-id="744e4-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="744e4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="744e4-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="744e4-106">[in] 取得するオブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="744e4-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="744e4-107">[out]ポインターの配列、CORDB_ADDRESS オブジェクトをそれぞれ示しています。</span><span class="sxs-lookup"><span data-stu-id="744e4-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="744e4-108">[out]実際に返されるオブジェクトの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="744e4-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="744e4-109">この値を null にすることがある場合`celt`は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="744e4-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="744e4-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="744e4-110">Requirements</span></span>  
 <span data-ttu-id="744e4-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="744e4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="744e4-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="744e4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="744e4-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="744e4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="744e4-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="744e4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="744e4-115">参照</span><span class="sxs-lookup"><span data-stu-id="744e4-115">See Also</span></span>  
 

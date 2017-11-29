---
title: "ICorDebugObjectEnum::Next メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 72195dbf74639d5799bb96754019dddf0f30101a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="9ab56-102">ICorDebugObjectEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="9ab56-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="9ab56-103">列挙体の現在位置から指定した数のオブジェクトの相対仮想アドレス (Rva) を取得します。</span><span class="sxs-lookup"><span data-stu-id="9ab56-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ab56-104">構文</span><span class="sxs-lookup"><span data-stu-id="9ab56-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ab56-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ab56-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9ab56-106">[in] 取得するオブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="9ab56-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="9ab56-107">[out]ポインターの配列、CORDB_ADDRESS オブジェクトをそれぞれ示しています。</span><span class="sxs-lookup"><span data-stu-id="9ab56-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9ab56-108">[out]実際に返されるオブジェクトの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ab56-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="9ab56-109">この値を null にすることがある場合`celt`は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="9ab56-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ab56-110">要件</span><span class="sxs-lookup"><span data-stu-id="9ab56-110">Requirements</span></span>  
 <span data-ttu-id="9ab56-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ab56-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ab56-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ab56-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ab56-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ab56-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ab56-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ab56-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ab56-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ab56-115">See Also</span></span>  
 

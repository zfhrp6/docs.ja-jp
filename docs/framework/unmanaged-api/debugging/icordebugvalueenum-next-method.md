---
title: "ICorDebugValueEnum::Next メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValueEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 71775db7134c8f376099b0820f4330602d3db0e6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="2f691-102">ICorDebugValueEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="2f691-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="2f691-103">列挙体の現在位置から指定数の"ICorDebugValue"のインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="2f691-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f691-104">構文</span><span class="sxs-lookup"><span data-stu-id="2f691-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2f691-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2f691-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="2f691-106">[in]数`ICorDebugValue`を取得するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="2f691-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="2f691-107">[out]それぞれが指すポインターの配列、`ICorDebugValue`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="2f691-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="2f691-108">[out]数へのポインター`ICorDebugValue`実際に返されるインスタンス。</span><span class="sxs-lookup"><span data-stu-id="2f691-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="2f691-109">この値を null にすることがある場合`celt`は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="2f691-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f691-110">要件</span><span class="sxs-lookup"><span data-stu-id="2f691-110">Requirements</span></span>  
 <span data-ttu-id="2f691-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f691-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f691-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f691-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f691-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f691-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f691-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f691-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f691-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f691-115">See Also</span></span>  
    
 

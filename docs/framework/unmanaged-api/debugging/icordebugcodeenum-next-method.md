---
title: "ICorDebugCodeEnum::Next メソッド"
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
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5dbc7985ebf2fff5fa0c5b524b8d6560f75318d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="9a684-102">ICorDebugCodeEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="9a684-102">ICorDebugCodeEnum::Next Method</span></span>
<span data-ttu-id="9a684-103">列挙体の現在位置から指定数の"ICorDebugCode"のインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="9a684-103">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a684-104">構文</span><span class="sxs-lookup"><span data-stu-id="9a684-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugCode *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a684-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9a684-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9a684-106">[in]数`ICorDebugCode`を取得するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="9a684-106">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="9a684-107">[out]それぞれが指すポインターの配列、`ICorDebugCode`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="9a684-107">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9a684-108">[out]数へのポインター`ICorDebugCode`実際に返されるインスタンス。</span><span class="sxs-lookup"><span data-stu-id="9a684-108">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="9a684-109">この値を null にすることがある場合`celt`は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="9a684-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a684-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="9a684-110">Requirements</span></span>  
 <span data-ttu-id="9a684-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9a684-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a684-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a684-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a684-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a684-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a684-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a684-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a684-115">参照</span><span class="sxs-lookup"><span data-stu-id="9a684-115">See Also</span></span>  
    
 

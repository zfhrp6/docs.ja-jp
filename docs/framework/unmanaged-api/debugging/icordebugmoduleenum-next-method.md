---
title: "ICorDebugModuleEnum::Next メソッド"
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
- ICorDebugModuleEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum::Next
helpviewer_keywords:
- ICorDebugModuleEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 9ff3fcd6-38fe-41f8-bfd3-f0ab6c7d77ca
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a57043f100b1cce35139d753d12707c2c2c349f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="8c8bc-102">ICorDebugModuleEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="8c8bc-102">ICorDebugModuleEnum::Next Method</span></span>
<span data-ttu-id="8c8bc-103">指定された"ICorDebugModule"インスタンスの数を取得`celt`列挙体の現在位置にあるからです。</span><span class="sxs-lookup"><span data-stu-id="8c8bc-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c8bc-104">構文</span><span class="sxs-lookup"><span data-stu-id="8c8bc-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c8bc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c8bc-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="8c8bc-106">[in]数`ICorDebugModule`を取得するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="8c8bc-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="8c8bc-107">[out]それぞれが指すポインターの配列、`ICorDebugModule`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8c8bc-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="8c8bc-108">[out]数へのポインター`ICorDebugModule`実際に返されるインスタンス。</span><span class="sxs-lookup"><span data-stu-id="8c8bc-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="8c8bc-109">この値を null にすることがある場合`celt`は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="8c8bc-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c8bc-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="8c8bc-110">Requirements</span></span>  
 <span data-ttu-id="8c8bc-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8c8bc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c8bc-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c8bc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c8bc-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c8bc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c8bc-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c8bc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c8bc-115">参照</span><span class="sxs-lookup"><span data-stu-id="8c8bc-115">See Also</span></span>  
 

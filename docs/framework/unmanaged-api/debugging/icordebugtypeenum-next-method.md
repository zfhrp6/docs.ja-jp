---
title: "ICorDebugTypeEnum::Next メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugTypeEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugTypeEnum::Next
helpviewer_keywords:
- ICorDebugTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: d0fdeba3-c195-4ece-8caf-79b1f40025d2
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 38f48c379ad4d84c2b16c208b33b71ac75caa52f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtypeenumnext-method"></a><span data-ttu-id="b42f8-102">ICorDebugTypeEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="b42f8-102">ICorDebugTypeEnum::Next Method</span></span>
<span data-ttu-id="b42f8-103">指定された"ICorDebugType"インスタンスの数を取得`celt`列挙体の現在位置にあるからです。</span><span class="sxs-lookup"><span data-stu-id="b42f8-103">Gets the number of "ICorDebugType" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b42f8-104">構文</span><span class="sxs-lookup"><span data-stu-id="b42f8-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b42f8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b42f8-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b42f8-106">[in]数`ICorDebugType`を取得するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="b42f8-106">[in] The number of `ICorDebugType` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="b42f8-107">[out]それぞれが指すポインターの配列、`ICorDebugType`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="b42f8-107">[out] An array of pointers, each of which points to an `ICorDebugType` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b42f8-108">[out]数へのポインター`ICorDebugType`実際に返されるインスタンス。</span><span class="sxs-lookup"><span data-stu-id="b42f8-108">[out] Pointer to the number of `ICorDebugType` instances actually returned.</span></span> <span data-ttu-id="b42f8-109">この値を null にすることがある場合`celt`は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="b42f8-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b42f8-110">要件</span><span class="sxs-lookup"><span data-stu-id="b42f8-110">Requirements</span></span>  
 <span data-ttu-id="b42f8-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b42f8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b42f8-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b42f8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b42f8-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b42f8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b42f8-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b42f8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b42f8-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="b42f8-115">See Also</span></span>  
 

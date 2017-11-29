---
title: "ICorDebugCodeEnum::Next メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCodeEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0260f52a32d5cd6d2862927bb0938c90bc430440
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="8df61-102">ICorDebugCodeEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="8df61-102">ICorDebugCodeEnum::Next Method</span></span>
<span data-ttu-id="8df61-103">列挙体の現在位置から指定数の"ICorDebugCode"のインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="8df61-103">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8df61-104">構文</span><span class="sxs-lookup"><span data-stu-id="8df61-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugCode *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8df61-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8df61-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="8df61-106">[in]数`ICorDebugCode`を取得するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="8df61-106">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="8df61-107">[out]それぞれが指すポインターの配列、`ICorDebugCode`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8df61-107">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="8df61-108">[out]数へのポインター`ICorDebugCode`実際に返されるインスタンス。</span><span class="sxs-lookup"><span data-stu-id="8df61-108">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="8df61-109">この値を null にすることがある場合`celt`は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="8df61-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8df61-110">要件</span><span class="sxs-lookup"><span data-stu-id="8df61-110">Requirements</span></span>  
 <span data-ttu-id="8df61-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8df61-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8df61-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8df61-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8df61-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8df61-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8df61-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8df61-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8df61-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="8df61-115">See Also</span></span>  
    
 

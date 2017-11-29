---
title: "ICorDebugGuidToTypeEnum::Next メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGuidToTypeEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 277661c8c5490b5c1f68cb8fdaf1eff5a020250f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="8c6ca-102">ICorDebugGuidToTypeEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="8c6ca-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="8c6ca-103">指定した数を取得[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)情報を入力する Guid をマップするインスタンス。</span><span class="sxs-lookup"><span data-stu-id="8c6ca-103">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c6ca-104">構文</span><span class="sxs-lookup"><span data-stu-id="8c6ca-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c6ca-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c6ca-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="8c6ca-106">[in]取得する型の GUID へマッピング オブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="8c6ca-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="8c6ca-107">[out]それぞれが指すポインターの配列、 [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)にマップするオブジェクト、[!INCLUDE[wrt](../../../../includes/wrt-md.md)]を対応する ICorDebugType オブジェクトの GUID。</span><span class="sxs-lookup"><span data-stu-id="8c6ca-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) object that maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="8c6ca-108">[out]数へのポインター [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)で実際に返されたオブジェクト`values`です。</span><span class="sxs-lookup"><span data-stu-id="8c6ca-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c6ca-109">コメント</span><span class="sxs-lookup"><span data-stu-id="8c6ca-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c6ca-110">要件</span><span class="sxs-lookup"><span data-stu-id="8c6ca-110">Requirements</span></span>  
 <span data-ttu-id="8c6ca-111">**プラットフォーム:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c6ca-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="8c6ca-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c6ca-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c6ca-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c6ca-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c6ca-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c6ca-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c6ca-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c6ca-115">See Also</span></span>  
 [<span data-ttu-id="8c6ca-116">ICorDebugGuidToTypeEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c6ca-116">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 [<span data-ttu-id="8c6ca-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c6ca-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

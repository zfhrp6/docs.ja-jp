---
title: ICorDebugGuidToTypeEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c156be3af49ac99f040360bda9f60f21a9ad66b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416219"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="3d89a-102">ICorDebugGuidToTypeEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="3d89a-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="3d89a-103">指定した数を取得[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)情報を入力する Guid をマップするインスタンス。</span><span class="sxs-lookup"><span data-stu-id="3d89a-103">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d89a-104">構文</span><span class="sxs-lookup"><span data-stu-id="3d89a-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d89a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3d89a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="3d89a-106">[in]取得する型の GUID へマッピング オブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="3d89a-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="3d89a-107">[out]それぞれが指すポインターの配列、 [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)にマップするオブジェクト、[!INCLUDE[wrt](../../../../includes/wrt-md.md)]を対応する ICorDebugType オブジェクトの GUID。</span><span class="sxs-lookup"><span data-stu-id="3d89a-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) object that maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="3d89a-108">[out]数へのポインター [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)で実際に返されたオブジェクト`values`です。</span><span class="sxs-lookup"><span data-stu-id="3d89a-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d89a-109">コメント</span><span class="sxs-lookup"><span data-stu-id="3d89a-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d89a-110">要件</span><span class="sxs-lookup"><span data-stu-id="3d89a-110">Requirements</span></span>  
 <span data-ttu-id="3d89a-111">**プラットフォーム:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d89a-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="3d89a-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d89a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d89a-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d89a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d89a-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d89a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d89a-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d89a-115">See Also</span></span>  
 [<span data-ttu-id="3d89a-116">ICorDebugGuidToTypeEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d89a-116">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 [<span data-ttu-id="3d89a-117">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d89a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

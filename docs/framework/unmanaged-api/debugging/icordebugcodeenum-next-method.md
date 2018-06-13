---
title: ICorDebugCodeEnum::Next メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 711c85b930617632d69497e4a9cf0a74360d27f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415108"
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="fbcbf-102">ICorDebugCodeEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="fbcbf-102">ICorDebugCodeEnum::Next Method</span></span>
<span data-ttu-id="fbcbf-103">列挙体の現在位置から指定数の"ICorDebugCode"のインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="fbcbf-103">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbcbf-104">構文</span><span class="sxs-lookup"><span data-stu-id="fbcbf-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugCode *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fbcbf-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fbcbf-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="fbcbf-106">[in]数`ICorDebugCode`を取得するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="fbcbf-106">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="fbcbf-107">[out]それぞれが指すポインターの配列、`ICorDebugCode`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="fbcbf-107">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="fbcbf-108">[out]数へのポインター`ICorDebugCode`実際に返されるインスタンス。</span><span class="sxs-lookup"><span data-stu-id="fbcbf-108">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="fbcbf-109">この値を null にすることがある場合`celt`は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="fbcbf-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbcbf-110">要件</span><span class="sxs-lookup"><span data-stu-id="fbcbf-110">Requirements</span></span>  
 <span data-ttu-id="fbcbf-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fbcbf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbcbf-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fbcbf-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fbcbf-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbcbf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbcbf-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbcbf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbcbf-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="fbcbf-115">See Also</span></span>  
    
 

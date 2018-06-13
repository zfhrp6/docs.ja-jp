---
title: ICorDebugGCReferenceEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01e52385f1a94ffb9682bdbe92e5c95e9870611e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416804"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="d7f90-102">ICorDebugGCReferenceEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="d7f90-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="d7f90-103">指定した数を取得[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)ガベージ コレクトされるオブジェクトに関する情報が含まれているインスタンス。</span><span class="sxs-lookup"><span data-stu-id="d7f90-103">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7f90-104">構文</span><span class="sxs-lookup"><span data-stu-id="d7f90-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7f90-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d7f90-105">Parameters</span></span>  
 <span data-ttu-id="d7f90-106">celt</span><span class="sxs-lookup"><span data-stu-id="d7f90-106">celt</span></span>  
 <span data-ttu-id="d7f90-107">[in]取得するルートの数。</span><span class="sxs-lookup"><span data-stu-id="d7f90-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="d7f90-108">ルート</span><span class="sxs-lookup"><span data-stu-id="d7f90-108">roots</span></span>  
 <span data-ttu-id="d7f90-109">[out]それぞれが指すポインターの配列、 [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)ガベージ コレクトされるオブジェクトのルートを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d7f90-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="d7f90-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="d7f90-110">pceltFetched</span></span>  
 <span data-ttu-id="d7f90-111">[out]数へのポインター [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)で実際に返されたオブジェクト`roots`です。</span><span class="sxs-lookup"><span data-stu-id="d7f90-111">[out] A pointer to the number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="d7f90-112">`celt` が 1 の場合、この値は`null` になることがあります。</span><span class="sxs-lookup"><span data-stu-id="d7f90-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7f90-113">コメント</span><span class="sxs-lookup"><span data-stu-id="d7f90-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7f90-114">要件</span><span class="sxs-lookup"><span data-stu-id="d7f90-114">Requirements</span></span>  
 <span data-ttu-id="d7f90-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d7f90-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7f90-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7f90-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7f90-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7f90-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7f90-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7f90-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7f90-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7f90-119">See Also</span></span>  
 [<span data-ttu-id="d7f90-120">ICorDebugGCReferenceEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7f90-120">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 [<span data-ttu-id="d7f90-121">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7f90-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

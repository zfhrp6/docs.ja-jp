---
title: "ICorPublishProcessEnum::Next メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcessEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcessEnum::Next
helpviewer_keywords:
- ICorPublishProcessEnum::Next method [.NET Framework debugging]
- Next method, ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: 6c399f37-1e38-4ca1-b70d-8ae41f7228b7
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6823a8d973b997576da3271c85234b347f1c8562
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishprocessenumnext-method"></a><span data-ttu-id="6b861-102">ICorPublishProcessEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="6b861-102">ICorPublishProcessEnum::Next Method</span></span>
<span data-ttu-id="6b861-103">現在のカーソル位置以降にある、コレクションから指定された数のプロセスを取得します。</span><span class="sxs-lookup"><span data-stu-id="6b861-103">Gets the specified number of processes from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b861-104">構文</span><span class="sxs-lookup"><span data-stu-id="6b861-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b861-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6b861-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6b861-106">[in]取得するプロセスの数。</span><span class="sxs-lookup"><span data-stu-id="6b861-106">[in] The number of processes to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="6b861-107">[out]配列へのポインターを取得[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)プロセスを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="6b861-107">[out] A pointer to the array of retrieved [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects, each of which represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6b861-108">[out]プロセスの数へのポインターが実際に返されます。</span><span class="sxs-lookup"><span data-stu-id="6b861-108">[out] Pointer to the number of processes actually returned.</span></span> <span data-ttu-id="6b861-109">この値を null にすることがある場合`celt`は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="6b861-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b861-110">要件</span><span class="sxs-lookup"><span data-stu-id="6b861-110">Requirements</span></span>  
 <span data-ttu-id="6b861-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6b861-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b861-112">**ヘッダー:** CorPub.idl、CorPub.h</span><span class="sxs-lookup"><span data-stu-id="6b861-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="6b861-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b861-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b861-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b861-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b861-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b861-115">See Also</span></span>  
 [<span data-ttu-id="6b861-116">ICorPublishProcessEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b861-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)

---
title: ICorPublishProcessEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum::Next
helpviewer_keywords:
- ICorPublishProcessEnum::Next method [.NET Framework debugging]
- Next method, ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: 6c399f37-1e38-4ca1-b70d-8ae41f7228b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19a10a527c37d93d00bec799fdaa12bb0ad3fdbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icorpublishprocessenumnext-method"></a><span data-ttu-id="7f93a-102">ICorPublishProcessEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="7f93a-102">ICorPublishProcessEnum::Next Method</span></span>
<span data-ttu-id="7f93a-103">現在のカーソル位置以降にある、コレクションから指定された数のプロセスを取得します。</span><span class="sxs-lookup"><span data-stu-id="7f93a-103">Gets the specified number of processes from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f93a-104">構文</span><span class="sxs-lookup"><span data-stu-id="7f93a-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f93a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7f93a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7f93a-106">[in]取得するプロセスの数。</span><span class="sxs-lookup"><span data-stu-id="7f93a-106">[in] The number of processes to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="7f93a-107">[out]配列へのポインターを取得[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)プロセスを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7f93a-107">[out] A pointer to the array of retrieved [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects, each of which represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="7f93a-108">[out]プロセスの数へのポインターが実際に返されます。</span><span class="sxs-lookup"><span data-stu-id="7f93a-108">[out] Pointer to the number of processes actually returned.</span></span> <span data-ttu-id="7f93a-109">この値を null にすることがある場合`celt`は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="7f93a-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f93a-110">要件</span><span class="sxs-lookup"><span data-stu-id="7f93a-110">Requirements</span></span>  
 <span data-ttu-id="7f93a-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7f93a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f93a-112">**ヘッダー:** CorPub.idl、CorPub.h</span><span class="sxs-lookup"><span data-stu-id="7f93a-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="7f93a-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f93a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f93a-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f93a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f93a-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f93a-115">See Also</span></span>  
 [<span data-ttu-id="7f93a-116">ICorPublishProcessEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7f93a-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)

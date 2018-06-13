---
title: ICorPublishEnum::Clone メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Clone
helpviewer_keywords:
- Clone method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::Clone method [.NET Framework debugging]
ms.assetid: c9a26ea3-b8eb-4b8e-854f-9a2ca26b3b39
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12d9e468027e88cc74900364459f83d7e5125a9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423807"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="aa3d8-102">ICorPublishEnum::Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="aa3d8-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="aa3d8-103">このコピーを作成[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="aa3d8-103">Creates a copy of this [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa3d8-104">構文</span><span class="sxs-lookup"><span data-stu-id="aa3d8-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aa3d8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa3d8-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="aa3d8-106">[out]アドレスへのポインター、`ICorPublishEnum`のこのコピーであるオブジェクトを`ICorPublishEnum`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="aa3d8-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa3d8-107">要件</span><span class="sxs-lookup"><span data-stu-id="aa3d8-107">Requirements</span></span>  
 <span data-ttu-id="aa3d8-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="aa3d8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa3d8-109">**ヘッダー:** CorPub.idl、CorPub.h</span><span class="sxs-lookup"><span data-stu-id="aa3d8-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="aa3d8-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa3d8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa3d8-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa3d8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa3d8-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa3d8-112">See Also</span></span>  
 [<span data-ttu-id="aa3d8-113">ICorPublishEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aa3d8-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)

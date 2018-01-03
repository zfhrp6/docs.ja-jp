---
title: "ICorPublishEnum::GetCount メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishEnum.GetCount
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishEnum::GetCount
helpviewer_keywords:
- GetCount method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::GetCount method [.NET Framework debugging]
ms.assetid: d228f684-2be3-4029-93ae-31fe02213c1f
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 023965489530e70deb7dc9460418ef0d56654081
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="a5e61-102">ICorPublishEnum::GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="a5e61-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="a5e61-103">列挙に含まれる項目の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="a5e61-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5e61-104">構文</span><span class="sxs-lookup"><span data-stu-id="a5e61-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a5e61-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a5e61-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="a5e61-106">[out]列挙に含まれる項目数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a5e61-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5e61-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="a5e61-107">Requirements</span></span>  
 <span data-ttu-id="a5e61-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a5e61-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5e61-109">**ヘッダー:** CorPub.idl、CorPub.h</span><span class="sxs-lookup"><span data-stu-id="a5e61-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a5e61-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5e61-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5e61-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5e61-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5e61-112">参照</span><span class="sxs-lookup"><span data-stu-id="a5e61-112">See Also</span></span>  
 [<span data-ttu-id="a5e61-113">ICorPublishEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5e61-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)

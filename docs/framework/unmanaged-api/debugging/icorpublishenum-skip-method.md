---
title: "ICorPublishEnum::Skip メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishEnum.Skip
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishEnum::Skip
helpviewer_keywords:
- ICorPublishEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 1680ec06-4ab0-447e-93ad-cdb8693fde5c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6f75681237ff00b61cf584fb99c7ee6bbda6df48
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishenumskip-method"></a><span data-ttu-id="6df45-102">ICorPublishEnum::Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="6df45-102">ICorPublishEnum::Skip Method</span></span>
<span data-ttu-id="6df45-103">列挙体の指定数の項目でカーソルを前方に移動します。</span><span class="sxs-lookup"><span data-stu-id="6df45-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6df45-104">構文</span><span class="sxs-lookup"><span data-stu-id="6df45-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6df45-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6df45-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6df45-106">[in]カーソルを前方に移動する項目の数。</span><span class="sxs-lookup"><span data-stu-id="6df45-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6df45-107">要件</span><span class="sxs-lookup"><span data-stu-id="6df45-107">Requirements</span></span>  
 <span data-ttu-id="6df45-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6df45-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6df45-109">**ヘッダー:** CorPub.idl、CorPub.h</span><span class="sxs-lookup"><span data-stu-id="6df45-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="6df45-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6df45-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6df45-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6df45-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6df45-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="6df45-112">See Also</span></span>  
 [<span data-ttu-id="6df45-113">ICorPublishEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6df45-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)

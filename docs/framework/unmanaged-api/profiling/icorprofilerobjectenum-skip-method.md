---
title: "ICorProfilerObjectEnum::Skip メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerObjectEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Skip
helpviewer_keywords:
- ICorProfilerObjectEnum::Skip method [.NET Framework profiling]
- Skip method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: f8e498f8-f93a-4b82-bd22-55bdbf5e8d45
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 607db61b25bafed841a81e8578438f4f70d4ee03
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="ede02-102">ICorProfilerObjectEnum::Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="ede02-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="ede02-103">指定した要素数がスキップされるように、現在の位置からこの列挙子のカーソルを進めます。</span><span class="sxs-lookup"><span data-stu-id="ede02-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ede02-104">構文</span><span class="sxs-lookup"><span data-stu-id="ede02-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ede02-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ede02-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ede02-106">[in]スキップする要素の数。</span><span class="sxs-lookup"><span data-stu-id="ede02-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ede02-107">コメント</span><span class="sxs-lookup"><span data-stu-id="ede02-107">Remarks</span></span>  
 <span data-ttu-id="ede02-108">この列挙子のカーソルの新しい位置は: (現在の位置) +`celt`です。</span><span class="sxs-lookup"><span data-stu-id="ede02-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ede02-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="ede02-109">Requirements</span></span>  
 <span data-ttu-id="ede02-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ede02-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ede02-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ede02-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ede02-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ede02-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ede02-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ede02-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ede02-114">参照</span><span class="sxs-lookup"><span data-stu-id="ede02-114">See Also</span></span>  
 [<span data-ttu-id="ede02-115">ICorProfilerObjectEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ede02-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)

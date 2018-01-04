---
title: "COR_PRF_FUNCTION 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_FUNCTION
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_FUNCTION
helpviewer_keywords: COR_PRF_FUNCTION structure [.NET Framework profiling]
ms.assetid: 8bb5acf5-cf4b-4ccb-93f1-46db1f3f8bf3
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 15ef81f07438a7cc18f7a131ee8cf9c50c47eb6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corprffunction-structure"></a><span data-ttu-id="57675-102">COR_PRF_FUNCTION 構造体</span><span class="sxs-lookup"><span data-stu-id="57675-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="57675-103">関数の一意の表記を、その関数の ID を再コンパイルされたバージョンの ID と組み合わせることによって、提供します。</span><span class="sxs-lookup"><span data-stu-id="57675-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57675-104">構文</span><span class="sxs-lookup"><span data-stu-id="57675-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="57675-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="57675-105">Members</span></span>  
  
|<span data-ttu-id="57675-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="57675-106">Member</span></span>|<span data-ttu-id="57675-107">説明</span><span class="sxs-lookup"><span data-stu-id="57675-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="57675-108">関数の ID。</span><span class="sxs-lookup"><span data-stu-id="57675-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="57675-109">再コンパイルされた関数の ID。</span><span class="sxs-lookup"><span data-stu-id="57675-109">The ID of the recompiled function.</span></span> <span data-ttu-id="57675-110">0 (ゼロ) の値では、関数の元のバージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="57675-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57675-111">コメント</span><span class="sxs-lookup"><span data-stu-id="57675-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57675-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="57675-112">Requirements</span></span>  
 <span data-ttu-id="57675-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="57675-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57675-114">**ヘッダー:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="57675-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="57675-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57675-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57675-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57675-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57675-117">参照</span><span class="sxs-lookup"><span data-stu-id="57675-117">See Also</span></span>  
 [<span data-ttu-id="57675-118">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="57675-118">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)

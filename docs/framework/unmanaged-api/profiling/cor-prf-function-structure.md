---
title: COR_PRF_FUNCTION 構造体
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION
helpviewer_keywords:
- COR_PRF_FUNCTION structure [.NET Framework profiling]
ms.assetid: 8bb5acf5-cf4b-4ccb-93f1-46db1f3f8bf3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1bc8d588641163ccf98054fdf1930a72a04c770c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452063"
---
# <a name="corprffunction-structure"></a><span data-ttu-id="67181-102">COR_PRF_FUNCTION 構造体</span><span class="sxs-lookup"><span data-stu-id="67181-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="67181-103">関数の一意の表記を、その関数の ID を再コンパイルされたバージョンの ID と組み合わせることによって、提供します。</span><span class="sxs-lookup"><span data-stu-id="67181-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67181-104">構文</span><span class="sxs-lookup"><span data-stu-id="67181-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="67181-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="67181-105">Members</span></span>  
  
|<span data-ttu-id="67181-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="67181-106">Member</span></span>|<span data-ttu-id="67181-107">説明</span><span class="sxs-lookup"><span data-stu-id="67181-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="67181-108">関数の ID。</span><span class="sxs-lookup"><span data-stu-id="67181-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="67181-109">再コンパイルされた関数の ID。</span><span class="sxs-lookup"><span data-stu-id="67181-109">The ID of the recompiled function.</span></span> <span data-ttu-id="67181-110">0 (ゼロ) の値では、関数の元のバージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="67181-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67181-111">コメント</span><span class="sxs-lookup"><span data-stu-id="67181-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67181-112">要件</span><span class="sxs-lookup"><span data-stu-id="67181-112">Requirements</span></span>  
 <span data-ttu-id="67181-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="67181-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67181-114">**ヘッダー:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="67181-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="67181-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67181-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67181-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67181-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67181-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="67181-117">See Also</span></span>  
 [<span data-ttu-id="67181-118">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="67181-118">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)

---
title: "COR_PRF_CLAUSE_TYPE 列挙型"
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
- COR_PRF_CLAUSE_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CLAUSE_TYPE
helpviewer_keywords:
- COR_PRF_CLAUSE_TYPE enumeration [.NET Framework profiling]
ms.assetid: f64c325a-ed3a-4aaf-b847-a88edbc4fefc
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e03b3f2462b8876bfba3cf7d0df40311935722f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corprfclausetype-enumeration"></a><span data-ttu-id="c5243-102">COR_PRF_CLAUSE_TYPE 列挙型</span><span class="sxs-lookup"><span data-stu-id="c5243-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="c5243-103">コードが入った、または出た例外句のタイプを示します。</span><span class="sxs-lookup"><span data-stu-id="c5243-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5243-104">構文</span><span class="sxs-lookup"><span data-stu-id="c5243-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="c5243-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="c5243-105">Members</span></span>  
  
|<span data-ttu-id="c5243-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="c5243-106">Member</span></span>|<span data-ttu-id="c5243-107">説明</span><span class="sxs-lookup"><span data-stu-id="c5243-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="c5243-108">例外句が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="c5243-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="c5243-109">例外句は、フィルター式です。</span><span class="sxs-lookup"><span data-stu-id="c5243-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="c5243-110">例外句は、`catch`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="c5243-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="c5243-111">例外句は、`finally`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="c5243-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c5243-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="c5243-112">Requirements</span></span>  
 <span data-ttu-id="c5243-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c5243-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5243-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c5243-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c5243-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5243-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5243-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5243-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5243-117">参照</span><span class="sxs-lookup"><span data-stu-id="c5243-117">See Also</span></span>  
 [<span data-ttu-id="c5243-118">列挙型のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="c5243-118">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)

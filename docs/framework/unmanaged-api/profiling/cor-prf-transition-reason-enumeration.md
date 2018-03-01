---
title: "COR_PRF_TRANSITION_REASON 列挙型"
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
- COR_PRF_TRANSITION_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_TRANSITION_REASON
helpviewer_keywords:
- COR_PRF_TRANSITION_REASON enumeration [.NET Framework profiling]
ms.assetid: da941118-01b7-4197-ae5b-9f2f8adcd623
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 498abc57e35946b2b0c8bf08cdd768bd7039c9f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corprftransitionreason-enumeration"></a><span data-ttu-id="5fefe-102">COR_PRF_TRANSITION_REASON 列挙型</span><span class="sxs-lookup"><span data-stu-id="5fefe-102">COR_PRF_TRANSITION_REASON Enumeration</span></span>
<span data-ttu-id="5fefe-103">マネージ コードからアンマネージ コードへ、またはその逆の遷移の理由を示します。</span><span class="sxs-lookup"><span data-stu-id="5fefe-103">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fefe-104">構文</span><span class="sxs-lookup"><span data-stu-id="5fefe-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="5fefe-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="5fefe-105">Members</span></span>  
  
|<span data-ttu-id="5fefe-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="5fefe-106">Member</span></span>|<span data-ttu-id="5fefe-107">説明</span><span class="sxs-lookup"><span data-stu-id="5fefe-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="5fefe-108">移行では、関数を呼び出すのためです。</span><span class="sxs-lookup"><span data-stu-id="5fefe-108">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="5fefe-109">移行では、関数から返されるのためです。</span><span class="sxs-lookup"><span data-stu-id="5fefe-109">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fefe-110">コメント</span><span class="sxs-lookup"><span data-stu-id="5fefe-110">Remarks</span></span>  
 <span data-ttu-id="5fefe-111">プロファイラーを受け取る遷移が発生すると、 [icorprofilercallback::managedtounmanagedtransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)または[icorprofilercallback::unmanagedtomanagedtransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)コールバック、うちいずれか値を提供、`COR_PRF_TRANSITION_REASON`遷移の理由を示す列挙体です。</span><span class="sxs-lookup"><span data-stu-id="5fefe-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fefe-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="5fefe-112">Requirements</span></span>  
 <span data-ttu-id="5fefe-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5fefe-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fefe-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5fefe-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5fefe-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fefe-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fefe-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fefe-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

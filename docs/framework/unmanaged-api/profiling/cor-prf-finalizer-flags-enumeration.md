---
title: "COR_PRF_FINALIZER_FLAGS 列挙型"
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
- COR_PRF_FINALIZER_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FINALIZER_FLAGS
helpviewer_keywords:
- COR_PRF_FINALIZER_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 297d7721-3911-4f36-9e34-d9da0c33e22a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ae0941e962b2fc1b08f0defb692038bd5fcf885a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corprffinalizerflags-enumeration"></a><span data-ttu-id="23e92-102">COR_PRF_FINALIZER_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="23e92-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="23e92-103">オブジェクトのファイナライザーを記述します。</span><span class="sxs-lookup"><span data-stu-id="23e92-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23e92-104">構文</span><span class="sxs-lookup"><span data-stu-id="23e92-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="23e92-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="23e92-105">Members</span></span>  
  
|<span data-ttu-id="23e92-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="23e92-106">Member</span></span>|<span data-ttu-id="23e92-107">説明</span><span class="sxs-lookup"><span data-stu-id="23e92-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="23e92-108">ファイナライザーが重要です。</span><span class="sxs-lookup"><span data-stu-id="23e92-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23e92-109">コメント</span><span class="sxs-lookup"><span data-stu-id="23e92-109">Remarks</span></span>  
 <span data-ttu-id="23e92-110">`COR_PRF_FINALIZER_FLAGS`列挙型を使用して、 [icorprofilercallback 2::finalizeableobjectqueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)オブジェクトのファイナライザーを記述するメソッド。</span><span class="sxs-lookup"><span data-stu-id="23e92-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23e92-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="23e92-111">Requirements</span></span>  
 <span data-ttu-id="23e92-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="23e92-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23e92-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="23e92-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="23e92-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23e92-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23e92-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23e92-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23e92-116">参照</span><span class="sxs-lookup"><span data-stu-id="23e92-116">See Also</span></span>  
 [<span data-ttu-id="23e92-117">列挙型のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="23e92-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)

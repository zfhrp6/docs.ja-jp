---
title: "COR_DEBUG_STEP_RANGE 構造体"
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
- COR_DEBUG_STEP_RANGE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_STEP_RANGE
helpviewer_keywords:
- COR_DEBUG_STEP_RANGE structure [.NET Framework debugging]
ms.assetid: 8809d00e-beaa-4dcf-b4e8-e89d0a5406b7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 27b1b7b26ea788683f9b322306c55a4b3945f342
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugsteprange-structure"></a><span data-ttu-id="c9a32-102">COR_DEBUG_STEP_RANGE 構造体</span><span class="sxs-lookup"><span data-stu-id="c9a32-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="c9a32-103">コードの範囲に関するオフセット情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c9a32-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="c9a32-104">この構造体を使って、 [icordebugstepper::steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="c9a32-104">This structure is used by the [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9a32-105">構文</span><span class="sxs-lookup"><span data-stu-id="c9a32-105">Syntax</span></span>  
  
```  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="c9a32-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="c9a32-106">Members</span></span>  
  
|<span data-ttu-id="c9a32-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="c9a32-107">Member</span></span>|<span data-ttu-id="c9a32-108">説明</span><span class="sxs-lookup"><span data-stu-id="c9a32-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="c9a32-109">範囲の先頭のオフセット。</span><span class="sxs-lookup"><span data-stu-id="c9a32-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="c9a32-110">範囲の最後のオフセット。</span><span class="sxs-lookup"><span data-stu-id="c9a32-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9a32-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="c9a32-111">Requirements</span></span>  
 <span data-ttu-id="c9a32-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c9a32-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9a32-113">**ヘッダー:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="c9a32-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="c9a32-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9a32-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9a32-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9a32-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9a32-116">参照</span><span class="sxs-lookup"><span data-stu-id="c9a32-116">See Also</span></span>  
 [<span data-ttu-id="c9a32-117">StepRange メソッド</span><span class="sxs-lookup"><span data-stu-id="c9a32-117">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)  
 [<span data-ttu-id="c9a32-118">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="c9a32-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="c9a32-119">デバッグ</span><span class="sxs-lookup"><span data-stu-id="c9a32-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

---
title: ICorDebugEnum Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum
helpviewer_keywords:
- ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 80be7efe-2c32-4b9f-8c52-40c6f6268219
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4659bbc9c2e3c71a6cf85e51a06bee4f789356b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422306"
---
# <a name="icordebugenum-interface1"></a><span data-ttu-id="771ae-102">ICorDebugEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="771ae-102">ICorDebugEnum Interface1</span></span>
<span data-ttu-id="771ae-103">デバッグのアプリケーションによって使用されている列挙子の抽象基本インターフェイスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="771ae-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="771ae-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="771ae-104">Methods</span></span>  
  
|<span data-ttu-id="771ae-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="771ae-105">Method</span></span>|<span data-ttu-id="771ae-106">説明</span><span class="sxs-lookup"><span data-stu-id="771ae-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="771ae-107">Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="771ae-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="771ae-108">このコピーを作成`ICorDebugEnum`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="771ae-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="771ae-109">GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="771ae-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="771ae-110">列挙に含まれる項目の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="771ae-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="771ae-111">Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="771ae-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="771ae-112">列挙体の先頭にカーソルを移動します。</span><span class="sxs-lookup"><span data-stu-id="771ae-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="771ae-113">Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="771ae-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="771ae-114">列挙体の指定数の項目でカーソルを前方に移動します。</span><span class="sxs-lookup"><span data-stu-id="771ae-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="771ae-115">コメント</span><span class="sxs-lookup"><span data-stu-id="771ae-115">Remarks</span></span>  
 <span data-ttu-id="771ae-116">次の列挙子から派生して`ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="771ae-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
-   <span data-ttu-id="771ae-117">"ICorDebugAppDomainEnum"</span><span class="sxs-lookup"><span data-stu-id="771ae-117">"ICorDebugAppDomainEnum"</span></span>  
  
-   <span data-ttu-id="771ae-118">"ICorDebugAssemblyEnum"</span><span class="sxs-lookup"><span data-stu-id="771ae-118">"ICorDebugAssemblyEnum"</span></span>  
  
-   [<span data-ttu-id="771ae-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="771ae-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
-   <span data-ttu-id="771ae-120">"ICorDebugBreakpointEnum"</span><span class="sxs-lookup"><span data-stu-id="771ae-120">"ICorDebugBreakpointEnum"</span></span>  
  
-   <span data-ttu-id="771ae-121">"ICorDebugChainEnum"</span><span class="sxs-lookup"><span data-stu-id="771ae-121">"ICorDebugChainEnum"</span></span>  
  
-   <span data-ttu-id="771ae-122">"ICorDebugCodeEnum"</span><span class="sxs-lookup"><span data-stu-id="771ae-122">"ICorDebugCodeEnum"</span></span>  
  
-   <span data-ttu-id="771ae-123">"ICorDebugErrorInfoEnum"</span><span class="sxs-lookup"><span data-stu-id="771ae-123">"ICorDebugErrorInfoEnum"</span></span>  
  
-   [<span data-ttu-id="771ae-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="771ae-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
-   <span data-ttu-id="771ae-125">"ICorDebugFrameEnum"</span><span class="sxs-lookup"><span data-stu-id="771ae-125">"ICorDebugFrameEnum"</span></span>  
  
-   [<span data-ttu-id="771ae-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="771ae-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
-   [<span data-ttu-id="771ae-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="771ae-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
-   [<span data-ttu-id="771ae-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="771ae-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
-   [<span data-ttu-id="771ae-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="771ae-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
-   <span data-ttu-id="771ae-130">"ICorDebugModuleEnum"</span><span class="sxs-lookup"><span data-stu-id="771ae-130">"ICorDebugModuleEnum"</span></span>  
  
-   <span data-ttu-id="771ae-131">"ICorDebugObjectEnum"</span><span class="sxs-lookup"><span data-stu-id="771ae-131">"ICorDebugObjectEnum"</span></span>  
  
-   <span data-ttu-id="771ae-132">"ICorDebugProcessEnum"</span><span class="sxs-lookup"><span data-stu-id="771ae-132">"ICorDebugProcessEnum"</span></span>  
  
-   <span data-ttu-id="771ae-133">"ICorDebugStepperEnum"</span><span class="sxs-lookup"><span data-stu-id="771ae-133">"ICorDebugStepperEnum"</span></span>  
  
-   <span data-ttu-id="771ae-134">"ICorDebugThreadEnum"</span><span class="sxs-lookup"><span data-stu-id="771ae-134">"ICorDebugThreadEnum"</span></span>  
  
-   <span data-ttu-id="771ae-135">"ICorDebugTypeEnum"</span><span class="sxs-lookup"><span data-stu-id="771ae-135">"ICorDebugTypeEnum"</span></span>  
  
-   <span data-ttu-id="771ae-136">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="771ae-136">"ICorDebugValueEnum"</span></span>  
  
-   [<span data-ttu-id="771ae-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="771ae-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="771ae-138">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="771ae-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="771ae-139">要件</span><span class="sxs-lookup"><span data-stu-id="771ae-139">Requirements</span></span>  
 <span data-ttu-id="771ae-140">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="771ae-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="771ae-141">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="771ae-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="771ae-142">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="771ae-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="771ae-143">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="771ae-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="771ae-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="771ae-144">See Also</span></span>  
 [<span data-ttu-id="771ae-145">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="771ae-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

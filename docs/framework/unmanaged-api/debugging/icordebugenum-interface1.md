---
title: ICorDebugEnum Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEnum
helpviewer_keywords: ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 80be7efe-2c32-4b9f-8c52-40c6f6268219
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 751cca87962473501ef29a4deb99d9d24be33396
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugenum-interface1"></a><span data-ttu-id="55925-102">ICorDebugEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="55925-102">ICorDebugEnum Interface1</span></span>
<span data-ttu-id="55925-103">デバッグのアプリケーションによって使用されている列挙子の抽象基本インターフェイスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="55925-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="55925-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="55925-104">Methods</span></span>  
  
|<span data-ttu-id="55925-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="55925-105">Method</span></span>|<span data-ttu-id="55925-106">説明</span><span class="sxs-lookup"><span data-stu-id="55925-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="55925-107">Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="55925-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="55925-108">このコピーを作成`ICorDebugEnum`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="55925-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="55925-109">GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="55925-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="55925-110">列挙に含まれる項目の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="55925-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="55925-111">Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="55925-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="55925-112">列挙体の先頭にカーソルを移動します。</span><span class="sxs-lookup"><span data-stu-id="55925-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="55925-113">Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="55925-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="55925-114">列挙体の指定数の項目でカーソルを前方に移動します。</span><span class="sxs-lookup"><span data-stu-id="55925-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55925-115">コメント</span><span class="sxs-lookup"><span data-stu-id="55925-115">Remarks</span></span>  
 <span data-ttu-id="55925-116">次の列挙子から派生して`ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="55925-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
-   <span data-ttu-id="55925-117">"ICorDebugAppDomainEnum"</span><span class="sxs-lookup"><span data-stu-id="55925-117">"ICorDebugAppDomainEnum"</span></span>  
  
-   <span data-ttu-id="55925-118">"ICorDebugAssemblyEnum"</span><span class="sxs-lookup"><span data-stu-id="55925-118">"ICorDebugAssemblyEnum"</span></span>  
  
-   [<span data-ttu-id="55925-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="55925-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
-   <span data-ttu-id="55925-120">"ICorDebugBreakpointEnum"</span><span class="sxs-lookup"><span data-stu-id="55925-120">"ICorDebugBreakpointEnum"</span></span>  
  
-   <span data-ttu-id="55925-121">"ICorDebugChainEnum"</span><span class="sxs-lookup"><span data-stu-id="55925-121">"ICorDebugChainEnum"</span></span>  
  
-   <span data-ttu-id="55925-122">"ICorDebugCodeEnum"</span><span class="sxs-lookup"><span data-stu-id="55925-122">"ICorDebugCodeEnum"</span></span>  
  
-   <span data-ttu-id="55925-123">"ICorDebugErrorInfoEnum"</span><span class="sxs-lookup"><span data-stu-id="55925-123">"ICorDebugErrorInfoEnum"</span></span>  
  
-   [<span data-ttu-id="55925-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="55925-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
-   <span data-ttu-id="55925-125">"ICorDebugFrameEnum"</span><span class="sxs-lookup"><span data-stu-id="55925-125">"ICorDebugFrameEnum"</span></span>  
  
-   [<span data-ttu-id="55925-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="55925-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
-   [<span data-ttu-id="55925-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="55925-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
-   [<span data-ttu-id="55925-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="55925-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
-   [<span data-ttu-id="55925-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="55925-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
-   <span data-ttu-id="55925-130">"ICorDebugModuleEnum"</span><span class="sxs-lookup"><span data-stu-id="55925-130">"ICorDebugModuleEnum"</span></span>  
  
-   <span data-ttu-id="55925-131">"ICorDebugObjectEnum"</span><span class="sxs-lookup"><span data-stu-id="55925-131">"ICorDebugObjectEnum"</span></span>  
  
-   <span data-ttu-id="55925-132">"ICorDebugProcessEnum"</span><span class="sxs-lookup"><span data-stu-id="55925-132">"ICorDebugProcessEnum"</span></span>  
  
-   <span data-ttu-id="55925-133">"ICorDebugStepperEnum"</span><span class="sxs-lookup"><span data-stu-id="55925-133">"ICorDebugStepperEnum"</span></span>  
  
-   <span data-ttu-id="55925-134">"ICorDebugThreadEnum"</span><span class="sxs-lookup"><span data-stu-id="55925-134">"ICorDebugThreadEnum"</span></span>  
  
-   <span data-ttu-id="55925-135">"ICorDebugTypeEnum"</span><span class="sxs-lookup"><span data-stu-id="55925-135">"ICorDebugTypeEnum"</span></span>  
  
-   <span data-ttu-id="55925-136">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="55925-136">"ICorDebugValueEnum"</span></span>  
  
-   [<span data-ttu-id="55925-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="55925-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="55925-138">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="55925-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55925-139">必要条件</span><span class="sxs-lookup"><span data-stu-id="55925-139">Requirements</span></span>  
 <span data-ttu-id="55925-140">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="55925-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55925-141">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55925-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55925-142">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55925-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55925-143">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55925-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55925-144">参照</span><span class="sxs-lookup"><span data-stu-id="55925-144">See Also</span></span>  
 [<span data-ttu-id="55925-145">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="55925-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

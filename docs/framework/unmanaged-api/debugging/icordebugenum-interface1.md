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
ms.openlocfilehash: 7f6596918819294f0ab68735cec12f9eab8bf83e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugenum-interface1"></a><span data-ttu-id="e1098-102">ICorDebugEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="e1098-102">ICorDebugEnum Interface1</span></span>
<span data-ttu-id="e1098-103">デバッグのアプリケーションによって使用されている列挙子の抽象基本インターフェイスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="e1098-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e1098-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="e1098-104">Methods</span></span>  
  
|<span data-ttu-id="e1098-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e1098-105">Method</span></span>|<span data-ttu-id="e1098-106">説明</span><span class="sxs-lookup"><span data-stu-id="e1098-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e1098-107">Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="e1098-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="e1098-108">このコピーを作成`ICorDebugEnum`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e1098-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="e1098-109">GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="e1098-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="e1098-110">列挙に含まれる項目の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="e1098-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="e1098-111">Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="e1098-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="e1098-112">列挙体の先頭にカーソルを移動します。</span><span class="sxs-lookup"><span data-stu-id="e1098-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="e1098-113">Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="e1098-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="e1098-114">列挙体の指定数の項目でカーソルを前方に移動します。</span><span class="sxs-lookup"><span data-stu-id="e1098-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1098-115">コメント</span><span class="sxs-lookup"><span data-stu-id="e1098-115">Remarks</span></span>  
 <span data-ttu-id="e1098-116">次の列挙子から派生して`ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="e1098-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
-   <span data-ttu-id="e1098-117">"ICorDebugAppDomainEnum"</span><span class="sxs-lookup"><span data-stu-id="e1098-117">"ICorDebugAppDomainEnum"</span></span>  
  
-   <span data-ttu-id="e1098-118">"ICorDebugAssemblyEnum"</span><span class="sxs-lookup"><span data-stu-id="e1098-118">"ICorDebugAssemblyEnum"</span></span>  
  
-   [<span data-ttu-id="e1098-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="e1098-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
-   <span data-ttu-id="e1098-120">"ICorDebugBreakpointEnum"</span><span class="sxs-lookup"><span data-stu-id="e1098-120">"ICorDebugBreakpointEnum"</span></span>  
  
-   <span data-ttu-id="e1098-121">"ICorDebugChainEnum"</span><span class="sxs-lookup"><span data-stu-id="e1098-121">"ICorDebugChainEnum"</span></span>  
  
-   <span data-ttu-id="e1098-122">"ICorDebugCodeEnum"</span><span class="sxs-lookup"><span data-stu-id="e1098-122">"ICorDebugCodeEnum"</span></span>  
  
-   <span data-ttu-id="e1098-123">"ICorDebugErrorInfoEnum"</span><span class="sxs-lookup"><span data-stu-id="e1098-123">"ICorDebugErrorInfoEnum"</span></span>  
  
-   [<span data-ttu-id="e1098-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="e1098-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
-   <span data-ttu-id="e1098-125">"ICorDebugFrameEnum"</span><span class="sxs-lookup"><span data-stu-id="e1098-125">"ICorDebugFrameEnum"</span></span>  
  
-   [<span data-ttu-id="e1098-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="e1098-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
-   [<span data-ttu-id="e1098-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="e1098-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
-   [<span data-ttu-id="e1098-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="e1098-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
-   [<span data-ttu-id="e1098-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="e1098-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
-   <span data-ttu-id="e1098-130">"ICorDebugModuleEnum"</span><span class="sxs-lookup"><span data-stu-id="e1098-130">"ICorDebugModuleEnum"</span></span>  
  
-   <span data-ttu-id="e1098-131">"ICorDebugObjectEnum"</span><span class="sxs-lookup"><span data-stu-id="e1098-131">"ICorDebugObjectEnum"</span></span>  
  
-   <span data-ttu-id="e1098-132">"ICorDebugProcessEnum"</span><span class="sxs-lookup"><span data-stu-id="e1098-132">"ICorDebugProcessEnum"</span></span>  
  
-   <span data-ttu-id="e1098-133">"ICorDebugStepperEnum"</span><span class="sxs-lookup"><span data-stu-id="e1098-133">"ICorDebugStepperEnum"</span></span>  
  
-   <span data-ttu-id="e1098-134">"ICorDebugThreadEnum"</span><span class="sxs-lookup"><span data-stu-id="e1098-134">"ICorDebugThreadEnum"</span></span>  
  
-   <span data-ttu-id="e1098-135">"ICorDebugTypeEnum"</span><span class="sxs-lookup"><span data-stu-id="e1098-135">"ICorDebugTypeEnum"</span></span>  
  
-   <span data-ttu-id="e1098-136">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="e1098-136">"ICorDebugValueEnum"</span></span>  
  
-   [<span data-ttu-id="e1098-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="e1098-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="e1098-138">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e1098-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1098-139">要件</span><span class="sxs-lookup"><span data-stu-id="e1098-139">Requirements</span></span>  
 <span data-ttu-id="e1098-140">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e1098-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1098-141">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1098-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1098-142">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1098-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1098-143">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1098-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1098-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1098-144">See Also</span></span>  
 [<span data-ttu-id="e1098-145">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e1098-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

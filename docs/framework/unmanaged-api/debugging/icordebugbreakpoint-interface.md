---
title: ICorDebugBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBreakpoint
helpviewer_keywords: ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b78b61b99fb8f236e787f3acbf993d0a1c57e797
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugbreakpoint-interface1"></a><span data-ttu-id="57675-102">ICorDebugBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="57675-102">ICorDebugBreakpoint Interface1</span></span>
<span data-ttu-id="57675-103">関数、または値のウォッチ ポイントでのブレークポイントを表します。</span><span class="sxs-lookup"><span data-stu-id="57675-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="57675-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="57675-104">Methods</span></span>  
  
|<span data-ttu-id="57675-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="57675-105">Method</span></span>|<span data-ttu-id="57675-106">説明</span><span class="sxs-lookup"><span data-stu-id="57675-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="57675-107">Activate メソッド</span><span class="sxs-lookup"><span data-stu-id="57675-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="57675-108">これのアクティブな状態を設定`ICorDebugBreakpoint`です。</span><span class="sxs-lookup"><span data-stu-id="57675-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="57675-109">IsActive メソッド</span><span class="sxs-lookup"><span data-stu-id="57675-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="57675-110">示す値を取得するかどうかこの`ICorDebugBreakpoint`がアクティブです。</span><span class="sxs-lookup"><span data-stu-id="57675-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57675-111">コメント</span><span class="sxs-lookup"><span data-stu-id="57675-111">Remarks</span></span>  
 <span data-ttu-id="57675-112">ブレークポイントでは、条件式は直接サポートしていません。</span><span class="sxs-lookup"><span data-stu-id="57675-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="57675-113">デバッガーがの上にそれを実装する必要がありますこのような機能を使用する場合は、`ICorDebugBreakpoint`です。</span><span class="sxs-lookup"><span data-stu-id="57675-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="57675-114">ICorDebugFunctionBreakpoint インターフェイスを拡張`ICorDebugBreakpoint`関数内のブレークポイントをサポートするためにします。</span><span class="sxs-lookup"><span data-stu-id="57675-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57675-115">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="57675-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57675-116">要件</span><span class="sxs-lookup"><span data-stu-id="57675-116">Requirements</span></span>  
 <span data-ttu-id="57675-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="57675-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57675-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="57675-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57675-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57675-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57675-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57675-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57675-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="57675-121">See Also</span></span>  
 [<span data-ttu-id="57675-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="57675-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: ICorDebugFunctionBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunctionBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunctionBreakpoint
helpviewer_keywords: ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 9c149303-14b1-4138-83d7-e8c3e0fcd332
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 910317bea8af3a80ee66544651de2372808734bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunctionbreakpoint-interface1"></a><span data-ttu-id="4d15a-102">ICorDebugFunctionBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="4d15a-102">ICorDebugFunctionBreakpoint Interface1</span></span>
<span data-ttu-id="4d15a-103">ICorDebugBreakpoint インターフェイス関数内のブレークポイントをサポートするために拡張します。</span><span class="sxs-lookup"><span data-stu-id="4d15a-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d15a-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="4d15a-104">Methods</span></span>  
  
|<span data-ttu-id="4d15a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="4d15a-105">Method</span></span>|<span data-ttu-id="4d15a-106">説明</span><span class="sxs-lookup"><span data-stu-id="4d15a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d15a-107">GetFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="4d15a-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="4d15a-108">ブレークポイントが設定されている関数を参照する ICorDebugFunction へのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="4d15a-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="4d15a-109">GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="4d15a-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="4d15a-110">関数内のブレークポイントのオフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="4d15a-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d15a-111">コメント</span><span class="sxs-lookup"><span data-stu-id="4d15a-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d15a-112">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="4d15a-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d15a-113">要件</span><span class="sxs-lookup"><span data-stu-id="4d15a-113">Requirements</span></span>  
 <span data-ttu-id="4d15a-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4d15a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d15a-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d15a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d15a-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d15a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d15a-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d15a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d15a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d15a-118">See Also</span></span>  
 [<span data-ttu-id="4d15a-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="4d15a-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

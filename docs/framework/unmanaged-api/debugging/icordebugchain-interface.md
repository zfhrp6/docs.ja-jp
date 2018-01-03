---
title: ICorDebugChain Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain
helpviewer_keywords: ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6000f6d91b3fe2325868b9af58740e1c4cd76127
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchain-interface1"></a><span data-ttu-id="40709-102">ICorDebugChain Interface1</span><span class="sxs-lookup"><span data-stu-id="40709-102">ICorDebugChain Interface1</span></span>
<span data-ttu-id="40709-103">物理呼び出し履歴または論理呼び出し履歴のセグメントを表します。</span><span class="sxs-lookup"><span data-stu-id="40709-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="40709-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="40709-104">Methods</span></span>  
  
|<span data-ttu-id="40709-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="40709-105">Method</span></span>|<span data-ttu-id="40709-106">説明</span><span class="sxs-lookup"><span data-stu-id="40709-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="40709-107">EnumerateFrames メソッド</span><span class="sxs-lookup"><span data-stu-id="40709-107">EnumerateFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|<span data-ttu-id="40709-108">最新のフレームを使用して開始する、チェーン内のすべてのマネージ スタック フレームを含む列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="40709-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="40709-109">GetActiveFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="40709-109">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|<span data-ttu-id="40709-110">アクティブなを取得 (つまり、最新) のフレーム チェーンをします。</span><span class="sxs-lookup"><span data-stu-id="40709-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="40709-111">GetCallee メソッド</span><span class="sxs-lookup"><span data-stu-id="40709-111">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|<span data-ttu-id="40709-112">このチェーンによって呼び出されたチェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="40709-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="40709-113">GetCaller メソッド</span><span class="sxs-lookup"><span data-stu-id="40709-113">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|<span data-ttu-id="40709-114">このチェーンと呼ばれる、チェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="40709-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="40709-115">GetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="40709-115">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|<span data-ttu-id="40709-116">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="40709-116">Not implemented.</span></span>|  
|[<span data-ttu-id="40709-117">GetNext メソッド</span><span class="sxs-lookup"><span data-stu-id="40709-117">GetNext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|<span data-ttu-id="40709-118">スレッドの次のフレーム チェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="40709-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="40709-119">GetPrevious メソッド</span><span class="sxs-lookup"><span data-stu-id="40709-119">GetPrevious Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|<span data-ttu-id="40709-120">スレッドの前のフレーム チェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="40709-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="40709-121">GetReason メソッド</span><span class="sxs-lookup"><span data-stu-id="40709-121">GetReason Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|<span data-ttu-id="40709-122">この呼び出しチェーンの生成の理由を取得します。</span><span class="sxs-lookup"><span data-stu-id="40709-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="40709-123">GetRegisterSet メソッド</span><span class="sxs-lookup"><span data-stu-id="40709-123">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|<span data-ttu-id="40709-124">このチェーンのアクティブな部分のレジスタ セットを取得します。</span><span class="sxs-lookup"><span data-stu-id="40709-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="40709-125">GetStackRange メソッド</span><span class="sxs-lookup"><span data-stu-id="40709-125">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|<span data-ttu-id="40709-126">このチェーンのスタック セグメントのアドレス範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="40709-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="40709-127">GetThread メソッド</span><span class="sxs-lookup"><span data-stu-id="40709-127">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|<span data-ttu-id="40709-128">この呼び出しチェーンが物理スレッドの一部を取得します。</span><span class="sxs-lookup"><span data-stu-id="40709-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="40709-129">IsManaged メソッド</span><span class="sxs-lookup"><span data-stu-id="40709-129">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|<span data-ttu-id="40709-130">このチェーンがマネージ コードを実行しているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="40709-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40709-131">コメント</span><span class="sxs-lookup"><span data-stu-id="40709-131">Remarks</span></span>  
 <span data-ttu-id="40709-132">チェーン内のスタック フレームは、連続したスタック領域を占有し、同じスレッドとコンテキストを共有します。</span><span class="sxs-lookup"><span data-stu-id="40709-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="40709-133">チェーンには、いずれかのマネージまたはアンマネージ コードのチェーンを表すことがあります。</span><span class="sxs-lookup"><span data-stu-id="40709-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="40709-134">空`ICorDebugChain`インスタンスは、アンマネージ コードのチェーンを表します。</span><span class="sxs-lookup"><span data-stu-id="40709-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40709-135">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="40709-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40709-136">必要条件</span><span class="sxs-lookup"><span data-stu-id="40709-136">Requirements</span></span>  
 <span data-ttu-id="40709-137">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="40709-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40709-138">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="40709-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40709-139">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40709-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40709-140">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40709-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40709-141">参照</span><span class="sxs-lookup"><span data-stu-id="40709-141">See Also</span></span>  
 [<span data-ttu-id="40709-142">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="40709-142">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

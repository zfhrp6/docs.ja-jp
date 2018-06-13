---
title: ICorDebugChain Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain
helpviewer_keywords:
- ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32889a8e8867fc42b48413463095dda423f26b85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409842"
---
# <a name="icordebugchain-interface1"></a><span data-ttu-id="f81ea-102">ICorDebugChain Interface1</span><span class="sxs-lookup"><span data-stu-id="f81ea-102">ICorDebugChain Interface1</span></span>
<span data-ttu-id="f81ea-103">物理呼び出し履歴または論理呼び出し履歴のセグメントを表します。</span><span class="sxs-lookup"><span data-stu-id="f81ea-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f81ea-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="f81ea-104">Methods</span></span>  
  
|<span data-ttu-id="f81ea-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f81ea-105">Method</span></span>|<span data-ttu-id="f81ea-106">説明</span><span class="sxs-lookup"><span data-stu-id="f81ea-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f81ea-107">EnumerateFrames メソッド</span><span class="sxs-lookup"><span data-stu-id="f81ea-107">EnumerateFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|<span data-ttu-id="f81ea-108">最新のフレームを使用して開始する、チェーン内のすべてのマネージ スタック フレームを含む列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="f81ea-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="f81ea-109">GetActiveFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="f81ea-109">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|<span data-ttu-id="f81ea-110">アクティブなを取得 (つまり、最新) のフレーム チェーンをします。</span><span class="sxs-lookup"><span data-stu-id="f81ea-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="f81ea-111">GetCallee メソッド</span><span class="sxs-lookup"><span data-stu-id="f81ea-111">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|<span data-ttu-id="f81ea-112">このチェーンによって呼び出されたチェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="f81ea-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="f81ea-113">GetCaller メソッド</span><span class="sxs-lookup"><span data-stu-id="f81ea-113">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|<span data-ttu-id="f81ea-114">このチェーンと呼ばれる、チェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="f81ea-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="f81ea-115">GetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="f81ea-115">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|<span data-ttu-id="f81ea-116">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="f81ea-116">Not implemented.</span></span>|  
|[<span data-ttu-id="f81ea-117">GetNext メソッド</span><span class="sxs-lookup"><span data-stu-id="f81ea-117">GetNext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|<span data-ttu-id="f81ea-118">スレッドの次のフレーム チェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="f81ea-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="f81ea-119">GetPrevious メソッド</span><span class="sxs-lookup"><span data-stu-id="f81ea-119">GetPrevious Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|<span data-ttu-id="f81ea-120">スレッドの前のフレーム チェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="f81ea-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="f81ea-121">GetReason メソッド</span><span class="sxs-lookup"><span data-stu-id="f81ea-121">GetReason Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|<span data-ttu-id="f81ea-122">この呼び出しチェーンの生成の理由を取得します。</span><span class="sxs-lookup"><span data-stu-id="f81ea-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="f81ea-123">GetRegisterSet メソッド</span><span class="sxs-lookup"><span data-stu-id="f81ea-123">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|<span data-ttu-id="f81ea-124">このチェーンのアクティブな部分のレジスタ セットを取得します。</span><span class="sxs-lookup"><span data-stu-id="f81ea-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="f81ea-125">GetStackRange メソッド</span><span class="sxs-lookup"><span data-stu-id="f81ea-125">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|<span data-ttu-id="f81ea-126">このチェーンのスタック セグメントのアドレス範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="f81ea-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="f81ea-127">GetThread メソッド</span><span class="sxs-lookup"><span data-stu-id="f81ea-127">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|<span data-ttu-id="f81ea-128">この呼び出しチェーンが物理スレッドの一部を取得します。</span><span class="sxs-lookup"><span data-stu-id="f81ea-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="f81ea-129">IsManaged メソッド</span><span class="sxs-lookup"><span data-stu-id="f81ea-129">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|<span data-ttu-id="f81ea-130">このチェーンがマネージ コードを実行しているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="f81ea-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f81ea-131">コメント</span><span class="sxs-lookup"><span data-stu-id="f81ea-131">Remarks</span></span>  
 <span data-ttu-id="f81ea-132">チェーン内のスタック フレームは、連続したスタック領域を占有し、同じスレッドとコンテキストを共有します。</span><span class="sxs-lookup"><span data-stu-id="f81ea-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="f81ea-133">チェーンには、いずれかのマネージまたはアンマネージ コードのチェーンを表すことがあります。</span><span class="sxs-lookup"><span data-stu-id="f81ea-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="f81ea-134">空`ICorDebugChain`インスタンスは、アンマネージ コードのチェーンを表します。</span><span class="sxs-lookup"><span data-stu-id="f81ea-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f81ea-135">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="f81ea-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f81ea-136">要件</span><span class="sxs-lookup"><span data-stu-id="f81ea-136">Requirements</span></span>  
 <span data-ttu-id="f81ea-137">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f81ea-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f81ea-138">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f81ea-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f81ea-139">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f81ea-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f81ea-140">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f81ea-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f81ea-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="f81ea-141">See Also</span></span>  
 [<span data-ttu-id="f81ea-142">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f81ea-142">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

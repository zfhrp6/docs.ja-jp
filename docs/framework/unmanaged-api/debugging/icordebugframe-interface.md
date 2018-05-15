---
title: ICorDebugFrame Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3d6c1a2bfd66e275b506d4465731c48cd7c6515
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugframe-interface1"></a><span data-ttu-id="4fc99-102">ICorDebugFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="4fc99-102">ICorDebugFrame Interface1</span></span>
<span data-ttu-id="4fc99-103">現在のスタックのフレームを表します。</span><span class="sxs-lookup"><span data-stu-id="4fc99-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4fc99-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="4fc99-104">Methods</span></span>  
  
|<span data-ttu-id="4fc99-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="4fc99-105">Method</span></span>|<span data-ttu-id="4fc99-106">説明</span><span class="sxs-lookup"><span data-stu-id="4fc99-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4fc99-107">CreateStepper メソッド</span><span class="sxs-lookup"><span data-stu-id="4fc99-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="4fc99-108">この基準としたステップ実行の操作を実行する、ICorDebugStepper を取得`ICorDebugFrame`です。</span><span class="sxs-lookup"><span data-stu-id="4fc99-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="4fc99-109">GetCallee メソッド</span><span class="sxs-lookup"><span data-stu-id="4fc99-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="4fc99-110">ポインターを取得、`ICorDebugFrame`このフレームと呼ばれる、またはこの場合、null を返しますが、チェーン内の最も内側のフレームを現在のチェーンにします。</span><span class="sxs-lookup"><span data-stu-id="4fc99-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="4fc99-111">GetCaller メソッド</span><span class="sxs-lookup"><span data-stu-id="4fc99-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="4fc99-112">ポインターを取得、`ICorDebugFrame`このフレームと呼ばれる現在のチェーン内またはチェーン内の最も外側のフレームは、この場合、null を返します。</span><span class="sxs-lookup"><span data-stu-id="4fc99-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="4fc99-113">GetChain メソッド</span><span class="sxs-lookup"><span data-stu-id="4fc99-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="4fc99-114">これで、ICorDebugChain へのポインターを取得`ICorDebugFrame`の一部です。</span><span class="sxs-lookup"><span data-stu-id="4fc99-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="4fc99-115">GetCode メソッド</span><span class="sxs-lookup"><span data-stu-id="4fc99-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="4fc99-116">このスタック フレームに関連付けられている ICorDebugCode へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="4fc99-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="4fc99-117">GetFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="4fc99-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="4fc99-118">このスタック フレームに関連付けられているコードを含む ICorDebugFunction へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="4fc99-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="4fc99-119">GetFunctionToken メソッド</span><span class="sxs-lookup"><span data-stu-id="4fc99-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="4fc99-120">このスタック フレームに関連付けられているコードを含む関数のメタデータ トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="4fc99-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="4fc99-121">GetStackRange メソッド</span><span class="sxs-lookup"><span data-stu-id="4fc99-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="4fc99-122">これによって表されるスタック フレームの絶対アドレス範囲を取得`ICorDebugFrame`です。</span><span class="sxs-lookup"><span data-stu-id="4fc99-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fc99-123">コメント</span><span class="sxs-lookup"><span data-stu-id="4fc99-123">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4fc99-124">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="4fc99-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fc99-125">要件</span><span class="sxs-lookup"><span data-stu-id="4fc99-125">Requirements</span></span>  
 <span data-ttu-id="4fc99-126">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4fc99-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fc99-127">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4fc99-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4fc99-128">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fc99-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fc99-129">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fc99-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fc99-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="4fc99-130">See Also</span></span>  
 [<span data-ttu-id="4fc99-131">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4fc99-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

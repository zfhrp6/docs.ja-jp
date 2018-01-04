---
title: "ICorDebugVirtualUnwinder インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 936df5c3d913a2ee5a1648906fb3ece2751d8ef5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="f4348-102">ICorDebugVirtualUnwinder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4348-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="f4348-103">スタック アンワインドを支援するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f4348-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f4348-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="f4348-104">Methods</span></span>  
  
|<span data-ttu-id="f4348-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f4348-105">Method</span></span>|<span data-ttu-id="f4348-106">name</span><span class="sxs-lookup"><span data-stu-id="f4348-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="f4348-107">GetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="f4348-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="f4348-108">このアンワインダーの現在のコンテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="f4348-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="f4348-109">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="f4348-109">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="f4348-110">呼び出し元のコンテキストに進みます。</span><span class="sxs-lookup"><span data-stu-id="f4348-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4348-111">コメント</span><span class="sxs-lookup"><span data-stu-id="f4348-111">Remarks</span></span>  
 <span data-ttu-id="f4348-112">スタック アンワインドを支援するため、`ICorDebugVirtualUnwinder` インターフェイスのメンバーがデバッガーにより実装されます。</span><span class="sxs-lookup"><span data-stu-id="f4348-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4348-113">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="f4348-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="f4348-114">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="f4348-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4348-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="f4348-115">Requirements</span></span>  
 <span data-ttu-id="f4348-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f4348-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4348-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4348-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4348-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4348-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4348-119">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4348-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4348-120">参照</span><span class="sxs-lookup"><span data-stu-id="f4348-120">See Also</span></span>  
 [<span data-ttu-id="f4348-121">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4348-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f4348-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="f4348-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

---
title: "ICorDebugMemoryBuffer インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98703b07f6601307b5f26aa14b2faf67f8823be5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="96ea1-102">ICorDebugMemoryBuffer インターフェイス</span><span class="sxs-lookup"><span data-stu-id="96ea1-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="96ea1-103">メモリ内のバッファーを表します。</span><span class="sxs-lookup"><span data-stu-id="96ea1-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="96ea1-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="96ea1-104">Methods</span></span>  
  
|<span data-ttu-id="96ea1-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="96ea1-105">Method</span></span>|<span data-ttu-id="96ea1-106">説明</span><span class="sxs-lookup"><span data-stu-id="96ea1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="96ea1-107">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="96ea1-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="96ea1-108">メモリ バッファーのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="96ea1-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="96ea1-109">GetStartAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="96ea1-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="96ea1-110">メモリ バッファーの開始アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="96ea1-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96ea1-111">コメント</span><span class="sxs-lookup"><span data-stu-id="96ea1-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96ea1-112">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="96ea1-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="96ea1-113">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="96ea1-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96ea1-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="96ea1-114">Requirements</span></span>  
 <span data-ttu-id="96ea1-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="96ea1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96ea1-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96ea1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96ea1-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96ea1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96ea1-118">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96ea1-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96ea1-119">参照</span><span class="sxs-lookup"><span data-stu-id="96ea1-119">See Also</span></span>  
 [<span data-ttu-id="96ea1-120">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="96ea1-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="96ea1-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="96ea1-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

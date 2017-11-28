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
ms.openlocfilehash: 80002d064c48a90236a64a3d0a56fab5877cf411
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="fef5c-102">ICorDebugMemoryBuffer インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fef5c-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="fef5c-103">メモリ内のバッファーを表します。</span><span class="sxs-lookup"><span data-stu-id="fef5c-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fef5c-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="fef5c-104">Methods</span></span>  
  
|<span data-ttu-id="fef5c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="fef5c-105">Method</span></span>|<span data-ttu-id="fef5c-106">説明</span><span class="sxs-lookup"><span data-stu-id="fef5c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fef5c-107">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="fef5c-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="fef5c-108">メモリ バッファーのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="fef5c-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="fef5c-109">GetStartAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="fef5c-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="fef5c-110">メモリ バッファーの開始アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="fef5c-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fef5c-111">コメント</span><span class="sxs-lookup"><span data-stu-id="fef5c-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fef5c-112">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="fef5c-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="fef5c-113">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="fef5c-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fef5c-114">要件</span><span class="sxs-lookup"><span data-stu-id="fef5c-114">Requirements</span></span>  
 <span data-ttu-id="fef5c-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fef5c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fef5c-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fef5c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fef5c-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fef5c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fef5c-118">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fef5c-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fef5c-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="fef5c-119">See Also</span></span>  
 [<span data-ttu-id="fef5c-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="fef5c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="fef5c-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="fef5c-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

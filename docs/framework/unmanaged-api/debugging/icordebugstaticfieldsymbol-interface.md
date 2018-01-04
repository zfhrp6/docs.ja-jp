---
title: "ICorDebugStaticFieldSymbol インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a25e19bf43d852670bc5f4f491fb25707395e04a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="d6fa9-102">ICorDebugStaticFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d6fa9-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="d6fa9-103">静的フィールドのデバッグ シンボル情報を表します。</span><span class="sxs-lookup"><span data-stu-id="d6fa9-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d6fa9-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="d6fa9-104">Methods</span></span>  
  
|<span data-ttu-id="d6fa9-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d6fa9-105">Method</span></span>|<span data-ttu-id="d6fa9-106">説明</span><span class="sxs-lookup"><span data-stu-id="d6fa9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d6fa9-107">GetAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="d6fa9-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="d6fa9-108">静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="d6fa9-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="d6fa9-109">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="d6fa9-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="d6fa9-110">静的フィールドの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="d6fa9-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="d6fa9-111">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="d6fa9-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="d6fa9-112">静的フィールドのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="d6fa9-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6fa9-113">コメント</span><span class="sxs-lookup"><span data-stu-id="d6fa9-113">Remarks</span></span>  
 <span data-ttu-id="d6fa9-114">`ICorDebugStaticFieldSymbol` インターフェイスは、静的フィールドのデバッグ シンボル情報を取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d6fa9-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6fa9-115">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="d6fa9-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="d6fa9-116">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="d6fa9-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6fa9-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="d6fa9-117">Requirements</span></span>  
 <span data-ttu-id="d6fa9-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d6fa9-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6fa9-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6fa9-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6fa9-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6fa9-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6fa9-121">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6fa9-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6fa9-122">参照</span><span class="sxs-lookup"><span data-stu-id="d6fa9-122">See Also</span></span>  
 [<span data-ttu-id="d6fa9-123">ICorDebugInstanceFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d6fa9-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="d6fa9-124">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d6fa9-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="d6fa9-125">デバッグ</span><span class="sxs-lookup"><span data-stu-id="d6fa9-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

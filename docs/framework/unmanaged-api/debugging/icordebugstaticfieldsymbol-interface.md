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
ms.openlocfilehash: b747d2d43fd7ff4dc901dff14277dbce9606497f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="4eee1-102">ICorDebugStaticFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4eee1-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="4eee1-103">静的フィールドのデバッグ シンボル情報を表します。</span><span class="sxs-lookup"><span data-stu-id="4eee1-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4eee1-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="4eee1-104">Methods</span></span>  
  
|<span data-ttu-id="4eee1-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="4eee1-105">Method</span></span>|<span data-ttu-id="4eee1-106">説明</span><span class="sxs-lookup"><span data-stu-id="4eee1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4eee1-107">GetAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="4eee1-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="4eee1-108">静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="4eee1-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="4eee1-109">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="4eee1-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="4eee1-110">静的フィールドの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="4eee1-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="4eee1-111">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="4eee1-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="4eee1-112">静的フィールドのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="4eee1-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4eee1-113">コメント</span><span class="sxs-lookup"><span data-stu-id="4eee1-113">Remarks</span></span>  
 <span data-ttu-id="4eee1-114">`ICorDebugStaticFieldSymbol` インターフェイスは、静的フィールドのデバッグ シンボル情報を取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="4eee1-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4eee1-115">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="4eee1-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="4eee1-116">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="4eee1-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4eee1-117">要件</span><span class="sxs-lookup"><span data-stu-id="4eee1-117">Requirements</span></span>  
 <span data-ttu-id="4eee1-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4eee1-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4eee1-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4eee1-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4eee1-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4eee1-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4eee1-121">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4eee1-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eee1-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="4eee1-122">See Also</span></span>  
 [<span data-ttu-id="4eee1-123">ICorDebugInstanceFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4eee1-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="4eee1-124">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="4eee1-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="4eee1-125">デバッグ</span><span class="sxs-lookup"><span data-stu-id="4eee1-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

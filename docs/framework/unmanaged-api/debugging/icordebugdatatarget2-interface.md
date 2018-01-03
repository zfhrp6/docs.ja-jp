---
title: "ICorDebugDataTarget2 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2aefdb34277d2cb7ebc29ef817745b85064475d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="b1c53-102">ICorDebugDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b1c53-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="b1c53-103">論理的に拡張し、 [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="b1c53-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b1c53-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="b1c53-104">Methods</span></span>  
  
|<span data-ttu-id="b1c53-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b1c53-105">Method</span></span>|<span data-ttu-id="b1c53-106">説明</span><span class="sxs-lookup"><span data-stu-id="b1c53-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b1c53-107">CreateVirtualUnwinder メソッド</span><span class="sxs-lookup"><span data-stu-id="b1c53-107">CreateVirtualUnwinder Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="b1c53-108">初期コンテキストからアンワインドを開始する新しいスタック アンワインダーを作成します (これは、必ずしもスレッドのリーフではありません)。</span><span class="sxs-lookup"><span data-stu-id="b1c53-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="b1c53-109">EnumerateThreadIDs メソッド</span><span class="sxs-lookup"><span data-stu-id="b1c53-109">EnumerateThreadIDs Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="b1c53-110">アクティブなスレッド ID の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="b1c53-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="b1c53-111">GetImageFromPointer メソッド</span><span class="sxs-lookup"><span data-stu-id="b1c53-111">GetImageFromPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="b1c53-112">モジュールのアドレスから、そのモジュールのベース アドレスとサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="b1c53-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="b1c53-113">GetImageLocation メソッド</span><span class="sxs-lookup"><span data-stu-id="b1c53-113">GetImageLocation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="b1c53-114">モジュールのベース アドレスからモジュールのパスを返します。</span><span class="sxs-lookup"><span data-stu-id="b1c53-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="b1c53-115">GetSymbolProviderForImage メソッド</span><span class="sxs-lookup"><span data-stu-id="b1c53-115">GetSymbolProviderForImage Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="b1c53-116">モジュールのベース アドレスからそのモジュールのシンボル プロバイダーを返します。</span><span class="sxs-lookup"><span data-stu-id="b1c53-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1c53-117">コメント</span><span class="sxs-lookup"><span data-stu-id="b1c53-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1c53-118">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="b1c53-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="b1c53-119">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="b1c53-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1c53-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="b1c53-120">Requirements</span></span>  
 <span data-ttu-id="b1c53-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b1c53-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1c53-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1c53-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1c53-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1c53-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1c53-124">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1c53-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1c53-125">参照</span><span class="sxs-lookup"><span data-stu-id="b1c53-125">See Also</span></span>  
 [<span data-ttu-id="b1c53-126">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b1c53-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b1c53-127">デバッグ</span><span class="sxs-lookup"><span data-stu-id="b1c53-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

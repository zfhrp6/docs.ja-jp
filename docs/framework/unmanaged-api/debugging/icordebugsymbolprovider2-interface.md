---
title: "ICorDebugSymbolProvider2 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7666b8d64b689d3640594f07614be97b72e85a8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="09397-102">ICorDebugSymbolProvider2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="09397-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="09397-103">論理的に拡張し、 [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)追加のデバッグ シンボル情報を取得するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="09397-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="09397-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="09397-104">Methods</span></span>  
  
|<span data-ttu-id="09397-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="09397-105">Method</span></span>|<span data-ttu-id="09397-106">説明</span><span class="sxs-lookup"><span data-stu-id="09397-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="09397-107">GetFrameProps メソッド</span><span class="sxs-lookup"><span data-stu-id="09397-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="09397-108">メソッドのメソッド開始位置を示す相対仮想アドレスと、指定されたコード相対仮想アドレスを持つ親フレームを返します。</span><span class="sxs-lookup"><span data-stu-id="09397-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="09397-109">GetGenericDictionaryInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="09397-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="09397-110">汎用のディクショナリ マップを取得します。</span><span class="sxs-lookup"><span data-stu-id="09397-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09397-111">コメント</span><span class="sxs-lookup"><span data-stu-id="09397-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09397-112">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="09397-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="09397-113">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="09397-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09397-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="09397-114">Requirements</span></span>  
 <span data-ttu-id="09397-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="09397-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09397-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="09397-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09397-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09397-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09397-118">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09397-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09397-119">参照</span><span class="sxs-lookup"><span data-stu-id="09397-119">See Also</span></span>  
 [<span data-ttu-id="09397-120">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="09397-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="09397-121">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="09397-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="09397-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="09397-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

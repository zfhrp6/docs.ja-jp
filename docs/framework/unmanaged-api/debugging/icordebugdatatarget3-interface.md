---
title: "ICorDebugDataTarget3 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a1ab94e792265916e29ed24239e25cb5d57d1313
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="11671-102">ICorDebugDataTarget3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11671-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="11671-103">論理的に拡張し、 [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)読み込まれたモジュールに関する情報を提供するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="11671-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="11671-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="11671-104">Method</span></span>  
  
|<span data-ttu-id="11671-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="11671-105">Method</span></span>|<span data-ttu-id="11671-106">説明</span><span class="sxs-lookup"><span data-stu-id="11671-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="11671-107">GetLoadedModules メソッド</span><span class="sxs-lookup"><span data-stu-id="11671-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="11671-108">これまでに読み込まれたモジュールの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="11671-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11671-109">コメント</span><span class="sxs-lookup"><span data-stu-id="11671-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11671-110">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="11671-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="11671-111">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="11671-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11671-112">要件</span><span class="sxs-lookup"><span data-stu-id="11671-112">Requirements</span></span>  
 <span data-ttu-id="11671-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="11671-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11671-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11671-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11671-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11671-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11671-116">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11671-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11671-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="11671-117">See Also</span></span>  
 [<span data-ttu-id="11671-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="11671-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="11671-119">デバッグ</span><span class="sxs-lookup"><span data-stu-id="11671-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

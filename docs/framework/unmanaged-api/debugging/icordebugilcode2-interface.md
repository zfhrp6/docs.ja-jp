---
title: "ICorDebugILCode2 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILCode2
api_location: mscordbi.dll
api_type: COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f126d92cebe3261dc92b89cbf66bbcff5fd8808e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="8c0ac-102">ICorDebugILCode2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c0ac-102">ICorDebugILCode2 Interface</span></span>
<span data-ttu-id="8c0ac-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="8c0ac-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="8c0ac-104">論理的に拡張し、 [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)に元のメソッド IL オフセットを関数のローカル変数シグネチャに対するトークンを返すし、プロファイラーのインストルメント化された中間言語 (IL) にマップするメソッドを提供するインターフェイスオフセットします。</span><span class="sxs-lookup"><span data-stu-id="8c0ac-104">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8c0ac-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8c0ac-105">Methods</span></span>  
  
|<span data-ttu-id="8c0ac-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="8c0ac-106">Method</span></span>|<span data-ttu-id="8c0ac-107">説明</span><span class="sxs-lookup"><span data-stu-id="8c0ac-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8c0ac-108">GetInstrumentedILMap メソッド</span><span class="sxs-lookup"><span data-stu-id="8c0ac-108">GetInstrumentedILMap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="8c0ac-109">プロファイラーのインストルメント化された IL オフセットから、このインスタンスに対する元のメソッドの IL オフセットへのマップを返します。</span><span class="sxs-lookup"><span data-stu-id="8c0ac-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="8c0ac-110">GetLocalVarSigToken メソッド</span><span class="sxs-lookup"><span data-stu-id="8c0ac-110">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="8c0ac-111">このインスタンスで示される関数について、ローカル変数のシグネチャのメタデータ トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="8c0ac-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8c0ac-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="8c0ac-112">Requirements</span></span>  
 <span data-ttu-id="8c0ac-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8c0ac-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c0ac-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c0ac-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c0ac-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c0ac-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c0ac-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c0ac-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c0ac-117">参照</span><span class="sxs-lookup"><span data-stu-id="8c0ac-117">See Also</span></span>  
 [<span data-ttu-id="8c0ac-118">ICorDebugILCode インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c0ac-118">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 [<span data-ttu-id="8c0ac-119">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c0ac-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8c0ac-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="8c0ac-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

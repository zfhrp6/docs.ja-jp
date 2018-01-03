---
title: "ICLRDataEnumMemoryRegionsCallback インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataEnumMemoryRegionsCallback
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataEnumMemoryRegionsCallback
helpviewer_keywords: ICLRDataEnumMemoryRegionsCallback interface [.NET Framework debugging]
ms.assetid: 3f1af8b0-8478-48e0-a7ec-3e90e0b97649
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 091f5345461ebe5054e769ae9d051ef2e0737ffb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="a3319-102">ICLRDataEnumMemoryRegionsCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a3319-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="a3319-103">コールバック メソッドを提供[iclrdataenummemoryregions::enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md)デバッガーにメモリの指定した領域の列挙の試行の結果を報告します。</span><span class="sxs-lookup"><span data-stu-id="a3319-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a3319-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="a3319-104">Methods</span></span>  
  
|<span data-ttu-id="a3319-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a3319-105">Method</span></span>|<span data-ttu-id="a3319-106">説明</span><span class="sxs-lookup"><span data-stu-id="a3319-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a3319-107">EnumMemoryRegion メソッド</span><span class="sxs-lookup"><span data-stu-id="a3319-107">EnumMemoryRegion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="a3319-108">によって呼び出されます`ICLRDataEnumMemoryRegions::EnumMemoryRegions`デバッガーにメモリの指定した領域の列挙の試行の結果を報告します。</span><span class="sxs-lookup"><span data-stu-id="a3319-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a3319-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="a3319-109">Requirements</span></span>  
 <span data-ttu-id="a3319-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a3319-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3319-111">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="a3319-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a3319-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3319-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3319-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3319-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3319-114">参照</span><span class="sxs-lookup"><span data-stu-id="a3319-114">See Also</span></span>  
 [<span data-ttu-id="a3319-115">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a3319-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

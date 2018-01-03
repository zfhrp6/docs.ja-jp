---
title: "ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataEnumMemoryRegionsCallback.EnumMemoryRegion
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
helpviewer_keywords:
- EnumMemoryRegion method [.NET Framework debugging]
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion method [.NET Framework debugging]
ms.assetid: 9bb93fab-57e8-4f9a-9ef3-1794504fa896
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1a284d7277aa2f8c474ca4aab3dd6208bc3b2bb0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="4733e-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion メソッド</span><span class="sxs-lookup"><span data-stu-id="4733e-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>
<span data-ttu-id="4733e-103">によって呼び出されます[iclrdataenummemoryregions::enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md)デバッガーにメモリの指定した領域の列挙の試行の結果を報告します。</span><span class="sxs-lookup"><span data-stu-id="4733e-103">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4733e-104">構文</span><span class="sxs-lookup"><span data-stu-id="4733e-104">Syntax</span></span>  
  
```  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4733e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4733e-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="4733e-106">[in]列挙するがメモリ領域の開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="4733e-106">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="4733e-107">[in](バイト単位) のメモリ領域のサイズ。</span><span class="sxs-lookup"><span data-stu-id="4733e-107">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4733e-108">コメント</span><span class="sxs-lookup"><span data-stu-id="4733e-108">Remarks</span></span>  
 <span data-ttu-id="4733e-109">`ICLRDataEnumMemoryRegions::EnumMemoryRegions`メソッドは、メモリ領域の列挙を試行するたびにこのコールバック メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4733e-109">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="4733e-110">列挙体は、このメソッドがエラーを示す HRESULT を返す場合でも続行されます。</span><span class="sxs-lookup"><span data-stu-id="4733e-110">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="4733e-111">このコールバックによって報告された領域には、重複またはオーバー ラップがあります。</span><span class="sxs-lookup"><span data-stu-id="4733e-111">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4733e-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="4733e-112">Requirements</span></span>  
 <span data-ttu-id="4733e-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4733e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4733e-114">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="4733e-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="4733e-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4733e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4733e-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4733e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4733e-117">参照</span><span class="sxs-lookup"><span data-stu-id="4733e-117">See Also</span></span>  
 [<span data-ttu-id="4733e-118">ICLRDataEnumMemoryRegionsCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4733e-118">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)

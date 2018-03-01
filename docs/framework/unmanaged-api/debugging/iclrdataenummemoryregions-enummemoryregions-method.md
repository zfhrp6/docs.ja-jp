---
title: "ICLRDataEnumMemoryRegions::EnumMemoryRegions メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1685b1f739519485e5e68928b29a874587e6f9c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="eac34-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions メソッド</span><span class="sxs-lookup"><span data-stu-id="eac34-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="eac34-103">指定されたメモリ領域を列挙します。</span><span class="sxs-lookup"><span data-stu-id="eac34-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eac34-104">構文</span><span class="sxs-lookup"><span data-stu-id="eac34-104">Syntax</span></span>  
  
```  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eac34-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eac34-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="eac34-106">[in]ポインター、 [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)インスタンスの結果をデバッガーに通知を列挙中の各メモリ領域については、このメソッドによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="eac34-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="eac34-107">メモリ領域の列挙は、コールバックがエラーを示す場合でもは続行されます。</span><span class="sxs-lookup"><span data-stu-id="eac34-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="eac34-108">[in]使用しません。</span><span class="sxs-lookup"><span data-stu-id="eac34-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="eac34-109">[in]値、 [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)列挙されるメモリの領域を指定する列挙です。</span><span class="sxs-lookup"><span data-stu-id="eac34-109">[in] A value of the [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eac34-110">コメント</span><span class="sxs-lookup"><span data-stu-id="eac34-110">Remarks</span></span>  
 <span data-ttu-id="eac34-111">このメソッドは、指定された使用[ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)インスタンスの結果の呼び出し元に通知します。</span><span class="sxs-lookup"><span data-stu-id="eac34-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eac34-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="eac34-112">Requirements</span></span>  
 <span data-ttu-id="eac34-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="eac34-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eac34-114">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="eac34-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="eac34-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eac34-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eac34-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eac34-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eac34-117">参照</span><span class="sxs-lookup"><span data-stu-id="eac34-117">See Also</span></span>  
 [<span data-ttu-id="eac34-118">ICLRDataEnumMemoryRegions インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eac34-118">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)

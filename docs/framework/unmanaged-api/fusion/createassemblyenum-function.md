---
title: "CreateAssemblyEnum 関数"
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
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3719da442b2c2c589772a0bc19cec3efb4e6dace
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="6d1b6-102">CreateAssemblyEnum 関数</span><span class="sxs-lookup"><span data-stu-id="6d1b6-102">CreateAssemblyEnum Function</span></span>
<span data-ttu-id="6d1b6-103">ポインターを取得、 [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)インスタンスに、指定したアセンブリ内のオブジェクトを列挙できる[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="6d1b6-103">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d1b6-104">構文</span><span class="sxs-lookup"><span data-stu-id="6d1b6-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d1b6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6d1b6-105">Parameters</span></span>  
 `pEnum`  
 <span data-ttu-id="6d1b6-106">[out]含む、要求されたメモリ位置へのポインター`IAssemblyEnum`ポインター。</span><span class="sxs-lookup"><span data-stu-id="6d1b6-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="6d1b6-107">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="6d1b6-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="6d1b6-108">`pUnkReserved`null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d1b6-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="6d1b6-109">[in]`IAssemblyName`要求されたアセンブリのです。</span><span class="sxs-lookup"><span data-stu-id="6d1b6-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="6d1b6-110">この名前は、列挙値をフィルターに使用されます。</span><span class="sxs-lookup"><span data-stu-id="6d1b6-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="6d1b6-111">グローバル アセンブリ キャッシュ内のすべてのアセンブリを列挙する null になります。</span><span class="sxs-lookup"><span data-stu-id="6d1b6-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6d1b6-112">[in]列挙子の動作を変更するためのフラグです。</span><span class="sxs-lookup"><span data-stu-id="6d1b6-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="6d1b6-113">このパラメーターからに正確に 1 ビットが含まれています、 [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="6d1b6-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="6d1b6-114">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="6d1b6-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="6d1b6-115">`pvReserved`null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d1b6-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d1b6-116">コメント</span><span class="sxs-lookup"><span data-stu-id="6d1b6-116">Remarks</span></span>  
 <span data-ttu-id="6d1b6-117">`dwFlags`パラメーターにはから正確に 1 ビットが含まれています、`ASM_CACHE_FLAGS`列挙します。</span><span class="sxs-lookup"><span data-stu-id="6d1b6-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d1b6-118">必要条件</span><span class="sxs-lookup"><span data-stu-id="6d1b6-118">Requirements</span></span>  
 <span data-ttu-id="6d1b6-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6d1b6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d1b6-120">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="6d1b6-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6d1b6-121">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="6d1b6-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6d1b6-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d1b6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d1b6-123">参照</span><span class="sxs-lookup"><span data-stu-id="6d1b6-123">See Also</span></span>  
 [<span data-ttu-id="6d1b6-124">IAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6d1b6-124">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 [<span data-ttu-id="6d1b6-125">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6d1b6-125">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="6d1b6-126">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="6d1b6-126">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

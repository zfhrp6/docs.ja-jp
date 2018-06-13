---
title: CreateAssemblyEnum 関数
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b2098d5d9ce1c01f232cf2904c1fd3e990dfbe2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432117"
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="d99e8-102">CreateAssemblyEnum 関数</span><span class="sxs-lookup"><span data-stu-id="d99e8-102">CreateAssemblyEnum Function</span></span>
<span data-ttu-id="d99e8-103">ポインターを取得、 [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)インスタンスに、指定したアセンブリ内のオブジェクトを列挙できる[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="d99e8-103">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d99e8-104">構文</span><span class="sxs-lookup"><span data-stu-id="d99e8-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d99e8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d99e8-105">Parameters</span></span>  
 `pEnum`  
 <span data-ttu-id="d99e8-106">[out]含む、要求されたメモリ位置へのポインター`IAssemblyEnum`ポインター。</span><span class="sxs-lookup"><span data-stu-id="d99e8-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="d99e8-107">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="d99e8-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="d99e8-108">`pUnkReserved` null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d99e8-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="d99e8-109">[in]`IAssemblyName`要求されたアセンブリのです。</span><span class="sxs-lookup"><span data-stu-id="d99e8-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="d99e8-110">この名前は、列挙値をフィルターに使用されます。</span><span class="sxs-lookup"><span data-stu-id="d99e8-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="d99e8-111">グローバル アセンブリ キャッシュ内のすべてのアセンブリを列挙する null になります。</span><span class="sxs-lookup"><span data-stu-id="d99e8-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d99e8-112">[in]列挙子の動作を変更するためのフラグです。</span><span class="sxs-lookup"><span data-stu-id="d99e8-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="d99e8-113">このパラメーターからに正確に 1 ビットが含まれています、 [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="d99e8-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="d99e8-114">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="d99e8-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="d99e8-115">`pvReserved` null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d99e8-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d99e8-116">コメント</span><span class="sxs-lookup"><span data-stu-id="d99e8-116">Remarks</span></span>  
 <span data-ttu-id="d99e8-117">`dwFlags`パラメーターにはから正確に 1 ビットが含まれています、`ASM_CACHE_FLAGS`列挙します。</span><span class="sxs-lookup"><span data-stu-id="d99e8-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d99e8-118">要件</span><span class="sxs-lookup"><span data-stu-id="d99e8-118">Requirements</span></span>  
 <span data-ttu-id="d99e8-119">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d99e8-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d99e8-120">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d99e8-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d99e8-121">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d99e8-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d99e8-122">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d99e8-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d99e8-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="d99e8-123">See Also</span></span>  
 [<span data-ttu-id="d99e8-124">IAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d99e8-124">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 [<span data-ttu-id="d99e8-125">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d99e8-125">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="d99e8-126">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="d99e8-126">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

---
title: "IMetaDataDispenserEx::FindAssemblyModule メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.FindAssemblyModule
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::FindAssemblyModule
helpviewer_keywords:
- FindAssemblyModule method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssemblyModule method [.NET Framework metadata]
ms.assetid: d1fb65e1-7e19-4513-85b1-44f87c294d3e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 482bc9b9a89d876e7ac09fcb4edcd190adc168f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="aa31e-102">IMetaDataDispenserEx::FindAssemblyModule メソッド</span><span class="sxs-lookup"><span data-stu-id="aa31e-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="aa31e-103">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="aa31e-103">This method is not implemented.</span></span> <span data-ttu-id="aa31e-104">呼び出された場合、E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="aa31e-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa31e-105">構文</span><span class="sxs-lookup"><span data-stu-id="aa31e-105">Syntax</span></span>  
  
```  
HRESULT FindAssemblyModule(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [in]  LPCWSTR  szModuleName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aa31e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa31e-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="aa31e-107">[in]使用しません。</span><span class="sxs-lookup"><span data-stu-id="aa31e-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="aa31e-108">[in]使用しません。</span><span class="sxs-lookup"><span data-stu-id="aa31e-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="aa31e-109">[in]使用しません。</span><span class="sxs-lookup"><span data-stu-id="aa31e-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="aa31e-110">[in]モジュールの名前。</span><span class="sxs-lookup"><span data-stu-id="aa31e-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="aa31e-111">[in]検索するアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="aa31e-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="aa31e-112">[out]アセンブリの簡易名。</span><span class="sxs-lookup"><span data-stu-id="aa31e-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="aa31e-113">[in]サイズをバイト単位での`szName`します。</span><span class="sxs-lookup"><span data-stu-id="aa31e-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="aa31e-114">[out]実際に返される文字数`szName`です。</span><span class="sxs-lookup"><span data-stu-id="aa31e-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa31e-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="aa31e-115">Requirements</span></span>  
 <span data-ttu-id="aa31e-116">**Platform:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="aa31e-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa31e-117">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="aa31e-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aa31e-118">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="aa31e-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aa31e-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa31e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa31e-120">参照</span><span class="sxs-lookup"><span data-stu-id="aa31e-120">See Also</span></span>  
 [<span data-ttu-id="aa31e-121">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aa31e-121">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="aa31e-122">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aa31e-122">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)

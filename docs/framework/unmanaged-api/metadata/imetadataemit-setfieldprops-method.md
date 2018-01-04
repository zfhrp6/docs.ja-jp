---
title: "IMetaDataEmit::SetFieldProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetFieldProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: daec4bb11115d4f31764fde767b083796eabbb73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="9c138-102">IMetaDataEmit::SetFieldProps メソッド</span><span class="sxs-lookup"><span data-stu-id="9c138-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="9c138-103">設定または指定したフィールドのトークンによって参照されるフィールドの既定値を更新します。</span><span class="sxs-lookup"><span data-stu-id="9c138-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c138-104">構文</span><span class="sxs-lookup"><span data-stu-id="9c138-104">Syntax</span></span>  
  
```  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,   
    [in]  DWORD       dwFieldFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c138-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9c138-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="9c138-106">[in]対象のフィールドのトークン。</span><span class="sxs-lookup"><span data-stu-id="9c138-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="9c138-107">[in]フィールドの属性。</span><span class="sxs-lookup"><span data-stu-id="9c138-107">[in] Field attributes.</span></span> <span data-ttu-id="9c138-108">これは、ビットマスク`CorFieldAttr`値。</span><span class="sxs-lookup"><span data-stu-id="9c138-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="9c138-109">[in]`ELEMENT_TYPE_`  *\** 定数値にします。</span><span class="sxs-lookup"><span data-stu-id="9c138-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="9c138-110">これは、`CorElementType`値。</span><span class="sxs-lookup"><span data-stu-id="9c138-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="9c138-111">定数が定義されない場合は、この値を設定`ELEMENT_TYPE_END`です。</span><span class="sxs-lookup"><span data-stu-id="9c138-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="9c138-112">[in]フィールドの定数値。</span><span class="sxs-lookup"><span data-stu-id="9c138-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="9c138-113">[in]Unicode 文字のサイズの`pValue`します。</span><span class="sxs-lookup"><span data-stu-id="9c138-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c138-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="9c138-114">Requirements</span></span>  
 <span data-ttu-id="9c138-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9c138-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c138-116">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9c138-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9c138-117">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="9c138-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c138-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c138-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c138-119">参照</span><span class="sxs-lookup"><span data-stu-id="9c138-119">See Also</span></span>  
 [<span data-ttu-id="9c138-120">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9c138-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="9c138-121">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9c138-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

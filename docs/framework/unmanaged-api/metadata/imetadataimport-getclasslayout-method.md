---
title: "IMetaDataImport::GetClassLayout メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetClassLayout
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cece37a6321fc68cbff2957f9753af5f2f916f5f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="a0007-102">IMetaDataImport::GetClassLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="a0007-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="a0007-103">指定した TypeDef トークンによって参照されるクラスのレイアウト情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="a0007-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0007-104">構文</span><span class="sxs-lookup"><span data-stu-id="a0007-104">Syntax</span></span>  
  
```  
HRESULT GetClassLayout  (   
   [in]  mdTypeDef          td,   
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0007-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0007-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="a0007-106">[in]返すレイアウトを持つクラスの TypeDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="a0007-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="a0007-107">[out]値 1、2、4、8、またはクラスのパック サイズを表す、16 のいずれか。</span><span class="sxs-lookup"><span data-stu-id="a0007-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="a0007-108">[out]配列[COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)値。</span><span class="sxs-lookup"><span data-stu-id="a0007-108">[out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a0007-109">[in] `rFieldOffset` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="a0007-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="a0007-110">[out]返される要素の数`rFieldOffset`です。</span><span class="sxs-lookup"><span data-stu-id="a0007-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="a0007-111">[out]によって表されるクラスのバイト サイズ`td`です。</span><span class="sxs-lookup"><span data-stu-id="a0007-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0007-112">要件</span><span class="sxs-lookup"><span data-stu-id="a0007-112">Requirements</span></span>  
 <span data-ttu-id="a0007-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a0007-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0007-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a0007-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a0007-115">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="a0007-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a0007-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0007-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0007-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0007-117">See Also</span></span>  
 [<span data-ttu-id="a0007-118">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0007-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a0007-119">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0007-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

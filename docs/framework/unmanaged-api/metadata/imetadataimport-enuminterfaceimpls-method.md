---
title: "IMetaDataImport::EnumInterfaceImpls メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumInterfaceImpls
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1d9f2883c32daafd8938bd1c80c035a3527cc6a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="a005e-102">IMetaDataImport::EnumInterfaceImpls メソッド</span><span class="sxs-lookup"><span data-stu-id="a005e-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="a005e-103">インターフェイス実装を表す MethodDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="a005e-103">Enumerates MethodDef tokens representing interface implementations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a005e-104">構文</span><span class="sxs-lookup"><span data-stu-id="a005e-104">Syntax</span></span>  
  
```  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a005e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a005e-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a005e-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a005e-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="a005e-107">[in]列挙するインターフェイスの実装を表す MethodDef トークンは、TypeDef のトークンです。</span><span class="sxs-lookup"><span data-stu-id="a005e-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="a005e-108">[out]MethodDef トークンを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="a005e-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a005e-109">[in] `rImpls` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="a005e-109">[in] The maximum size of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="a005e-110">[out]実際に返されるトークン数`rImpls`です。</span><span class="sxs-lookup"><span data-stu-id="a005e-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a005e-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="a005e-111">Return Value</span></span>  
  
|<span data-ttu-id="a005e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a005e-112">HRESULT</span></span>|<span data-ttu-id="a005e-113">説明</span><span class="sxs-lookup"><span data-stu-id="a005e-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a005e-114">`EnumInterfaceImpls`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="a005e-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a005e-115">MethodDef トークンを列挙することはありません。</span><span class="sxs-lookup"><span data-stu-id="a005e-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="a005e-116">その場合は、`pcImpls`は 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="a005e-116">In that case, `pcImpls` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a005e-117">要件</span><span class="sxs-lookup"><span data-stu-id="a005e-117">Requirements</span></span>  
 <span data-ttu-id="a005e-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a005e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a005e-119">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a005e-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a005e-120">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="a005e-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a005e-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a005e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a005e-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="a005e-122">See Also</span></span>  
 [<span data-ttu-id="a005e-123">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a005e-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a005e-124">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a005e-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

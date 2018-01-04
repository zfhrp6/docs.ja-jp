---
title: "IMetaDataImport::EnumEvents メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumEvents
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumEvents
helpviewer_keywords:
- IMetaDataImport::EnumEvents method [.NET Framework metadata]
- EnumEvents method [.NET Framework metadata]
ms.assetid: e1efedcb-3dd7-42ae-a399-21c24728aec5
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed783cf80fb068656855c2c06ab814f665f1cede
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="0676d-102">IMetaDataImport::EnumEvents メソッド</span><span class="sxs-lookup"><span data-stu-id="0676d-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="0676d-103">指定した TypeDef トークンのイベント定義トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="0676d-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0676d-104">構文</span><span class="sxs-lookup"><span data-stu-id="0676d-104">Syntax</span></span>  
  
```  
HRESULT EnumEvents (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdEvent     rEvents[],   
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0676d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0676d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="0676d-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0676d-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="0676d-107">[in]イベント定義を持つが列挙されるまでは TypeDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="0676d-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="0676d-108">[out]返されるイベントの配列。</span><span class="sxs-lookup"><span data-stu-id="0676d-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0676d-109">[in] `rEvents` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="0676d-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="0676d-110">[out]実際に返されるイベントの数`rEvents`です。</span><span class="sxs-lookup"><span data-stu-id="0676d-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0676d-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="0676d-111">Return Value</span></span>  
  
|<span data-ttu-id="0676d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0676d-112">HRESULT</span></span>|<span data-ttu-id="0676d-113">説明</span><span class="sxs-lookup"><span data-stu-id="0676d-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0676d-114">`EnumEvents`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="0676d-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0676d-115">列挙するイベントがありません。</span><span class="sxs-lookup"><span data-stu-id="0676d-115">There are no events to enumerate.</span></span> <span data-ttu-id="0676d-116">その場合は、`pcEvents`ゼロです。</span><span class="sxs-lookup"><span data-stu-id="0676d-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0676d-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="0676d-117">Requirements</span></span>  
 <span data-ttu-id="0676d-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0676d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0676d-119">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0676d-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0676d-120">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="0676d-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0676d-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0676d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0676d-122">参照</span><span class="sxs-lookup"><span data-stu-id="0676d-122">See Also</span></span>  
 [<span data-ttu-id="0676d-123">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0676d-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="0676d-124">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0676d-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

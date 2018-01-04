---
title: "IMetaDataImport::EnumParams メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumParams
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumParams
helpviewer_keywords:
- IMetaDataImport::EnumParams method [.NET Framework metadata]
- EnumParams method [.NET Framework metadata]
ms.assetid: 52118dc9-fe6e-4b39-aa48-c3cc3ea4214d
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 51544a44ed4bae25d4214e25c717769a8446f0f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="d0707-102">IMetaDataImport::EnumParams メソッド</span><span class="sxs-lookup"><span data-stu-id="d0707-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="d0707-103">指定した MethodDef トークンによって参照されるメソッドのパラメーターを表す ParamDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="d0707-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0707-104">構文</span><span class="sxs-lookup"><span data-stu-id="d0707-104">Syntax</span></span>  
  
```  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0707-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d0707-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d0707-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d0707-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="d0707-107">このメソッドの最初の呼び出しで NULL があります。</span><span class="sxs-lookup"><span data-stu-id="d0707-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="d0707-108">[in]列挙するパラメーターを持つメソッドを表す MethodDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="d0707-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="d0707-109">[out]ParamDef トークンを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="d0707-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d0707-110">[in] `rParams` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="d0707-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d0707-111">[out]返される ParamDef トークン数`rParams`です。</span><span class="sxs-lookup"><span data-stu-id="d0707-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0707-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="d0707-112">Return Value</span></span>  
  
|<span data-ttu-id="d0707-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d0707-113">HRESULT</span></span>|<span data-ttu-id="d0707-114">説明</span><span class="sxs-lookup"><span data-stu-id="d0707-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d0707-115">`EnumParams`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="d0707-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d0707-116">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="d0707-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="d0707-117">その場合は、`pcTokens`ゼロです。</span><span class="sxs-lookup"><span data-stu-id="d0707-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d0707-118">必要条件</span><span class="sxs-lookup"><span data-stu-id="d0707-118">Requirements</span></span>  
 <span data-ttu-id="d0707-119">**Platform:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d0707-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0707-120">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d0707-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d0707-121">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="d0707-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d0707-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0707-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0707-123">参照</span><span class="sxs-lookup"><span data-stu-id="d0707-123">See Also</span></span>  
 [<span data-ttu-id="d0707-124">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d0707-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="d0707-125">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d0707-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

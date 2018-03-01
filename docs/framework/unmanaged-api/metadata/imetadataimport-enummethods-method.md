---
title: "IMetaDataImport::EnumMethods メソッド"
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
- IMetaDataImport.EnumMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethods
helpviewer_keywords:
- IMetaDataImport::EnumMethods method [.NET Framework metadata]
- EnumMethods method [.NET Framework metadata]
ms.assetid: 8cc3b0c3-d97d-4f71-9e7d-ef2a92b4959a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4052bcd07ec5abd3c560569b59600123350e810c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="de04f-102">IMetaDataImport::EnumMethods メソッド</span><span class="sxs-lookup"><span data-stu-id="de04f-102">IMetaDataImport::EnumMethods Method</span></span>
<span data-ttu-id="de04f-103">指定した型のメソッドを表す MethodDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="de04f-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de04f-104">構文</span><span class="sxs-lookup"><span data-stu-id="de04f-104">Syntax</span></span>  
  
```  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,   
   [in]  mdTypeDef      cl,   
   [out] mdMethodDef    rMethods[],   
   [in]  ULONG          cMax,   
   [out] ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de04f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="de04f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="de04f-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="de04f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="de04f-107">このメソッドの最初の呼び出しで NULL があります。</span><span class="sxs-lookup"><span data-stu-id="de04f-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="de04f-108">[in]型を列挙するメソッドを表す TypeDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="de04f-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="de04f-109">[out]MethodDef トークンを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="de04f-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="de04f-110">[in]MethodDef の最大サイズ`rMethods`配列。</span><span class="sxs-lookup"><span data-stu-id="de04f-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="de04f-111">[out]MethodDef トークンで返される数`rMethods`です。</span><span class="sxs-lookup"><span data-stu-id="de04f-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de04f-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="de04f-112">Return Value</span></span>  
  
|<span data-ttu-id="de04f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="de04f-113">HRESULT</span></span>|<span data-ttu-id="de04f-114">説明</span><span class="sxs-lookup"><span data-stu-id="de04f-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="de04f-115">`EnumMethods`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="de04f-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="de04f-116">MethodDef トークンを列挙することはありません。</span><span class="sxs-lookup"><span data-stu-id="de04f-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="de04f-117">その場合は、`pcTokens`ゼロです。</span><span class="sxs-lookup"><span data-stu-id="de04f-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="de04f-118">必要条件</span><span class="sxs-lookup"><span data-stu-id="de04f-118">Requirements</span></span>  
 <span data-ttu-id="de04f-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="de04f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de04f-120">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="de04f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="de04f-121">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="de04f-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="de04f-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de04f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de04f-123">参照</span><span class="sxs-lookup"><span data-stu-id="de04f-123">See Also</span></span>  
 [<span data-ttu-id="de04f-124">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="de04f-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="de04f-125">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="de04f-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

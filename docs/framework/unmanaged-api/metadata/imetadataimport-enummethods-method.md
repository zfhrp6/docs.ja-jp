---
title: IMetaDataImport::EnumMethods メソッド
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 933694a6a033dbfe817e3848b9008f05b86f51f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449013"
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="8cfae-102">IMetaDataImport::EnumMethods メソッド</span><span class="sxs-lookup"><span data-stu-id="8cfae-102">IMetaDataImport::EnumMethods Method</span></span>
<span data-ttu-id="8cfae-103">指定した型のメソッドを表す MethodDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="8cfae-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cfae-104">構文</span><span class="sxs-lookup"><span data-stu-id="8cfae-104">Syntax</span></span>  
  
```  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,   
   [in]  mdTypeDef      cl,   
   [out] mdMethodDef    rMethods[],   
   [in]  ULONG          cMax,   
   [out] ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8cfae-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8cfae-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="8cfae-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8cfae-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="8cfae-107">このメソッドの最初の呼び出しで NULL があります。</span><span class="sxs-lookup"><span data-stu-id="8cfae-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="8cfae-108">[in]型を列挙するメソッドを表す TypeDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="8cfae-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="8cfae-109">[out]MethodDef トークンを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="8cfae-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8cfae-110">[in]MethodDef の最大サイズ`rMethods`配列。</span><span class="sxs-lookup"><span data-stu-id="8cfae-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="8cfae-111">[out]MethodDef トークンで返される数`rMethods`です。</span><span class="sxs-lookup"><span data-stu-id="8cfae-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8cfae-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="8cfae-112">Return Value</span></span>  
  
|<span data-ttu-id="8cfae-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8cfae-113">HRESULT</span></span>|<span data-ttu-id="8cfae-114">説明</span><span class="sxs-lookup"><span data-stu-id="8cfae-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8cfae-115">`EnumMethods` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="8cfae-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8cfae-116">MethodDef トークンを列挙することはありません。</span><span class="sxs-lookup"><span data-stu-id="8cfae-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="8cfae-117">その場合は、`pcTokens`ゼロです。</span><span class="sxs-lookup"><span data-stu-id="8cfae-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8cfae-118">要件</span><span class="sxs-lookup"><span data-stu-id="8cfae-118">Requirements</span></span>  
 <span data-ttu-id="8cfae-119">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8cfae-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cfae-120">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8cfae-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8cfae-121">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="8cfae-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8cfae-122">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cfae-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cfae-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="8cfae-123">See Also</span></span>  
 [<span data-ttu-id="8cfae-124">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8cfae-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="8cfae-125">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8cfae-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

---
title: IMetaDataImport::EnumUserStrings メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUserStrings
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUserStrings
helpviewer_keywords:
- IMetaDataImport::EnumUserStrings method [.NET Framework metadata]
- EnumUserStrings method [.NET Framework metadata]
ms.assetid: 2b1f1418-4be8-4cdb-b418-b3abccc527a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98b99493e54b123d37eb281455180b9a25baddd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446831"
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="c1cb9-102">IMetaDataImport::EnumUserStrings メソッド</span><span class="sxs-lookup"><span data-stu-id="c1cb9-102">IMetaDataImport::EnumUserStrings Method</span></span>
<span data-ttu-id="c1cb9-103">現在のメタデータ スコープ内にあるハードコーディングされた文字列を表す String トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="c1cb9-103">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1cb9-104">構文</span><span class="sxs-lookup"><span data-stu-id="c1cb9-104">Syntax</span></span>  
  
```  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1cb9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c1cb9-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c1cb9-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c1cb9-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c1cb9-107">このメソッドの最初の呼び出しで NULL があります。</span><span class="sxs-lookup"><span data-stu-id="c1cb9-107">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="c1cb9-108">[out]文字列トークンを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="c1cb9-108">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c1cb9-109">[in] `rStrings` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="c1cb9-109">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="c1cb9-110">[out]返される文字列のトークン数`rStrings`です。</span><span class="sxs-lookup"><span data-stu-id="c1cb9-110">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1cb9-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="c1cb9-111">Return Value</span></span>  
  
|<span data-ttu-id="c1cb9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c1cb9-112">HRESULT</span></span>|<span data-ttu-id="c1cb9-113">説明</span><span class="sxs-lookup"><span data-stu-id="c1cb9-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c1cb9-114">`EnumUserStrings` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="c1cb9-114">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c1cb9-115">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="c1cb9-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="c1cb9-116">その場合は、`pcStrings`ゼロです。</span><span class="sxs-lookup"><span data-stu-id="c1cb9-116">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1cb9-117">コメント</span><span class="sxs-lookup"><span data-stu-id="c1cb9-117">Remarks</span></span>  
 <span data-ttu-id="c1cb9-118">文字列のトークンがによって作成された、 [imetadataemit::defineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="c1cb9-118">The String tokens are created by the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="c1cb9-119">このメソッドは、コンパイラではなくメタデータ ブラウザーで使用するよう設計されています。</span><span class="sxs-lookup"><span data-stu-id="c1cb9-119">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1cb9-120">要件</span><span class="sxs-lookup"><span data-stu-id="c1cb9-120">Requirements</span></span>  
 <span data-ttu-id="c1cb9-121">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c1cb9-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1cb9-122">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c1cb9-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c1cb9-123">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="c1cb9-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c1cb9-124">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1cb9-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1cb9-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1cb9-125">See Also</span></span>  
 [<span data-ttu-id="c1cb9-126">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c1cb9-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="c1cb9-127">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c1cb9-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

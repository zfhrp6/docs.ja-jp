---
title: IMetaDataImport::EnumSignatures メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumSignatures
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d36270047c8af0580a1cc3b44aa303e5907f33fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448121"
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="ea50a-102">IMetaDataImport::EnumSignatures メソッド</span><span class="sxs-lookup"><span data-stu-id="ea50a-102">IMetaDataImport::EnumSignatures Method</span></span>
<span data-ttu-id="ea50a-103">現在のスコープ内のスタンドアロン シグネチャを表す Signature トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="ea50a-103">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea50a-104">構文</span><span class="sxs-lookup"><span data-stu-id="ea50a-104">Syntax</span></span>  
  
```  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ea50a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ea50a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ea50a-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ea50a-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="ea50a-107">このメソッドの最初の呼び出しで NULL があります。</span><span class="sxs-lookup"><span data-stu-id="ea50a-107">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="ea50a-108">[out]署名トークンの保存に使用する配列。</span><span class="sxs-lookup"><span data-stu-id="ea50a-108">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ea50a-109">[in] `rSignatures` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="ea50a-109">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="ea50a-110">[out]返された署名トークンの数`rSignatures`です。</span><span class="sxs-lookup"><span data-stu-id="ea50a-110">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea50a-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="ea50a-111">Return Value</span></span>  
  
|<span data-ttu-id="ea50a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ea50a-112">HRESULT</span></span>|<span data-ttu-id="ea50a-113">説明</span><span class="sxs-lookup"><span data-stu-id="ea50a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ea50a-114">`EnumSignatures` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="ea50a-114">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ea50a-115">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="ea50a-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="ea50a-116">その場合は、`pcSignatures`ゼロです。</span><span class="sxs-lookup"><span data-stu-id="ea50a-116">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea50a-117">コメント</span><span class="sxs-lookup"><span data-stu-id="ea50a-117">Remarks</span></span>  
 <span data-ttu-id="ea50a-118">署名トークンがによって作成された、 [imetadataemit::gettokenfromsig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="ea50a-118">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea50a-119">要件</span><span class="sxs-lookup"><span data-stu-id="ea50a-119">Requirements</span></span>  
 <span data-ttu-id="ea50a-120">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ea50a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea50a-121">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ea50a-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ea50a-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="ea50a-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ea50a-123">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea50a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea50a-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea50a-124">See Also</span></span>  
 [<span data-ttu-id="ea50a-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ea50a-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="ea50a-126">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ea50a-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

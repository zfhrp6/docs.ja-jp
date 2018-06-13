---
title: IMetaDataEmit::SetFieldMarshal メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee18cbdc821dc523e9012488f0c08d9211164e62
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445563"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="2b439-102">IMetaDataEmit::SetFieldMarshal メソッド</span><span class="sxs-lookup"><span data-stu-id="2b439-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="2b439-103">指定したトークンによって参照されるフィールド、メソッドの戻り値、またはメソッドのパラメーターのマーシャ リング情報 PInvoke に設定します。</span><span class="sxs-lookup"><span data-stu-id="2b439-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b439-104">構文</span><span class="sxs-lookup"><span data-stu-id="2b439-104">Syntax</span></span>  
  
```  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,   
    [in]  PCCOR_SIGNATURE  pvNativeType,   
    [in]  ULONG            cbNativeType   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b439-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2b439-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="2b439-106">[in]ターゲット データ項目のトークンです。</span><span class="sxs-lookup"><span data-stu-id="2b439-106">[in] The token for target data item.</span></span> <span data-ttu-id="2b439-107">これは、いずれか、`mdFieldDef`または`mdParamDef`トークンです。</span><span class="sxs-lookup"><span data-stu-id="2b439-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="2b439-108">[in]アンマネージ型のシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="2b439-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="2b439-109">[in]内のバイト数`pvNativeType`です。</span><span class="sxs-lookup"><span data-stu-id="2b439-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b439-110">要件</span><span class="sxs-lookup"><span data-stu-id="2b439-110">Requirements</span></span>  
 <span data-ttu-id="2b439-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2b439-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b439-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2b439-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2b439-113">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="2b439-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2b439-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b439-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b439-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b439-115">See Also</span></span>  
 [<span data-ttu-id="2b439-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2b439-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="2b439-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2b439-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

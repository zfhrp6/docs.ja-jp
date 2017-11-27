---
title: "IMetaDataImport::GetTypeSpecFromToken メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetTypeSpecFromToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetTypeSpecFromToken
helpviewer_keywords:
- GetTypeSpecFromToken method [.NET Framework metadata]
- IMetaDataImport::GetTypeSpecFromToken method [.NET Framework metadata]
ms.assetid: ee518bda-3296-482e-a7b7-e9d51dd1a181
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 37a8c2580dad3e198290b72b49b0aacaf1804c25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="f4dae-102">IMetaDataImport::GetTypeSpecFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="f4dae-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="f4dae-103">指定したトークンが表すタイプ仕様のバイナリ メタデータ シグネチャを取得します。</span><span class="sxs-lookup"><span data-stu-id="f4dae-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4dae-104">構文</span><span class="sxs-lookup"><span data-stu-id="f4dae-104">Syntax</span></span>  
  
```  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4dae-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f4dae-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="f4dae-106">[in]要求されたメタデータ署名に関連付けられている TypeSpec トークンです。</span><span class="sxs-lookup"><span data-stu-id="f4dae-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="f4dae-107">[out]バイナリ メタデータ シグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f4dae-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="f4dae-108">[out]メタデータ署名のバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="f4dae-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4dae-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="f4dae-109">Return Value</span></span>  
 <span data-ttu-id="f4dae-110">成功または失敗を示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="f4dae-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="f4dae-111">FAILED マクロでは、エラーをテストできます。</span><span class="sxs-lookup"><span data-stu-id="f4dae-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4dae-112">要件</span><span class="sxs-lookup"><span data-stu-id="f4dae-112">Requirements</span></span>  
 <span data-ttu-id="f4dae-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f4dae-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4dae-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f4dae-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f4dae-115">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="f4dae-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f4dae-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4dae-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4dae-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4dae-117">See Also</span></span>  
 [<span data-ttu-id="f4dae-118">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4dae-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="f4dae-119">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4dae-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

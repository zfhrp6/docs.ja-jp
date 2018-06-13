---
title: IMetaDataImport::GetSigFromToken メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetSigFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetSigFromToken
helpviewer_keywords:
- IMetaDataImport::GetSigFromToken method [.NET Framework metadata]
- GetSigFromToken method [.NET Framework metadata]
ms.assetid: ab894dc4-f7b6-4afc-bfcb-582a4b7e53a2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f40fb2e94eac13211cf8ccf179904071a23f59ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447228"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="dd52e-102">IMetaDataImport::GetSigFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="dd52e-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="dd52e-103">指定したトークンに関連付けられているバイナリ メタデータ シグネチャを取得します。</span><span class="sxs-lookup"><span data-stu-id="dd52e-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd52e-104">構文</span><span class="sxs-lookup"><span data-stu-id="dd52e-104">Syntax</span></span>  
  
```  
HRESULT GetSigFromToken (   
   [in]   mdSignature        mdSig,   
   [out]  PCCOR_SIGNATURE    *ppvSig,   
   [out]  ULONG              *pcbSig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd52e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dd52e-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="dd52e-106">[in]バイナリ メタデータ シグネチャを返すトークンです。</span><span class="sxs-lookup"><span data-stu-id="dd52e-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="dd52e-107">[out]返されるメタデータ シグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dd52e-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="dd52e-108">[out]バイナリ メタデータ シグネチャのバイト サイズ。</span><span class="sxs-lookup"><span data-stu-id="dd52e-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd52e-109">要件</span><span class="sxs-lookup"><span data-stu-id="dd52e-109">Requirements</span></span>  
 <span data-ttu-id="dd52e-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dd52e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd52e-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dd52e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd52e-112">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="dd52e-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dd52e-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd52e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd52e-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd52e-114">See Also</span></span>  
 [<span data-ttu-id="dd52e-115">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd52e-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="dd52e-116">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd52e-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

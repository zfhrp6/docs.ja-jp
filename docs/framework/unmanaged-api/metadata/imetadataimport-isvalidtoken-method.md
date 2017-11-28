---
title: "IMetaDataImport::IsValidToken メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.IsValidToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3c916e71518ded93c90b270205dd975201762846
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="ebd67-102">IMetaDataImport::IsValidToken メソッド</span><span class="sxs-lookup"><span data-stu-id="ebd67-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="ebd67-103">指定したトークンが、コード オブジェクトへの有効な参照を保持しているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="ebd67-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebd67-104">構文</span><span class="sxs-lookup"><span data-stu-id="ebd67-104">Syntax</span></span>  
  
```  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ebd67-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ebd67-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="ebd67-106">[in]参照の有効性を確認するトークン。</span><span class="sxs-lookup"><span data-stu-id="ebd67-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ebd67-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="ebd67-107">Return Value</span></span>  
 <span data-ttu-id="ebd67-108">`true`場合`tk`現在のスコープ内で有効なメタデータ トークンします。</span><span class="sxs-lookup"><span data-stu-id="ebd67-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="ebd67-109">それ以外の場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="ebd67-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebd67-110">要件</span><span class="sxs-lookup"><span data-stu-id="ebd67-110">Requirements</span></span>  
 <span data-ttu-id="ebd67-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ebd67-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebd67-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ebd67-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ebd67-113">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="ebd67-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ebd67-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebd67-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebd67-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ebd67-115">See Also</span></span>  
 [<span data-ttu-id="ebd67-116">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ebd67-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="ebd67-117">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ebd67-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

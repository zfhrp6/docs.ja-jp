---
title: IMetaDataImport::GetUserString メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetUserString
helpviewer_keywords:
- IMetaDataImport::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0fd3bb47-58b5-4083-b241-b9719df7a285
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 474338ff1780ce9b442208cd06f8b14bc411be5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="52045-102">IMetaDataImport::GetUserString メソッド</span><span class="sxs-lookup"><span data-stu-id="52045-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="52045-103">指定したメタデータ トークンで表されるリテラル文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="52045-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52045-104">構文</span><span class="sxs-lookup"><span data-stu-id="52045-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52045-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="52045-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="52045-106">[in]関連付けられている文字列を返す文字列トークンです。</span><span class="sxs-lookup"><span data-stu-id="52045-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="52045-107">[out]要求された文字列のコピー。</span><span class="sxs-lookup"><span data-stu-id="52045-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="52045-108">[in]要求されたワイド文字の最大サイズ`szString`です。</span><span class="sxs-lookup"><span data-stu-id="52045-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="52045-109">[out]返されたのワイド文字単位のサイズ`szString`です。</span><span class="sxs-lookup"><span data-stu-id="52045-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52045-110">要件</span><span class="sxs-lookup"><span data-stu-id="52045-110">Requirements</span></span>  
 <span data-ttu-id="52045-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="52045-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52045-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="52045-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="52045-113">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="52045-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="52045-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52045-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52045-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="52045-115">See Also</span></span>  
 [<span data-ttu-id="52045-116">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52045-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="52045-117">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52045-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

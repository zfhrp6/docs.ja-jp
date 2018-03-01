---
title: "IMetaDataImport::GetUserString メソッド"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 944d7e6413f35ad56af38dee90dc90f881c1d4cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="d5cb0-102">IMetaDataImport::GetUserString メソッド</span><span class="sxs-lookup"><span data-stu-id="d5cb0-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="d5cb0-103">指定したメタデータ トークンで表されるリテラル文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="d5cb0-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5cb0-104">構文</span><span class="sxs-lookup"><span data-stu-id="d5cb0-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5cb0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d5cb0-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="d5cb0-106">[in]関連付けられている文字列を返す文字列トークンです。</span><span class="sxs-lookup"><span data-stu-id="d5cb0-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="d5cb0-107">[out]要求された文字列のコピー。</span><span class="sxs-lookup"><span data-stu-id="d5cb0-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="d5cb0-108">[in]要求されたワイド文字の最大サイズ`szString`です。</span><span class="sxs-lookup"><span data-stu-id="d5cb0-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="d5cb0-109">[out]返されたのワイド文字単位のサイズ`szString`です。</span><span class="sxs-lookup"><span data-stu-id="d5cb0-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5cb0-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="d5cb0-110">Requirements</span></span>  
 <span data-ttu-id="d5cb0-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d5cb0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5cb0-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d5cb0-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d5cb0-113">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d5cb0-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d5cb0-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5cb0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5cb0-115">参照</span><span class="sxs-lookup"><span data-stu-id="d5cb0-115">See Also</span></span>  
 [<span data-ttu-id="d5cb0-116">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5cb0-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="d5cb0-117">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5cb0-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

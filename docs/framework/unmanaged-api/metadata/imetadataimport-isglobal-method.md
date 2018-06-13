---
title: IMetaDataImport::IsGlobal メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsGlobal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsGlobal
helpviewer_keywords:
- IsGlobal method [.NET Framework metadata]
- IMetaDataImport::IsGlobal method [.NET Framework metadata]
ms.assetid: 44cf6908-f555-4ae8-b2cf-24bd974bf2fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4156c3507ccbd21d59893c5e03e15fe9b7322e48
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447799"
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="72325-102">IMetaDataImport::IsGlobal メソッド</span><span class="sxs-lookup"><span data-stu-id="72325-102">IMetaDataImport::IsGlobal Method</span></span>
<span data-ttu-id="72325-103">指定したメタデータ トークンによって表されるフィールド、メソッド、または型がグローバル スコープを保持しているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="72325-103">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72325-104">構文</span><span class="sxs-lookup"><span data-stu-id="72325-104">Syntax</span></span>  
  
```  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72325-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="72325-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="72325-106">[in]型、フィールド、またはメソッドを表すメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="72325-106">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="72325-107">[out] の場合は、1 オブジェクトがグローバル スコープです。それ以外の場合、0 (ゼロ)。</span><span class="sxs-lookup"><span data-stu-id="72325-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72325-108">要件</span><span class="sxs-lookup"><span data-stu-id="72325-108">Requirements</span></span>  
 <span data-ttu-id="72325-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="72325-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72325-110">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="72325-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="72325-111">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="72325-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="72325-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72325-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72325-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="72325-113">See Also</span></span>  
 [<span data-ttu-id="72325-114">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="72325-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="72325-115">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="72325-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

---
title: "IMetaDataImport::FindTypeDefByName メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindTypeDefByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindTypeDefByName
helpviewer_keywords:
- FindTypeDefByName method [.NET Framework metadata]
- IMetaDataImport::FindTypeDefByName method [.NET Framework metadata]
ms.assetid: f4c2cd88-ac28-4bad-9ab1-2cf9d2de41e6
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e4b3a5f9ff15e2b94e6d5c5e885605d8eabae711
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="5fd91-102">IMetaDataImport::FindTypeDefByName メソッド</span><span class="sxs-lookup"><span data-stu-id="5fd91-102">IMetaDataImport::FindTypeDefByName Method</span></span>
<span data-ttu-id="5fd91-103">トークンの TypeDef メタデータへのポインターを取得、<xref:System.Type>指定した名前です。</span><span class="sxs-lookup"><span data-stu-id="5fd91-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fd91-104">構文</span><span class="sxs-lookup"><span data-stu-id="5fd91-104">Syntax</span></span>  
  
```  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5fd91-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5fd91-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="5fd91-106">[in]TypeDef トークンを取得する対象の型の名前。</span><span class="sxs-lookup"><span data-stu-id="5fd91-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="5fd91-107">[in]外側のクラスを表す TypeDef または TypeRef トークンです。</span><span class="sxs-lookup"><span data-stu-id="5fd91-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="5fd91-108">検索する型が入れ子になったクラスでない場合は、この値を NULL に設定します。</span><span class="sxs-lookup"><span data-stu-id="5fd91-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="5fd91-109">[out]一致する TypeDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5fd91-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fd91-110">要件</span><span class="sxs-lookup"><span data-stu-id="5fd91-110">Requirements</span></span>  
 <span data-ttu-id="5fd91-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5fd91-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fd91-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5fd91-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5fd91-113">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="5fd91-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5fd91-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fd91-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fd91-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="5fd91-115">See Also</span></span>  
 [<span data-ttu-id="5fd91-116">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5fd91-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="5fd91-117">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5fd91-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

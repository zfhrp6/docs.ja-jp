---
title: "IMetaDataImport::GetNestedClassProps メソッド"
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
- IMetaDataImport.GetNestedClassProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNestedClassProps
helpviewer_keywords:
- GetNestedClassProps method [.NET Framework metadata]
- IMetaDataImport::GetNestedClassProps method [.NET Framework metadata]
ms.assetid: 704d19f1-bdef-4745-af8c-6476eb246fb3
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8bbfe382a9a2fdf8ece1015ee73c3d9ef604ec7e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="9fe95-102">IMetaDataImport::GetNestedClassProps メソッド</span><span class="sxs-lookup"><span data-stu-id="9fe95-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="9fe95-103">親の TypeDef トークンを取得<xref:System.Type>入れ子にされた型の指定しました。</span><span class="sxs-lookup"><span data-stu-id="9fe95-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fe95-104">構文</span><span class="sxs-lookup"><span data-stu-id="9fe95-104">Syntax</span></span>  
  
```  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9fe95-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9fe95-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="9fe95-106">[in]TypeDef トークンを表す、<xref:System.Type>親クラスを返すためにトークンです。</span><span class="sxs-lookup"><span data-stu-id="9fe95-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="9fe95-107">[out]TypeDef トークンへのポインター、<xref:System.Type>を`tdNestedClass`が入れ子になっています。</span><span class="sxs-lookup"><span data-stu-id="9fe95-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fe95-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="9fe95-108">Requirements</span></span>  
 <span data-ttu-id="9fe95-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9fe95-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fe95-110">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9fe95-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9fe95-111">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="9fe95-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9fe95-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fe95-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fe95-113">参照</span><span class="sxs-lookup"><span data-stu-id="9fe95-113">See Also</span></span>  
 [<span data-ttu-id="9fe95-114">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9fe95-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="9fe95-115">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9fe95-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

---
title: "IMetaDataImport::GetTypeRefProps メソッド"
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
- IMetaDataImport.GetTypeRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeRefProps
helpviewer_keywords:
- IMetaDataImport::GetTypeRefProps method [.NET Framework metadata]
- GetTypeRefProps method [.NET Framework metadata]
ms.assetid: 01837955-ce1e-4068-b338-fd473bd77d1d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 23dbfe2468088da5e02fb7156606af5f3fa51044
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="d810d-102">IMetaDataImport::GetTypeRefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="d810d-102">IMetaDataImport::GetTypeRefProps Method</span></span>
<span data-ttu-id="d810d-103">関連付けられているメタデータを取得、<xref:System.Type>指定した TypeRef トークンによって参照されています。</span><span class="sxs-lookup"><span data-stu-id="d810d-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d810d-104">構文</span><span class="sxs-lookup"><span data-stu-id="d810d-104">Syntax</span></span>  
  
```  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d810d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d810d-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="d810d-106">[in]メタデータを返す型を表す TypeRef トークンです。</span><span class="sxs-lookup"><span data-stu-id="d810d-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="d810d-107">[out]これで、参照が行われるスコープへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d810d-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="d810d-108">この値に AssemblyRef または ModuleRef トークンです。</span><span class="sxs-lookup"><span data-stu-id="d810d-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="d810d-109">[out]型名を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="d810d-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="d810d-110">[in]要求されたサイズのワイド文字単位`szName`です。</span><span class="sxs-lookup"><span data-stu-id="d810d-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="d810d-111">[out]ワイド文字で返されるサイズ`szName`です。</span><span class="sxs-lookup"><span data-stu-id="d810d-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d810d-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="d810d-112">Requirements</span></span>  
 <span data-ttu-id="d810d-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d810d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d810d-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d810d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d810d-115">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d810d-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d810d-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d810d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d810d-117">参照</span><span class="sxs-lookup"><span data-stu-id="d810d-117">See Also</span></span>  
 [<span data-ttu-id="d810d-118">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d810d-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="d810d-119">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d810d-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

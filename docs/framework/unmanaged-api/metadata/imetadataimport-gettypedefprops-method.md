---
title: "IMetaDataImport::GetTypeDefProps メソッド"
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
- IMetaDataImport.GetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f3e7f2c2fe602ef3464766b62ef12e8f83767bf4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="3a3bb-102">IMetaDataImport::GetTypeDefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="3a3bb-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="3a3bb-103">メタデータ情報を返します、<xref:System.Type>指定した TypeDef トークンによって表されます。</span><span class="sxs-lookup"><span data-stu-id="3a3bb-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a3bb-104">構文</span><span class="sxs-lookup"><span data-stu-id="3a3bb-104">Syntax</span></span>  
  
```  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3a3bb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3a3bb-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="3a3bb-106">[in]メタデータを返す型を表す TypeDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="3a3bb-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="3a3bb-107">[out]型名を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="3a3bb-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="3a3bb-108">[in]ワイド文字単位のサイズ`szTypeDef`です。</span><span class="sxs-lookup"><span data-stu-id="3a3bb-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="3a3bb-109">[out]ワイド文字数で返される`szTypeDef`です。</span><span class="sxs-lookup"><span data-stu-id="3a3bb-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="3a3bb-110">[out]型定義を変更するフラグのいずれかへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3a3bb-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="3a3bb-111">この値からビットマスクである、 [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="3a3bb-111">This value is a bitmask from the [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="3a3bb-112">[out]要求された型の基本型を表す TypeDef または TypeRef メタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="3a3bb-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a3bb-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="3a3bb-113">Requirements</span></span>  
 <span data-ttu-id="3a3bb-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3a3bb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a3bb-115">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3a3bb-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3a3bb-116">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="3a3bb-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3a3bb-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a3bb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a3bb-118">参照</span><span class="sxs-lookup"><span data-stu-id="3a3bb-118">See Also</span></span>  
 [<span data-ttu-id="3a3bb-119">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a3bb-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="3a3bb-120">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a3bb-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

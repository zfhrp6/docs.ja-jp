---
title: "IMetaDataImport::GetTypeDefProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetTypeDefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1025ffde2bd066c81c4c562c0dd86e829fc2aef3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="98ed0-102">IMetaDataImport::GetTypeDefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="98ed0-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="98ed0-103">メタデータ情報を返します、<xref:System.Type>指定した TypeDef トークンによって表されます。</span><span class="sxs-lookup"><span data-stu-id="98ed0-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98ed0-104">構文</span><span class="sxs-lookup"><span data-stu-id="98ed0-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="98ed0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="98ed0-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="98ed0-106">[in]メタデータを返す型を表す TypeDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="98ed0-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="98ed0-107">[out]型名を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="98ed0-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="98ed0-108">[in]ワイド文字単位のサイズ`szTypeDef`です。</span><span class="sxs-lookup"><span data-stu-id="98ed0-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="98ed0-109">[out]ワイド文字数で返される`szTypeDef`です。</span><span class="sxs-lookup"><span data-stu-id="98ed0-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="98ed0-110">[out]型定義を変更するフラグのいずれかへのポインター。</span><span class="sxs-lookup"><span data-stu-id="98ed0-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="98ed0-111">この値からビットマスクである、 [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="98ed0-111">This value is a bitmask from the [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="98ed0-112">[out]要求された型の基本型を表す TypeDef または TypeRef メタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="98ed0-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98ed0-113">要件</span><span class="sxs-lookup"><span data-stu-id="98ed0-113">Requirements</span></span>  
 <span data-ttu-id="98ed0-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="98ed0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98ed0-115">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="98ed0-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="98ed0-116">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="98ed0-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="98ed0-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98ed0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98ed0-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="98ed0-118">See Also</span></span>  
 [<span data-ttu-id="98ed0-119">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98ed0-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="98ed0-120">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98ed0-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

---
title: IMetaDataImport::GetTypeDefProps メソッド
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa69eda974187748d7046c792fa16b7729e3deff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446883"
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="11325-102">IMetaDataImport::GetTypeDefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="11325-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="11325-103">メタデータ情報を返します、<xref:System.Type>指定した TypeDef トークンによって表されます。</span><span class="sxs-lookup"><span data-stu-id="11325-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11325-104">構文</span><span class="sxs-lookup"><span data-stu-id="11325-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="11325-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="11325-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="11325-106">[in]メタデータを返す型を表す TypeDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="11325-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="11325-107">[out]型名を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="11325-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="11325-108">[in]ワイド文字単位のサイズ`szTypeDef`です。</span><span class="sxs-lookup"><span data-stu-id="11325-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="11325-109">[out]ワイド文字数で返される`szTypeDef`です。</span><span class="sxs-lookup"><span data-stu-id="11325-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="11325-110">[out]型定義を変更するフラグのいずれかへのポインター。</span><span class="sxs-lookup"><span data-stu-id="11325-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="11325-111">この値からビットマスクである、 [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="11325-111">This value is a bitmask from the [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="11325-112">[out]要求された型の基本型を表す TypeDef または TypeRef メタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="11325-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11325-113">要件</span><span class="sxs-lookup"><span data-stu-id="11325-113">Requirements</span></span>  
 <span data-ttu-id="11325-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="11325-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11325-115">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="11325-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="11325-116">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="11325-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="11325-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11325-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11325-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="11325-118">See Also</span></span>  
 [<span data-ttu-id="11325-119">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11325-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="11325-120">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11325-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

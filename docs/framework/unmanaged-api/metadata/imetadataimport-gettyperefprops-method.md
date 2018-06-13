---
title: IMetaDataImport::GetTypeRefProps メソッド
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 25482ee81d5210e5ab69007767aecf01435602d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448597"
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="849cd-102">IMetaDataImport::GetTypeRefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="849cd-102">IMetaDataImport::GetTypeRefProps Method</span></span>
<span data-ttu-id="849cd-103">関連付けられているメタデータを取得、<xref:System.Type>指定した TypeRef トークンによって参照されています。</span><span class="sxs-lookup"><span data-stu-id="849cd-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="849cd-104">構文</span><span class="sxs-lookup"><span data-stu-id="849cd-104">Syntax</span></span>  
  
```  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="849cd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="849cd-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="849cd-106">[in]メタデータを返す型を表す TypeRef トークンです。</span><span class="sxs-lookup"><span data-stu-id="849cd-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="849cd-107">[out]これで、参照が行われるスコープへのポインター。</span><span class="sxs-lookup"><span data-stu-id="849cd-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="849cd-108">この値に AssemblyRef または ModuleRef トークンです。</span><span class="sxs-lookup"><span data-stu-id="849cd-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="849cd-109">[out]型名を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="849cd-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="849cd-110">[in]要求されたサイズのワイド文字単位`szName`です。</span><span class="sxs-lookup"><span data-stu-id="849cd-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="849cd-111">[out]ワイド文字で返されるサイズ`szName`です。</span><span class="sxs-lookup"><span data-stu-id="849cd-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="849cd-112">要件</span><span class="sxs-lookup"><span data-stu-id="849cd-112">Requirements</span></span>  
 <span data-ttu-id="849cd-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="849cd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="849cd-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="849cd-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="849cd-115">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="849cd-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="849cd-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="849cd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="849cd-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="849cd-117">See Also</span></span>  
 [<span data-ttu-id="849cd-118">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="849cd-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="849cd-119">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="849cd-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

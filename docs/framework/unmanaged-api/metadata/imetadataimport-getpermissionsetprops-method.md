---
title: IMetaDataImport::GetPermissionSetProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPermissionSetProps
helpviewer_keywords:
- GetPermissionSetProps method [.NET Framework metadata]
- IMetaDataImport::GetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 9855f0e4-12c0-4d3d-ab5d-d6bc52d25eae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be9b2fa3037dc00bce52d9ff89291d1c02cffc38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449300"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="3a7a7-102">IMetaDataImport::GetPermissionSetProps メソッド</span><span class="sxs-lookup"><span data-stu-id="3a7a7-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="3a7a7-103">関連付けられているメタデータを取得、<xref:System.Security.PermissionSet?displayProperty=nameWithType>指定したアクセス許可のトークンによって表されます。</span><span class="sxs-lookup"><span data-stu-id="3a7a7-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a7a7-104">構文</span><span class="sxs-lookup"><span data-stu-id="3a7a7-104">Syntax</span></span>  
  
```  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,   
   [out] void const        **ppvPermission,   
   [out] ULONG             *pcbPermission  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3a7a7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3a7a7-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="3a7a7-106">[in]メタデータ プロパティを取得する設定のアクセス許可を表す権限メタデータ トークンです。</span><span class="sxs-lookup"><span data-stu-id="3a7a7-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="3a7a7-107">[out]権限セットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3a7a7-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="3a7a7-108">[out]アクセス許可セットのバイナリ メタデータ シグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3a7a7-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="3a7a7-109">[out]バイト サイズ`ppvPermission`です。</span><span class="sxs-lookup"><span data-stu-id="3a7a7-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a7a7-110">要件</span><span class="sxs-lookup"><span data-stu-id="3a7a7-110">Requirements</span></span>  
 <span data-ttu-id="3a7a7-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3a7a7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a7a7-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3a7a7-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3a7a7-113">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="3a7a7-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3a7a7-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a7a7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a7a7-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a7a7-115">See Also</span></span>  
 <xref:System.Security.PermissionSet>  
 [<span data-ttu-id="3a7a7-116">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a7a7-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="3a7a7-117">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a7a7-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

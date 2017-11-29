---
title: "IMetaDataImport::GetPermissionSetProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetPermissionSetProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetPermissionSetProps
helpviewer_keywords:
- GetPermissionSetProps method [.NET Framework metadata]
- IMetaDataImport::GetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 9855f0e4-12c0-4d3d-ab5d-d6bc52d25eae
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2556c0beee7a21d2f01c403ab141054e5bf68177
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="6b910-102">IMetaDataImport::GetPermissionSetProps メソッド</span><span class="sxs-lookup"><span data-stu-id="6b910-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="6b910-103">関連付けられているメタデータを取得、<xref:System.Security.PermissionSet?displayProperty=nameWithType>指定したアクセス許可のトークンによって表されます。</span><span class="sxs-lookup"><span data-stu-id="6b910-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b910-104">構文</span><span class="sxs-lookup"><span data-stu-id="6b910-104">Syntax</span></span>  
  
```  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,   
   [out] void const        **ppvPermission,   
   [out] ULONG             *pcbPermission  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b910-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6b910-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="6b910-106">[in]メタデータ プロパティを取得する設定のアクセス許可を表す権限メタデータ トークンです。</span><span class="sxs-lookup"><span data-stu-id="6b910-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="6b910-107">[out]権限セットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6b910-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="6b910-108">[out]アクセス許可セットのバイナリ メタデータ シグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6b910-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="6b910-109">[out]バイト サイズ`ppvPermission`です。</span><span class="sxs-lookup"><span data-stu-id="6b910-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b910-110">要件</span><span class="sxs-lookup"><span data-stu-id="6b910-110">Requirements</span></span>  
 <span data-ttu-id="6b910-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6b910-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b910-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6b910-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6b910-113">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="6b910-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6b910-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b910-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b910-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b910-115">See Also</span></span>  
 <xref:System.Security.PermissionSet>  
 [<span data-ttu-id="6b910-116">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b910-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="6b910-117">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b910-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

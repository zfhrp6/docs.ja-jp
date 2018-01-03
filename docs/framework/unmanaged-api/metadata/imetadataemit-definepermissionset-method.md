---
title: "IMetaDataEmit::DefinePermissionSet メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefinePermissionSet
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 74bea316d3f56e007c4b75e6b801d8c82ae8ce96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="deadc-102">IMetaDataEmit::DefinePermissionSet メソッド</span><span class="sxs-lookup"><span data-stu-id="deadc-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="deadc-103">アクセス許可が、指定したメタデータ シグネチャを持つ、設定の定義を作成し、そのアクセス許可セットの定義にトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="deadc-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deadc-104">構文</span><span class="sxs-lookup"><span data-stu-id="deadc-104">Syntax</span></span>  
  
```  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="deadc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="deadc-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="deadc-106">[in]装飾するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="deadc-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="deadc-107">[in]A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md)を使用する宣言型セキュリティの種類を示す値。</span><span class="sxs-lookup"><span data-stu-id="deadc-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="deadc-108">[in]アクセス許可 BLOB。</span><span class="sxs-lookup"><span data-stu-id="deadc-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="deadc-109">[in]サイズをバイト単位での`pvPermission`します。</span><span class="sxs-lookup"><span data-stu-id="deadc-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="deadc-110">[out]返されるアクセス許可のトークンです。</span><span class="sxs-lookup"><span data-stu-id="deadc-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="deadc-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="deadc-111">Requirements</span></span>  
 <span data-ttu-id="deadc-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="deadc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="deadc-113">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="deadc-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="deadc-114">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="deadc-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="deadc-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="deadc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deadc-116">参照</span><span class="sxs-lookup"><span data-stu-id="deadc-116">See Also</span></span>  
 [<span data-ttu-id="deadc-117">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="deadc-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="deadc-118">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="deadc-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

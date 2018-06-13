---
title: IMetaDataEmit::DefinePermissionSet メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePermissionSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 05339787b112ad029cb9870e8c6ffca37e55e631
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445190"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="20d7f-102">IMetaDataEmit::DefinePermissionSet メソッド</span><span class="sxs-lookup"><span data-stu-id="20d7f-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="20d7f-103">アクセス許可が、指定したメタデータ シグネチャを持つ、設定の定義を作成し、そのアクセス許可セットの定義にトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="20d7f-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20d7f-104">構文</span><span class="sxs-lookup"><span data-stu-id="20d7f-104">Syntax</span></span>  
  
```  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20d7f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="20d7f-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="20d7f-106">[in]装飾するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="20d7f-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="20d7f-107">[in]A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md)を使用する宣言型セキュリティの種類を示す値。</span><span class="sxs-lookup"><span data-stu-id="20d7f-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="20d7f-108">[in]アクセス許可 BLOB。</span><span class="sxs-lookup"><span data-stu-id="20d7f-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="20d7f-109">[in]サイズをバイト単位での`pvPermission`します。</span><span class="sxs-lookup"><span data-stu-id="20d7f-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="20d7f-110">[out]返されるアクセス許可のトークンです。</span><span class="sxs-lookup"><span data-stu-id="20d7f-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20d7f-111">要件</span><span class="sxs-lookup"><span data-stu-id="20d7f-111">Requirements</span></span>  
 <span data-ttu-id="20d7f-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="20d7f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20d7f-113">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="20d7f-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="20d7f-114">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="20d7f-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20d7f-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20d7f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20d7f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="20d7f-116">See Also</span></span>  
 [<span data-ttu-id="20d7f-117">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20d7f-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="20d7f-118">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20d7f-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

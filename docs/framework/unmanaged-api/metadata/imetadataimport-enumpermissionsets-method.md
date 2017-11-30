---
title: "IMetaDataImport::EnumPermissionSets メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumPermissionSets
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumPermissionSets
helpviewer_keywords:
- EnumPermissionSets method [.NET Framework metadata]
- IMetaDataImport::EnumPermissionSets method [.NET Framework metadata]
ms.assetid: 347d7e5c-c90f-45ad-bd1e-2c7912b0b19c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 031e97ad1b8180a64bc789ae52e141932d600782
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="9e2e1-102">IMetaDataImport::EnumPermissionSets メソッド</span><span class="sxs-lookup"><span data-stu-id="9e2e1-102">IMetaDataImport::EnumPermissionSets Method</span></span>
<span data-ttu-id="9e2e1-103">指定したメタデータ スコープ内のオブジェクトのアクセス許可を列挙します。</span><span class="sxs-lookup"><span data-stu-id="9e2e1-103">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e2e1-104">構文</span><span class="sxs-lookup"><span data-stu-id="9e2e1-104">Syntax</span></span>  
  
```  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,   
   [in]      mdToken       tk,   
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e2e1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9e2e1-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="9e2e1-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9e2e1-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="9e2e1-107">このメソッドの最初の呼び出しで NULL があります。</span><span class="sxs-lookup"><span data-stu-id="9e2e1-107">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="9e2e1-108">[in]可能な最も幅の広いスコープを検索する検索のスコープを制限するメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="9e2e1-108">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="9e2e1-109">[in]フラグを表す、<xref:System.Security.Permissions.SecurityAction>に含める値`rPermission`、すべてのアクションを返すには 0 です。</span><span class="sxs-lookup"><span data-stu-id="9e2e1-109">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="9e2e1-110">[out]アクセス許可のトークンの保存に使用する配列。</span><span class="sxs-lookup"><span data-stu-id="9e2e1-110">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9e2e1-111">[in] `rPermission` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="9e2e1-111">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="9e2e1-112">[out]返されるアクセス許可のトークン数`rPermission`です。</span><span class="sxs-lookup"><span data-stu-id="9e2e1-112">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e2e1-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="9e2e1-113">Return Value</span></span>  
  
|<span data-ttu-id="9e2e1-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9e2e1-114">HRESULT</span></span>|<span data-ttu-id="9e2e1-115">説明</span><span class="sxs-lookup"><span data-stu-id="9e2e1-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9e2e1-116">`EnumPermissionSets`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="9e2e1-116">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9e2e1-117">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="9e2e1-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="9e2e1-118">その場合は、`pcTokens`ゼロです。</span><span class="sxs-lookup"><span data-stu-id="9e2e1-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9e2e1-119">要件</span><span class="sxs-lookup"><span data-stu-id="9e2e1-119">Requirements</span></span>  
 <span data-ttu-id="9e2e1-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9e2e1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e2e1-121">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9e2e1-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9e2e1-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="9e2e1-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9e2e1-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e2e1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e2e1-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e2e1-124">See Also</span></span>  
 [<span data-ttu-id="9e2e1-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9e2e1-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="9e2e1-126">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9e2e1-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

---
title: "IMetaDataImport::GetRVA メソッド"
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
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6c055afaa129b52c67cd0463a5d44afec5cde103
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="26869-102">IMetaDataImport::GetRVA メソッド</span><span class="sxs-lookup"><span data-stu-id="26869-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="26869-103">相対仮想アドレス (RVA) と、メソッド、または指定したトークンによって表されるフィールドの実装フラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="26869-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26869-104">構文</span><span class="sxs-lookup"><span data-stu-id="26869-104">Syntax</span></span>  
  
```  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26869-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26869-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="26869-106">[in]RVA を返すコード オブジェクトを表す MethodDef または FieldDef メタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="26869-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="26869-107">トークンが、FieldDef の場合は、フィールドは、グローバル変数にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="26869-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="26869-108">[out]トークンが表すコード オブジェクトの相対仮想アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26869-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="26869-109">[out]このメソッドの実装フラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26869-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="26869-110">この値からビットマスクである、 [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="26869-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="26869-111">値`pdwImplFlags`は有効な場合にのみ、 `tk` MethodDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="26869-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26869-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="26869-112">Requirements</span></span>  
 <span data-ttu-id="26869-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="26869-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26869-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="26869-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="26869-115">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="26869-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="26869-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26869-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26869-117">参照</span><span class="sxs-lookup"><span data-stu-id="26869-117">See Also</span></span>  
 [<span data-ttu-id="26869-118">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="26869-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="26869-119">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="26869-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

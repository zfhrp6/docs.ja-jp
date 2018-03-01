---
title: "IMetaDataImport::GetNameFromToken メソッド"
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
- IMetaDataImport.GetNameFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: baa0c0e78f7912561b432effd2bf5503e0f06ae7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="6b8b4-102">IMetaDataImport::GetNameFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="6b8b4-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="6b8b4-103">指定したメタデータ トークンによって参照されるオブジェクトの UTF-8 名を取得します。</span><span class="sxs-lookup"><span data-stu-id="6b8b4-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="6b8b4-104">このメソッドは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="6b8b4-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b8b4-105">構文</span><span class="sxs-lookup"><span data-stu-id="6b8b4-105">Syntax</span></span>  
  
```  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b8b4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6b8b4-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="6b8b4-107">[in]名前を取得するオブジェクトを表すトークンです。</span><span class="sxs-lookup"><span data-stu-id="6b8b4-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="6b8b4-108">[out]ヒープで utf-8 オブジェクト名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6b8b4-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b8b4-109">コメント</span><span class="sxs-lookup"><span data-stu-id="6b8b4-109">Remarks</span></span>  
 <span data-ttu-id="6b8b4-110">`GetNameFromToken` は互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="6b8b4-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="6b8b4-111">代わりに、トークンが必要ななどの特定の種類のプロパティを取得するメソッドを呼び出す`GetFieldProps`フィールドまたは`GetMethodProps`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="6b8b4-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b8b4-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="6b8b4-112">Requirements</span></span>  
 <span data-ttu-id="6b8b4-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6b8b4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b8b4-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6b8b4-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6b8b4-115">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="6b8b4-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6b8b4-116">**.NET framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="6b8b4-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b8b4-117">参照</span><span class="sxs-lookup"><span data-stu-id="6b8b4-117">See Also</span></span>  
 [<span data-ttu-id="6b8b4-118">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b8b4-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="6b8b4-119">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b8b4-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

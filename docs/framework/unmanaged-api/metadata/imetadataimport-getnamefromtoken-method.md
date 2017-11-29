---
title: "IMetaDataImport::GetNameFromToken メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetNameFromToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e77954d5730417a005c6c1ac07fa171bd0f1b13a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="73de8-102">IMetaDataImport::GetNameFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="73de8-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="73de8-103">指定したメタデータ トークンによって参照されるオブジェクトの UTF-8 名を取得します。</span><span class="sxs-lookup"><span data-stu-id="73de8-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="73de8-104">このメソッドは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="73de8-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73de8-105">構文</span><span class="sxs-lookup"><span data-stu-id="73de8-105">Syntax</span></span>  
  
```  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73de8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="73de8-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="73de8-107">[in]名前を取得するオブジェクトを表すトークンです。</span><span class="sxs-lookup"><span data-stu-id="73de8-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="73de8-108">[out]ヒープで utf-8 オブジェクト名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="73de8-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73de8-109">コメント</span><span class="sxs-lookup"><span data-stu-id="73de8-109">Remarks</span></span>  
 <span data-ttu-id="73de8-110">`GetNameFromToken` は互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="73de8-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="73de8-111">代わりに、トークンが必要ななどの特定の種類のプロパティを取得するメソッドを呼び出す`GetFieldProps`フィールドまたは`GetMethodProps`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="73de8-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73de8-112">要件</span><span class="sxs-lookup"><span data-stu-id="73de8-112">Requirements</span></span>  
 <span data-ttu-id="73de8-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="73de8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73de8-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="73de8-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="73de8-115">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="73de8-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="73de8-116">**.NET framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="73de8-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73de8-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="73de8-117">See Also</span></span>  
 [<span data-ttu-id="73de8-118">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="73de8-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="73de8-119">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="73de8-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

---
title: "IMetaDataEmit2::DefineMethodSpec メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.DefineMethodSpec
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::DefineMethodSpec
helpviewer_keywords:
- DefineMethodSpec method [.NET Framework metadata]
- IMetaDataEmit2::DefineMethodSpec method [.NET Framework metadata]
ms.assetid: 3c24e552-fc69-4971-b65a-a3e4b5f7f1e8
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 036654c733dc73d40c526bf5cad4dd3750e2e9d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="2f856-102">IMetaDataEmit2::DefineMethodSpec メソッド</span><span class="sxs-lookup"><span data-stu-id="2f856-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="2f856-103">メソッドのジェネリックのインスタンスを作成し、定義にトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="2f856-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f856-104">構文</span><span class="sxs-lookup"><span data-stu-id="2f856-104">Syntax</span></span>  
  
```  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMethodSpec      *pmi  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2f856-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2f856-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="2f856-106">[in]ジェネリックのインスタンスを作成する対象のメソッドのトークンです。</span><span class="sxs-lookup"><span data-stu-id="2f856-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="2f856-107">トークン型でなければなりません`mdMethodDef`または`mdMemberRef`です。</span><span class="sxs-lookup"><span data-stu-id="2f856-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="2f856-108">[in]バイナリ COM + メソッドのシグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2f856-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="2f856-109">[in]サイズをバイト単位での`pvSigBlob`します。</span><span class="sxs-lookup"><span data-stu-id="2f856-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="2f856-110">[out]メソッドのメタデータ署名の定義をトークンです。</span><span class="sxs-lookup"><span data-stu-id="2f856-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f856-111">要件</span><span class="sxs-lookup"><span data-stu-id="2f856-111">Requirements</span></span>  
 <span data-ttu-id="2f856-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f856-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f856-113">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2f856-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2f856-114">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="2f856-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2f856-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f856-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f856-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f856-116">See Also</span></span>  
 [<span data-ttu-id="2f856-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2f856-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="2f856-118">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2f856-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)

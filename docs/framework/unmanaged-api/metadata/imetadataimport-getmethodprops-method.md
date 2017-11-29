---
title: "IMetaDataImport::GetMethodProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetMethodProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d02369f1e401f49548f4fdb0fc177dc7403654d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetmethodprops-method"></a><span data-ttu-id="d4729-102">IMetaDataImport::GetMethodProps メソッド</span><span class="sxs-lookup"><span data-stu-id="d4729-102">IMetaDataImport::GetMethodProps Method</span></span>
<span data-ttu-id="d4729-103">指定した MethodDef トークンによって参照されるメソッドに関連付けられているメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="d4729-103">Gets the metadata associated with the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4729-104">構文</span><span class="sxs-lookup"><span data-stu-id="d4729-104">Syntax</span></span>  
  
```  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4729-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d4729-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="d4729-106">[in]メタデータを返すメソッドを表す MethodDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="d4729-106">[in] The MethodDef token that represents the method to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="d4729-107">[out]メソッドを実装する型を表す TypeDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d4729-107">[out] A Pointer to a TypeDef token that represents the type that implements the method.</span></span>  
  
 `szMethod`  
 <span data-ttu-id="d4729-108">[out]メソッドの名前を持つバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d4729-108">[out] A Pointer to a buffer that has the method's name.</span></span>  
  
 `cchMethod`  
 <span data-ttu-id="d4729-109">[in]要求されたサイズの`szMethod`します。</span><span class="sxs-lookup"><span data-stu-id="d4729-109">[in] The requested size of `szMethod`.</span></span>  
  
 `pchMethod`  
 <span data-ttu-id="d4729-110">[out]ワイド文字単位のサイズへのポインター`szMethod`切り捨て、メソッド名でのワイド文字の実際の数の場合。</span><span class="sxs-lookup"><span data-stu-id="d4729-110">[out] A Pointer to the size in wide characters of `szMethod`, or in the case of truncation, the actual number of wide characters in the method name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="d4729-111">[out]メソッドに関連付けられているフラグのいずれかへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d4729-111">[out] A pointer to any flags associated with the method.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="d4729-112">[out]メソッドのバイナリ メタデータ シグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d4729-112">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="d4729-113">[out]サイズのバイト数へのポインター`ppvSigBlob`です。</span><span class="sxs-lookup"><span data-stu-id="d4729-113">[out] A Pointer to the size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="d4729-114">[out]メソッドの相対仮想アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d4729-114">[out] A pointer to the relative virtual address of the method.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="d4729-115">[out]メソッドの実装フラグのいずれかへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d4729-115">[out] A pointer to any implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4729-116">要件</span><span class="sxs-lookup"><span data-stu-id="d4729-116">Requirements</span></span>  
 <span data-ttu-id="d4729-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d4729-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4729-118">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d4729-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d4729-119">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d4729-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d4729-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4729-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4729-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4729-121">See Also</span></span>  
 [<span data-ttu-id="d4729-122">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d4729-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="d4729-123">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d4729-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

---
title: IMetaDataImport::GetMethodProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4037ca42c5a66f075e949cd2035c1e7db510bb8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448910"
---
# <a name="imetadataimportgetmethodprops-method"></a><span data-ttu-id="ffbb3-102">IMetaDataImport::GetMethodProps メソッド</span><span class="sxs-lookup"><span data-stu-id="ffbb3-102">IMetaDataImport::GetMethodProps Method</span></span>
<span data-ttu-id="ffbb3-103">指定した MethodDef トークンによって参照されるメソッドに関連付けられているメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="ffbb3-103">Gets the metadata associated with the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffbb3-104">構文</span><span class="sxs-lookup"><span data-stu-id="ffbb3-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="ffbb3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ffbb3-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="ffbb3-106">[in]メタデータを返すメソッドを表す MethodDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="ffbb3-106">[in] The MethodDef token that represents the method to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="ffbb3-107">[out]メソッドを実装する型を表す TypeDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ffbb3-107">[out] A Pointer to a TypeDef token that represents the type that implements the method.</span></span>  
  
 `szMethod`  
 <span data-ttu-id="ffbb3-108">[out]メソッドの名前を持つバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ffbb3-108">[out] A Pointer to a buffer that has the method's name.</span></span>  
  
 `cchMethod`  
 <span data-ttu-id="ffbb3-109">[in]要求されたサイズの`szMethod`します。</span><span class="sxs-lookup"><span data-stu-id="ffbb3-109">[in] The requested size of `szMethod`.</span></span>  
  
 `pchMethod`  
 <span data-ttu-id="ffbb3-110">[out]ワイド文字単位のサイズへのポインター`szMethod`切り捨て、メソッド名でのワイド文字の実際の数の場合。</span><span class="sxs-lookup"><span data-stu-id="ffbb3-110">[out] A Pointer to the size in wide characters of `szMethod`, or in the case of truncation, the actual number of wide characters in the method name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="ffbb3-111">[out]メソッドに関連付けられているフラグのいずれかへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ffbb3-111">[out] A pointer to any flags associated with the method.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="ffbb3-112">[out]メソッドのバイナリ メタデータ シグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ffbb3-112">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="ffbb3-113">[out]サイズのバイト数へのポインター`ppvSigBlob`です。</span><span class="sxs-lookup"><span data-stu-id="ffbb3-113">[out] A Pointer to the size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="ffbb3-114">[out]メソッドの相対仮想アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ffbb3-114">[out] A pointer to the relative virtual address of the method.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="ffbb3-115">[out]メソッドの実装フラグのいずれかへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ffbb3-115">[out] A pointer to any implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffbb3-116">要件</span><span class="sxs-lookup"><span data-stu-id="ffbb3-116">Requirements</span></span>  
 <span data-ttu-id="ffbb3-117">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ffbb3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffbb3-118">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ffbb3-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ffbb3-119">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="ffbb3-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ffbb3-120">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffbb3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffbb3-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="ffbb3-121">See Also</span></span>  
 [<span data-ttu-id="ffbb3-122">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ffbb3-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="ffbb3-123">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ffbb3-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

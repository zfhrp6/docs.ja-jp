---
title: IMetaDataImport2::GetMethodSpecProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetMethodSpecProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetMethodSpecProps
helpviewer_keywords:
- GetMethodSpecProps method [.NET Framework metadata]
- IMetaDataImport2::GetMethodSpecProps method [.NET Framework metadata]
ms.assetid: 9544b711-e669-4eaf-8630-ee862e5e4489
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3249ad76c428752c91540e135bc978d3fe835de1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448134"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="fac66-102">IMetaDataImport2::GetMethodSpecProps メソッド</span><span class="sxs-lookup"><span data-stu-id="fac66-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="fac66-103">指定した MethodSpec によって参照されるメソッドのメタデータ署名のトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="fac66-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fac66-104">構文</span><span class="sxs-lookup"><span data-stu-id="fac66-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,   
   [out] ULONG            *pcbSigBlob  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="fac66-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fac66-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="fac66-106">[in]メソッドのインスタンス化を表す MethodSpec トークンです。</span><span class="sxs-lookup"><span data-stu-id="fac66-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="fac66-107">[out]メソッドの定義を表す MethodDef または新しいトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fac66-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="fac66-108">[out]メソッドのバイナリ メタデータ シグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fac66-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="fac66-109">[out]サイズをバイト単位での`ppvSigBlob`します。</span><span class="sxs-lookup"><span data-stu-id="fac66-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fac66-110">要件</span><span class="sxs-lookup"><span data-stu-id="fac66-110">Requirements</span></span>  
 <span data-ttu-id="fac66-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fac66-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fac66-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fac66-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fac66-113">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="fac66-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fac66-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fac66-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fac66-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="fac66-115">See Also</span></span>  
 [<span data-ttu-id="fac66-116">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fac66-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="fac66-117">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fac66-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)

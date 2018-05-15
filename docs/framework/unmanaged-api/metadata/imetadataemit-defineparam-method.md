---
title: IMetaDataEmit::DefineParam メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5d49ac70aceb76f69711ea4bf514f69697ac156c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="e3489-102">IMetaDataEmit::DefineParam メソッド</span><span class="sxs-lookup"><span data-stu-id="e3489-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="e3489-103">指定したトークンによって参照されるメソッドの指定したシグネチャを持つパラメーターの定義を作成し、そのパラメーターの定義のトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="e3489-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3489-104">構文</span><span class="sxs-lookup"><span data-stu-id="e3489-104">Syntax</span></span>  
  
```  
HRESULT DefineParam (  
    [in]  mdMethodDef md,   
    [in]  ULONG       ulParamSeq,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,   
    [out] mdParamDef  *ppd   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3489-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e3489-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="e3489-106">[in]パラメーターを持つが定義されているメソッドのトークン。</span><span class="sxs-lookup"><span data-stu-id="e3489-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="e3489-107">[in]パラメーターのシーケンス番号。</span><span class="sxs-lookup"><span data-stu-id="e3489-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="e3489-108">[in]Unicode のパラメーターの名前です。</span><span class="sxs-lookup"><span data-stu-id="e3489-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="e3489-109">[in]パラメーターのフラグ。</span><span class="sxs-lookup"><span data-stu-id="e3489-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="e3489-110">これは、ビットマスク`CorParamAttr`値。</span><span class="sxs-lookup"><span data-stu-id="e3489-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="e3489-111">[in]`ELEMENT_TYPE_` *\** 定数値にします。</span><span class="sxs-lookup"><span data-stu-id="e3489-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="e3489-112">[in]パラメーターの定数値。</span><span class="sxs-lookup"><span data-stu-id="e3489-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="e3489-113">[in]Unicode 文字のサイズの`pValue`します。</span><span class="sxs-lookup"><span data-stu-id="e3489-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="e3489-114">[out]`mdParamDef`トークンが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="e3489-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3489-115">コメント</span><span class="sxs-lookup"><span data-stu-id="e3489-115">Remarks</span></span>  
 <span data-ttu-id="e3489-116">値がシーケンス`ulParamSeq`パラメーターの 1 から始まります。</span><span class="sxs-lookup"><span data-stu-id="e3489-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="e3489-117">戻り値は、シーケンス番号は 0 です。</span><span class="sxs-lookup"><span data-stu-id="e3489-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3489-118">要件</span><span class="sxs-lookup"><span data-stu-id="e3489-118">Requirements</span></span>  
 <span data-ttu-id="e3489-119">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e3489-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3489-120">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e3489-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e3489-121">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="e3489-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3489-122">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3489-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3489-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3489-123">See Also</span></span>  
 [<span data-ttu-id="e3489-124">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e3489-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="e3489-125">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e3489-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

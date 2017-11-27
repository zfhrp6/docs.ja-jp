---
title: "IMetaDataEmit::DefineParam メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineParam
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5abe9cf0385a42645468bf58c2f81223ac4eeead
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="19835-102">IMetaDataEmit::DefineParam メソッド</span><span class="sxs-lookup"><span data-stu-id="19835-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="19835-103">指定したトークンによって参照されるメソッドの指定したシグネチャを持つパラメーターの定義を作成し、そのパラメーターの定義のトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="19835-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19835-104">構文</span><span class="sxs-lookup"><span data-stu-id="19835-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="19835-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="19835-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="19835-106">[in]パラメーターを持つが定義されているメソッドのトークン。</span><span class="sxs-lookup"><span data-stu-id="19835-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="19835-107">[in]パラメーターのシーケンス番号。</span><span class="sxs-lookup"><span data-stu-id="19835-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="19835-108">[in]Unicode のパラメーターの名前です。</span><span class="sxs-lookup"><span data-stu-id="19835-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="19835-109">[in]パラメーターのフラグ。</span><span class="sxs-lookup"><span data-stu-id="19835-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="19835-110">これは、ビットマスク`CorParamAttr`値。</span><span class="sxs-lookup"><span data-stu-id="19835-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="19835-111">[in]`ELEMENT_TYPE_`  *\** 定数値にします。</span><span class="sxs-lookup"><span data-stu-id="19835-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="19835-112">[in]パラメーターの定数値。</span><span class="sxs-lookup"><span data-stu-id="19835-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="19835-113">[in]Unicode 文字のサイズの`pValue`します。</span><span class="sxs-lookup"><span data-stu-id="19835-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="19835-114">[out]`mdParamDef`トークンが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="19835-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19835-115">コメント</span><span class="sxs-lookup"><span data-stu-id="19835-115">Remarks</span></span>  
 <span data-ttu-id="19835-116">値がシーケンス`ulParamSeq`パラメーターの 1 から始まります。</span><span class="sxs-lookup"><span data-stu-id="19835-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="19835-117">戻り値は、シーケンス番号は 0 です。</span><span class="sxs-lookup"><span data-stu-id="19835-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19835-118">要件</span><span class="sxs-lookup"><span data-stu-id="19835-118">Requirements</span></span>  
 <span data-ttu-id="19835-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="19835-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19835-120">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="19835-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="19835-121">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="19835-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19835-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19835-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19835-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="19835-123">See Also</span></span>  
 [<span data-ttu-id="19835-124">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="19835-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="19835-125">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="19835-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

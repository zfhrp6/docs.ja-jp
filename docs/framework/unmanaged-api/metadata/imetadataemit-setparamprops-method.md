---
title: "IMetaDataEmit::SetParamProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetParamProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetParamProps
helpviewer_keywords:
- IMetaDataEmit::SetParamProps method [.NET Framework metadata]
- SetParamProps method [.NET Framework metadata]
ms.assetid: a95a3908-9f87-4084-937e-8e01ef03ad63
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ac76a9af6839ea08169c8b9c143fa96066e954ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="f9b7d-102">IMetaDataEmit::SetParamProps メソッド</span><span class="sxs-lookup"><span data-stu-id="f9b7d-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="f9b7d-103">前回の呼び出しで定義されているメソッドのパラメーターの機能の変更を設定または[imetadataemit::defineparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="f9b7d-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9b7d-104">構文</span><span class="sxs-lookup"><span data-stu-id="f9b7d-104">Syntax</span></span>  
  
```  
HRESULT SetParamProps (   
    [in]  mdParamDef  pd,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9b7d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f9b7d-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="f9b7d-106">[in]ターゲット パラメーターのトークン。</span><span class="sxs-lookup"><span data-stu-id="f9b7d-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="f9b7d-107">[in]Unicode のパラメーターの名前です。</span><span class="sxs-lookup"><span data-stu-id="f9b7d-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="f9b7d-108">[in]パラメーターのフラグ。</span><span class="sxs-lookup"><span data-stu-id="f9b7d-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="f9b7d-109">[in]ELEMENT_TYPE * 定数の値にします。</span><span class="sxs-lookup"><span data-stu-id="f9b7d-109">[in] The ELEMENT_TYPE_* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="f9b7d-110">[in]パラメーターの定数値。</span><span class="sxs-lookup"><span data-stu-id="f9b7d-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="f9b7d-111">[in]サイズ (Unicode) 文字の`pValue`します。</span><span class="sxs-lookup"><span data-stu-id="f9b7d-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9b7d-112">要件</span><span class="sxs-lookup"><span data-stu-id="f9b7d-112">Requirements</span></span>  
 <span data-ttu-id="f9b7d-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f9b7d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9b7d-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f9b7d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f9b7d-115">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="f9b7d-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9b7d-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9b7d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9b7d-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9b7d-117">See Also</span></span>  
 [<span data-ttu-id="f9b7d-118">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9b7d-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f9b7d-119">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9b7d-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

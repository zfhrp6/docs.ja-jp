---
title: IMetaDataEmit::SetParamProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParamProps
helpviewer_keywords:
- IMetaDataEmit::SetParamProps method [.NET Framework metadata]
- SetParamProps method [.NET Framework metadata]
ms.assetid: a95a3908-9f87-4084-937e-8e01ef03ad63
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 61688ed5201a1bb6721c4db70b380c7b8373c2e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446442"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="6973c-102">IMetaDataEmit::SetParamProps メソッド</span><span class="sxs-lookup"><span data-stu-id="6973c-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="6973c-103">前回の呼び出しで定義されているメソッドのパラメーターの機能の変更を設定または[imetadataemit::defineparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="6973c-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6973c-104">構文</span><span class="sxs-lookup"><span data-stu-id="6973c-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="6973c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6973c-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="6973c-106">[in]ターゲット パラメーターのトークン。</span><span class="sxs-lookup"><span data-stu-id="6973c-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="6973c-107">[in]Unicode のパラメーターの名前です。</span><span class="sxs-lookup"><span data-stu-id="6973c-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="6973c-108">[in]パラメーターのフラグ。</span><span class="sxs-lookup"><span data-stu-id="6973c-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="6973c-109">[in]ELEMENT_TYPE \* 定数の値にします。</span><span class="sxs-lookup"><span data-stu-id="6973c-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="6973c-110">[in]パラメーターの定数値。</span><span class="sxs-lookup"><span data-stu-id="6973c-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="6973c-111">[in]サイズ (Unicode) 文字の`pValue`します。</span><span class="sxs-lookup"><span data-stu-id="6973c-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6973c-112">要件</span><span class="sxs-lookup"><span data-stu-id="6973c-112">Requirements</span></span>  
 <span data-ttu-id="6973c-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6973c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6973c-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6973c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6973c-115">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="6973c-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6973c-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6973c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6973c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="6973c-117">See Also</span></span>  
 [<span data-ttu-id="6973c-118">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6973c-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="6973c-119">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6973c-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

---
title: IMetaDataImport::GetMethodSemantics メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodSemantics
helpviewer_keywords:
- GetMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::GetMethodSemantics method [.NET Framework metadata]
ms.assetid: 5e018eaa-d60e-4a0b-a2c5-8c36bd09d905
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4f4908f5d03687fb415c91325941aaab148832dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447743"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="919c3-102">IMetaDataImport::GetMethodSemantics メソッド</span><span class="sxs-lookup"><span data-stu-id="919c3-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="919c3-103">トークンの指定した MethodDef トークンと対になったプロパティによって参照されるメソッドと、指定した EventProp によって参照されるイベントの間の関係を示すフラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="919c3-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="919c3-104">構文</span><span class="sxs-lookup"><span data-stu-id="919c3-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="919c3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="919c3-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="919c3-106">[in]セマンティック ロール情報を取得するメソッドを表す MethodDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="919c3-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="919c3-107">[in]ペアのプロパティとメソッドのロールを取得する対象のイベントを表すトークンです。</span><span class="sxs-lookup"><span data-stu-id="919c3-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="919c3-108">[out]関連付けられたセマンティクス フラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="919c3-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="919c3-109">この値からビットマスクである、 [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="919c3-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="919c3-110">コメント</span><span class="sxs-lookup"><span data-stu-id="919c3-110">Remarks</span></span>  
 <span data-ttu-id="919c3-111">[Imetadataemit::defineproperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)メソッドは、メソッドのセマンティクスのフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="919c3-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="919c3-112">要件</span><span class="sxs-lookup"><span data-stu-id="919c3-112">Requirements</span></span>  
 <span data-ttu-id="919c3-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="919c3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="919c3-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="919c3-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="919c3-115">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="919c3-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="919c3-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="919c3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="919c3-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="919c3-117">See Also</span></span>  
 [<span data-ttu-id="919c3-118">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="919c3-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="919c3-119">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="919c3-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

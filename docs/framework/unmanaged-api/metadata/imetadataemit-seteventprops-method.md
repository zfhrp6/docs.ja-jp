---
title: "IMetaDataEmit::SetEventProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetEventProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 167e56052550fa844d1265802455b3cbf6368ba3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="f56a9-102">IMetaDataEmit::SetEventProps メソッド</span><span class="sxs-lookup"><span data-stu-id="f56a9-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="f56a9-103">前回の呼び出しによって定義されたイベントの指定した機能の更新を設定または[imetadataemit::defineevent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="f56a9-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f56a9-104">構文</span><span class="sxs-lookup"><span data-stu-id="f56a9-104">Syntax</span></span>  
  
```  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,   
    [in]  DWORD       dwEventFlags,   
    [in]  mdToken     tkEventType,   
    [in]  mdMethodDef mdAddOn,   
    [in]  mdMethodDef mdRemoveOn,   
    [in]  mdMethodDef mdFire,   
    [in]  mdMethodDef rmdOtherMethods[]   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f56a9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f56a9-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="f56a9-106">[in]イベント トークンです。</span><span class="sxs-lookup"><span data-stu-id="f56a9-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="f56a9-107">[in]イベントのフラグです。</span><span class="sxs-lookup"><span data-stu-id="f56a9-107">[in] Event flags.</span></span> <span data-ttu-id="f56a9-108">これは、ビットマスク`CorEventAttr`値。</span><span class="sxs-lookup"><span data-stu-id="f56a9-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="f56a9-109">[in]イベント クラスに対してトークンです。</span><span class="sxs-lookup"><span data-stu-id="f56a9-109">[in] The token for the event class.</span></span> <span data-ttu-id="f56a9-110">これは、いずれか、`mdTypeDef`または`mdTypeRef`トークンです。</span><span class="sxs-lookup"><span data-stu-id="f56a9-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="f56a9-111">[in]イベント、または null にサブスクライブするために使用するメソッド。</span><span class="sxs-lookup"><span data-stu-id="f56a9-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="f56a9-112">[in]イベント、または null をアンサブスク ライブする方法。</span><span class="sxs-lookup"><span data-stu-id="f56a9-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="f56a9-113">[in]イベントを発生させる (派生クラス) によって使用されるメソッド。</span><span class="sxs-lookup"><span data-stu-id="f56a9-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="f56a9-114">[in]イベントに関連付けられたその他のメソッドのトークンの配列。</span><span class="sxs-lookup"><span data-stu-id="f56a9-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="f56a9-115">配列の最後の要素である必要があります`mdMethodDefNil`です。</span><span class="sxs-lookup"><span data-stu-id="f56a9-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f56a9-116">要件</span><span class="sxs-lookup"><span data-stu-id="f56a9-116">Requirements</span></span>  
 <span data-ttu-id="f56a9-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f56a9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f56a9-118">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f56a9-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f56a9-119">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="f56a9-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f56a9-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f56a9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f56a9-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="f56a9-121">See Also</span></span>  
 [<span data-ttu-id="f56a9-122">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f56a9-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f56a9-123">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f56a9-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

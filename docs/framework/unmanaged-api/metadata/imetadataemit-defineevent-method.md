---
title: "IMetaDataEmit::DefineEvent メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bf790ce270565abaf1d91e54c9e3569a50ab3435
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="c1df0-102">IMetaDataEmit::DefineEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="c1df0-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="c1df0-103">指定したメタデータ シグネチャを持つイベントの定義を作成し、そのイベント定義トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="c1df0-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1df0-104">構文</span><span class="sxs-lookup"><span data-stu-id="c1df0-104">Syntax</span></span>  
  
```  
HRESULT DefineEvent (   
    [in]  mdTypeDef    td,   
    [in]  LPCWSTR      szEvent,   
    [in]  DWORD        dwEventFlags,   
    [in]  mdToken      tkEventType,   
    [in]  mdMethodDef  mdAddOn,   
    [in]  mdMethodDef  mdRemoveOn,   
    [in]  mdMethodDef  mdFire,   
    [in]  mdMethodDef  rmdOtherMethods[],   
    [out] mdEvent      *pmdEvent   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1df0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c1df0-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="c1df0-106">[in]ターゲット クラスまたはインターフェイスのトークンです。</span><span class="sxs-lookup"><span data-stu-id="c1df0-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="c1df0-107">これは、いずれか、`mdTypeDef`または`mdTypeDefNil`トークンです。</span><span class="sxs-lookup"><span data-stu-id="c1df0-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="c1df0-108">[in]イベントの名前。</span><span class="sxs-lookup"><span data-stu-id="c1df0-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="c1df0-109">[in]イベントのフラグです。</span><span class="sxs-lookup"><span data-stu-id="c1df0-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="c1df0-110">[in]イベント クラスに対してトークンです。</span><span class="sxs-lookup"><span data-stu-id="c1df0-110">[in] The token for the event class.</span></span> <span data-ttu-id="c1df0-111">これは、 `mdTypeDef`、 `mdTypeRef`、または`mdTokenNil`トークンです。</span><span class="sxs-lookup"><span data-stu-id="c1df0-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="c1df0-112">[in]イベント、または null にサブスクライブするために使用するメソッド。</span><span class="sxs-lookup"><span data-stu-id="c1df0-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="c1df0-113">[in]イベント、または null をアンサブスク ライブする方法。</span><span class="sxs-lookup"><span data-stu-id="c1df0-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="c1df0-114">[in]イベントを発生させる (派生クラス) によって使用されるメソッド。</span><span class="sxs-lookup"><span data-stu-id="c1df0-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="c1df0-115">[in]イベントに関連付けられたその他のメソッドのトークンの配列。</span><span class="sxs-lookup"><span data-stu-id="c1df0-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="c1df0-116">配列はで終了、`mdMethodDefNil`トークンです。</span><span class="sxs-lookup"><span data-stu-id="c1df0-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="c1df0-117">[out]イベントに割り当てられたメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="c1df0-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1df0-118">要件</span><span class="sxs-lookup"><span data-stu-id="c1df0-118">Requirements</span></span>  
 <span data-ttu-id="c1df0-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c1df0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1df0-120">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c1df0-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c1df0-121">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="c1df0-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1df0-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1df0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1df0-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1df0-123">See Also</span></span>  
 [<span data-ttu-id="c1df0-124">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c1df0-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="c1df0-125">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c1df0-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

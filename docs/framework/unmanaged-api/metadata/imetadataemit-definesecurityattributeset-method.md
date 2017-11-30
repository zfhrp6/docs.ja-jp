---
title: "IMetaDataEmit::DefineSecurityAttributeSet メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineSecurityAttributeSet
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineSecurityAttributeSet
helpviewer_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet method [.NET Framework metadata]
- DefineSecurityAttributeSet method [.NET Framework metadata]
ms.assetid: 27064ca2-4186-4433-90a7-3b297785e891
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 79d5bb7240305d06d916e969765606ddc2ddf9b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="699f8-102">IMetaDataEmit::DefineSecurityAttributeSet メソッド</span><span class="sxs-lookup"><span data-stu-id="699f8-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="699f8-103">指定したトークンによって参照されるオブジェクトにアタッチするセキュリティ権限のセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="699f8-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="699f8-104">構文</span><span class="sxs-lookup"><span data-stu-id="699f8-104">Syntax</span></span>  
  
```  
HRESULT DefineSecurityAttributeSet (   
    [in]  mdToken       tkObj,   
    [in]  COR_SECATTR   rSecAttrs[],   
    [in]  ULONG         cSecAttrs,   
    [out] ULONG         *pulErrorAttr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="699f8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="699f8-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="699f8-106">[in]セキュリティ情報が接続されているトークンです。</span><span class="sxs-lookup"><span data-stu-id="699f8-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="699f8-107">[in]配列`COR_SECATTR`構造体。</span><span class="sxs-lookup"><span data-stu-id="699f8-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="699f8-108">[in]内の要素の数`rSecAttrs`です。</span><span class="sxs-lookup"><span data-stu-id="699f8-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="699f8-109">[out]メソッドが失敗した場合、指定のインデックス`rSecAttrs`の問題の原因となった要素。</span><span class="sxs-lookup"><span data-stu-id="699f8-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="699f8-110">要件</span><span class="sxs-lookup"><span data-stu-id="699f8-110">Requirements</span></span>  
 <span data-ttu-id="699f8-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="699f8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="699f8-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="699f8-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="699f8-113">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="699f8-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="699f8-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="699f8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="699f8-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="699f8-115">See Also</span></span>  
 [<span data-ttu-id="699f8-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="699f8-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="699f8-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="699f8-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

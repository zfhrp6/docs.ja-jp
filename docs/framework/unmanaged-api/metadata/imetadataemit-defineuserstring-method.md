---
title: "IMetaDataEmit::DefineUserString メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineUserString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineUserString
helpviewer_keywords:
- DefineUserString method [.NET Framework metadata]
- IMetaDataEmit::DefineUserString method [.NET Framework metadata]
ms.assetid: 88fb7ef3-bbdf-429c-b678-c9c153456461
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 729f2d48722fb34b844636b416edf36d715e1a48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="a6169-102">IMetaDataEmit::DefineUserString メソッド</span><span class="sxs-lookup"><span data-stu-id="a6169-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="a6169-103">指定されたリテラル文字列のメタデータ トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="a6169-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6169-104">構文</span><span class="sxs-lookup"><span data-stu-id="a6169-104">Syntax</span></span>  
  
```  
HRESULT DefineUserString (   
    [in]  LPCWSTR     szString,   
    [in]  ULONG       cchString,   
    [out] mdString    *pstk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6169-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a6169-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="a6169-106">[in]格納するユーザー文字列。</span><span class="sxs-lookup"><span data-stu-id="a6169-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="a6169-107">[in]ワイド文字のカウント`szString`です。</span><span class="sxs-lookup"><span data-stu-id="a6169-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="a6169-108">[out]割り当てられた文字列トークン。</span><span class="sxs-lookup"><span data-stu-id="a6169-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6169-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="a6169-109">Requirements</span></span>  
 <span data-ttu-id="a6169-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a6169-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6169-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a6169-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a6169-112">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="a6169-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6169-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6169-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6169-114">参照</span><span class="sxs-lookup"><span data-stu-id="a6169-114">See Also</span></span>  
 [<span data-ttu-id="a6169-115">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6169-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="a6169-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6169-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

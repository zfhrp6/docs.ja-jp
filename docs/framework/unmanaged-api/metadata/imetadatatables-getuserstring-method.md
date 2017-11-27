---
title: "IMetaDataTables::GetUserString メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetUserString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetUserString
helpviewer_keywords:
- IMetaDataTables::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 35b8f0d6-9aba-4714-adb2-62020a38fb7e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 648cc9e6f947f5eaf5dd6c9354ba305f7ca0d530
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetuserstring-method"></a><span data-ttu-id="698ad-102">IMetaDataTables::GetUserString メソッド</span><span class="sxs-lookup"><span data-stu-id="698ad-102">IMetaDataTables::GetUserString Method</span></span>
<span data-ttu-id="698ad-103">現在のスコープ内の文字列の列で指定したインデックス位置には、ハード コーディングされた文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="698ad-103">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="698ad-104">構文</span><span class="sxs-lookup"><span data-stu-id="698ad-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
    [in]  ULONG       ixUserString,  
    [out] ULONG       *pcbData,  
    [out] const void  **ppData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="698ad-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="698ad-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="698ad-106">[in]ハード コーディングされた文字列の取得元となるインデックス値。</span><span class="sxs-lookup"><span data-stu-id="698ad-106">[in] The index value from which the hard-coded string will be retrieved.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="698ad-107">[out]P; のサイズに ointer`ppData`です。</span><span class="sxs-lookup"><span data-stu-id="698ad-107">[out] A p;ointer to the size of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="698ad-108">[out]返される文字列へのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="698ad-108">[out] A pointer to a pointer to the returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="698ad-109">要件</span><span class="sxs-lookup"><span data-stu-id="698ad-109">Requirements</span></span>  
 <span data-ttu-id="698ad-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="698ad-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="698ad-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="698ad-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="698ad-112">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="698ad-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="698ad-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="698ad-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="698ad-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="698ad-114">See Also</span></span>  
 [<span data-ttu-id="698ad-115">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="698ad-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="698ad-116">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="698ad-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

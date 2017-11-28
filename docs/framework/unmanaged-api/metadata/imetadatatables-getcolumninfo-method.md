---
title: "IMetaDataTables::GetColumnInfo メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetColumnInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 939085294666a233341f65a8f5736d9dce201470
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="6a3a6-102">IMetaDataTables::GetColumnInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="6a3a6-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="6a3a6-103">指定されたテーブルで指定された列に関するデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="6a3a6-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a3a6-104">構文</span><span class="sxs-lookup"><span data-stu-id="6a3a6-104">Syntax</span></span>  
  
```  
HRESULT GetColumnInfo (   
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a3a6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6a3a6-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="6a3a6-106">[in]目的のテーブルのインデックス。</span><span class="sxs-lookup"><span data-stu-id="6a3a6-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="6a3a6-107">[in]必要な列のインデックス。</span><span class="sxs-lookup"><span data-stu-id="6a3a6-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="6a3a6-108">[out]行内の列のオフセットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6a3a6-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="6a3a6-109">[out]列のバイト単位のサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6a3a6-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="6a3a6-110">[out]列の値の型へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6a3a6-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="6a3a6-111">[out]列の名前へのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6a3a6-111">[out] A pointer to a pointer to the column name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a3a6-112">要件</span><span class="sxs-lookup"><span data-stu-id="6a3a6-112">Requirements</span></span>  
 <span data-ttu-id="6a3a6-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6a3a6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a3a6-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6a3a6-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6a3a6-115">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="6a3a6-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6a3a6-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a3a6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a3a6-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="6a3a6-117">See Also</span></span>  
 [<span data-ttu-id="6a3a6-118">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6a3a6-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="6a3a6-119">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6a3a6-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

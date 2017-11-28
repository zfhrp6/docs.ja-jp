---
title: "IMetaDataTables::GetColumn メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetColumn
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: abc6e5ad5ec1da5ac92dafb455e44d0ccfdade4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="cff69-102">IMetaDataTables::GetColumn メソッド</span><span class="sxs-lookup"><span data-stu-id="cff69-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="cff69-103">指定した列と、指定されたテーブルの行のセルに含まれる値へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="cff69-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cff69-104">構文</span><span class="sxs-lookup"><span data-stu-id="cff69-104">Syntax</span></span>  
  
```  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cff69-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cff69-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="cff69-106">[in]テーブルのインデックス。</span><span class="sxs-lookup"><span data-stu-id="cff69-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="cff69-107">[in]テーブル内の列のインデックス。</span><span class="sxs-lookup"><span data-stu-id="cff69-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="cff69-108">[in]テーブル内の行のインデックス。</span><span class="sxs-lookup"><span data-stu-id="cff69-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="cff69-109">[out]セルの値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="cff69-109">[out] A pointer to the value in the cell.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cff69-110">要件</span><span class="sxs-lookup"><span data-stu-id="cff69-110">Requirements</span></span>  
 <span data-ttu-id="cff69-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cff69-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cff69-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cff69-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cff69-113">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="cff69-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cff69-114">**.NET framework のバージョン**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cff69-114">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff69-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="cff69-115">See Also</span></span>  
 [<span data-ttu-id="cff69-116">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cff69-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="cff69-117">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cff69-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

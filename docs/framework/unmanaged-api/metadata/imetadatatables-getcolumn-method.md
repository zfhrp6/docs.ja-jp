---
title: IMetaDataTables::GetColumn メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 850a97240e0a6450b4dec759a8786e0df5bffac8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448961"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="b5459-102">IMetaDataTables::GetColumn メソッド</span><span class="sxs-lookup"><span data-stu-id="b5459-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="b5459-103">指定した列と、指定されたテーブルの行のセルに含まれる値へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="b5459-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5459-104">構文</span><span class="sxs-lookup"><span data-stu-id="b5459-104">Syntax</span></span>  
  
```  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5459-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b5459-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="b5459-106">[in]テーブルのインデックス。</span><span class="sxs-lookup"><span data-stu-id="b5459-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="b5459-107">[in]テーブル内の列のインデックス。</span><span class="sxs-lookup"><span data-stu-id="b5459-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="b5459-108">[in]テーブル内の行のインデックス。</span><span class="sxs-lookup"><span data-stu-id="b5459-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="b5459-109">[out]セルの値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b5459-109">[out] A pointer to the value in the cell.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5459-110">要件</span><span class="sxs-lookup"><span data-stu-id="b5459-110">Requirements</span></span>  
 <span data-ttu-id="b5459-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b5459-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5459-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b5459-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b5459-113">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="b5459-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b5459-114">**.NET framework のバージョン** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5459-114">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5459-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5459-115">See Also</span></span>  
 [<span data-ttu-id="b5459-116">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b5459-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="b5459-117">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b5459-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

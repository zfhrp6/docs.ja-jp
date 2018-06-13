---
title: IMetaDataTables::GetColumnInfo メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetColumnInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 79f08109f1ad267c4898cc0789859b55f534d1b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448082"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="eca9d-102">IMetaDataTables::GetColumnInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="eca9d-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="eca9d-103">指定されたテーブルで指定された列に関するデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="eca9d-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eca9d-104">構文</span><span class="sxs-lookup"><span data-stu-id="eca9d-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="eca9d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eca9d-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="eca9d-106">[in]目的のテーブルのインデックス。</span><span class="sxs-lookup"><span data-stu-id="eca9d-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="eca9d-107">[in]必要な列のインデックス。</span><span class="sxs-lookup"><span data-stu-id="eca9d-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="eca9d-108">[out]行内の列のオフセットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eca9d-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="eca9d-109">[out]列のバイト単位のサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eca9d-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="eca9d-110">[out]列の値の型へのポインター。</span><span class="sxs-lookup"><span data-stu-id="eca9d-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="eca9d-111">[out]列の名前へのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eca9d-111">[out] A pointer to a pointer to the column name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eca9d-112">要件</span><span class="sxs-lookup"><span data-stu-id="eca9d-112">Requirements</span></span>  
 <span data-ttu-id="eca9d-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="eca9d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eca9d-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="eca9d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eca9d-115">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="eca9d-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eca9d-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eca9d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eca9d-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="eca9d-117">See Also</span></span>  
 [<span data-ttu-id="eca9d-118">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eca9d-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="eca9d-119">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eca9d-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

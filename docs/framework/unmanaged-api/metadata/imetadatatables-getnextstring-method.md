---
title: IMetaDataTables::GetNextString メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextString
helpviewer_keywords:
- IMetaDataTables::GetNextString method [.NET Framework metadata]
- GetNextString method [.NET Framework metadata]
ms.assetid: d9720428-c353-4f07-a7e8-899e106a1b37
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eea43e5eaa037a3b70f482b0602d8d8d3d594f75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449850"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="9b923-102">IMetaDataTables::GetNextString メソッド</span><span class="sxs-lookup"><span data-stu-id="9b923-102">IMetaDataTables::GetNextString Method</span></span>
<span data-ttu-id="9b923-103">現在のテーブルの列には、次の文字列のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="9b923-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b923-104">構文</span><span class="sxs-lookup"><span data-stu-id="9b923-104">Syntax</span></span>  
  
```  
HRESULT GetNextString (   
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b923-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9b923-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="9b923-106">[in]文字列テーブルの列からインデックス値。</span><span class="sxs-lookup"><span data-stu-id="9b923-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="9b923-107">[out]列に [次へ] の文字列のインデックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9b923-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b923-108">要件</span><span class="sxs-lookup"><span data-stu-id="9b923-108">Requirements</span></span>  
 <span data-ttu-id="9b923-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9b923-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b923-110">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9b923-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9b923-111">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="9b923-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9b923-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b923-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b923-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b923-113">See Also</span></span>  
 [<span data-ttu-id="9b923-114">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b923-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="9b923-115">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b923-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

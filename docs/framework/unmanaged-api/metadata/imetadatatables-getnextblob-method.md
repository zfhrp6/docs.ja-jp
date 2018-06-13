---
title: IMetaDataTables::GetNextBlob メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextBlob
helpviewer_keywords:
- IMetaDataTables::GetNextBlob method [.NET Framework metadata]
- GetNextBlob method [.NET Framework metadata]
ms.assetid: 017c8ab4-4c09-4754-9935-5b0b49cabecb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: caf7faeea4bcec9b73f3c43f0923d308baebf6d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447621"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="04043-102">IMetaDataTables::GetNextBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="04043-102">IMetaDataTables::GetNextBlob Method</span></span>
<span data-ttu-id="04043-103">テーブル内には、次のバイナリ ラージ オブジェクト (BLOB) のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="04043-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04043-104">構文</span><span class="sxs-lookup"><span data-stu-id="04043-104">Syntax</span></span>  
  
```  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04043-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="04043-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="04043-106">[in]Blob の列から返されるインデックスです。</span><span class="sxs-lookup"><span data-stu-id="04043-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="04043-107">[out]次の BLOB のインデックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="04043-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04043-108">要件</span><span class="sxs-lookup"><span data-stu-id="04043-108">Requirements</span></span>  
 <span data-ttu-id="04043-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="04043-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04043-110">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="04043-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="04043-111">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="04043-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="04043-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04043-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04043-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="04043-113">See Also</span></span>  
 [<span data-ttu-id="04043-114">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="04043-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="04043-115">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="04043-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

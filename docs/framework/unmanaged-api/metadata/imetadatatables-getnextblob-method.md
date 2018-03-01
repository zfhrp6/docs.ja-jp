---
title: "IMetaDataTables::GetNextBlob メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 399cf6626e7a56584829b2a8417958ce7e608727
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="75e16-102">IMetaDataTables::GetNextBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="75e16-102">IMetaDataTables::GetNextBlob Method</span></span>
<span data-ttu-id="75e16-103">テーブル内には、次のバイナリ ラージ オブジェクト (BLOB) のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="75e16-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75e16-104">構文</span><span class="sxs-lookup"><span data-stu-id="75e16-104">Syntax</span></span>  
  
```  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="75e16-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="75e16-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="75e16-106">[in]Blob の列から返されるインデックスです。</span><span class="sxs-lookup"><span data-stu-id="75e16-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="75e16-107">[out]次の BLOB のインデックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="75e16-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75e16-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="75e16-108">Requirements</span></span>  
 <span data-ttu-id="75e16-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="75e16-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75e16-110">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="75e16-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="75e16-111">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="75e16-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="75e16-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75e16-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75e16-113">参照</span><span class="sxs-lookup"><span data-stu-id="75e16-113">See Also</span></span>  
 [<span data-ttu-id="75e16-114">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="75e16-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="75e16-115">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="75e16-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

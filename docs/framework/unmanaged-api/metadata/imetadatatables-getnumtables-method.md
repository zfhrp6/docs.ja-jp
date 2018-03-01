---
title: "IMetaDataTables::GetNumTables メソッド"
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
- IMetaDataTables.GetNumTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNumTables
helpviewer_keywords:
- GetNumTables method [.NET Framework metadata]
- IMetaDataTables::GetNumTables method [.NET Framework metadata]
ms.assetid: 8196f2a3-bbf2-45d3-a6cd-74502c356644
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0d65b17899f0a6856daf3d99fe8b8025d5d4c462
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetnumtables-method"></a><span data-ttu-id="253a6-102">IMetaDataTables::GetNumTables メソッド</span><span class="sxs-lookup"><span data-stu-id="253a6-102">IMetaDataTables::GetNumTables Method</span></span>
<span data-ttu-id="253a6-103">現在のスコープ内のテーブルの数を取得`IMetaDataTables`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="253a6-103">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="253a6-104">構文</span><span class="sxs-lookup"><span data-stu-id="253a6-104">Syntax</span></span>  
  
```  
HRESULT GetNumTables (  
    [out]  ULONG   *pcTables  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="253a6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="253a6-105">Parameters</span></span>  
 `pcTables`  
 <span data-ttu-id="253a6-106">[out]現在のインスタンスのスコープ内のテーブルの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="253a6-106">[out] A pointer to the number of tables in the current instance scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="253a6-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="253a6-107">Requirements</span></span>  
 <span data-ttu-id="253a6-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="253a6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="253a6-109">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="253a6-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="253a6-110">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="253a6-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="253a6-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="253a6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="253a6-112">参照</span><span class="sxs-lookup"><span data-stu-id="253a6-112">See Also</span></span>  
 [<span data-ttu-id="253a6-113">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="253a6-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="253a6-114">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="253a6-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

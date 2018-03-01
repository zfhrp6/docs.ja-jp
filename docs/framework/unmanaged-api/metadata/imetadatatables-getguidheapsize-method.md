---
title: "IMetaDataTables::GetGuidHeapSize メソッド"
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
- IMetaDataTables.GetGuidHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuidHeapSize
helpviewer_keywords:
- GetGuidHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetGuidHeapSize method [.NET Framework metadata]
ms.assetid: e875cbee-1ad9-4f1a-bf03-38cdb8ff371a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 297b8f3572f67aa5e8b17b1b94d71f59962cfe68
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="1b36c-102">IMetaDataTables::GetGuidHeapSize メソッド</span><span class="sxs-lookup"><span data-stu-id="1b36c-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="1b36c-103">GUID ヒープのバイト単位のサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="1b36c-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b36c-104">構文</span><span class="sxs-lookup"><span data-stu-id="1b36c-104">Syntax</span></span>  
  
```  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b36c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1b36c-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="1b36c-106">[out]GUID ヒープのバイト単位のサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1b36c-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b36c-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="1b36c-107">Requirements</span></span>  
 <span data-ttu-id="1b36c-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1b36c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b36c-109">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1b36c-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1b36c-110">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="1b36c-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1b36c-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b36c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b36c-112">参照</span><span class="sxs-lookup"><span data-stu-id="1b36c-112">See Also</span></span>  
 [<span data-ttu-id="1b36c-113">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1b36c-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="1b36c-114">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1b36c-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

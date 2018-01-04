---
title: "IMetaDataImport::ResetEnum メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.ResetEnum
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::ResetEnum
helpviewer_keywords:
- ResetEnum method [.NET Framework metadata]
- IMetaDataImport::ResetEnum method [.NET Framework metadata]
ms.assetid: dda867b5-1050-49ba-b01c-fcc83b7a5617
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 794dcd1b211f5fe3a4ac9f2c840eba6bb908c6ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="e6cc4-102">IMetaDataImport::ResetEnum メソッド</span><span class="sxs-lookup"><span data-stu-id="e6cc4-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="e6cc4-103">指定した列挙子を指定した位置にリセットします。</span><span class="sxs-lookup"><span data-stu-id="e6cc4-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6cc4-104">構文</span><span class="sxs-lookup"><span data-stu-id="e6cc4-104">Syntax</span></span>  
  
```  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,   
   [in] ULONG       ulPos  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6cc4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e6cc4-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="e6cc4-106">[in]リセットする列挙子。</span><span class="sxs-lookup"><span data-stu-id="e6cc4-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="e6cc4-107">[in]新しい位置を列挙子を配置します。</span><span class="sxs-lookup"><span data-stu-id="e6cc4-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6cc4-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="e6cc4-108">Requirements</span></span>  
 <span data-ttu-id="e6cc4-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e6cc4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6cc4-110">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e6cc4-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e6cc4-111">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="e6cc4-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e6cc4-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6cc4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6cc4-113">参照</span><span class="sxs-lookup"><span data-stu-id="e6cc4-113">See Also</span></span>  
 [<span data-ttu-id="e6cc4-114">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6cc4-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="e6cc4-115">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6cc4-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

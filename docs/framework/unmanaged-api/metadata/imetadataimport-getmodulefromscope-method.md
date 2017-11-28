---
title: "IMetaDataImport::GetModuleFromScope メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetModuleFromScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d7a9987f9a557cda79483e46c1798d471aa13944
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="df649-102">IMetaDataImport::GetModuleFromScope メソッド</span><span class="sxs-lookup"><span data-stu-id="df649-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="df649-103">現在のメタデータ スコープ内で参照されるモジュールのメタデータ トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="df649-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df649-104">構文</span><span class="sxs-lookup"><span data-stu-id="df649-104">Syntax</span></span>  
  
```  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df649-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="df649-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="df649-106">[out]現在のメタデータ スコープで参照されているモジュールを表すトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="df649-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df649-107">要件</span><span class="sxs-lookup"><span data-stu-id="df649-107">Requirements</span></span>  
 <span data-ttu-id="df649-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="df649-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df649-109">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="df649-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="df649-110">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="df649-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="df649-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df649-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df649-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="df649-112">See Also</span></span>  
 [<span data-ttu-id="df649-113">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="df649-113">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="df649-114">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="df649-114">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

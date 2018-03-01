---
title: "IAssemblyName::GetVersion メソッド"
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
- IAssemblyName.GetVersion
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetVersion
helpviewer_keywords:
- IAssemblyName::GetVersion method [.NET Framework fusion]
- GetVersion method, IAssemblyName interface [.NET Framework fusion]
ms.assetid: 42230928-2c33-41fd-9519-d96efef6c7af
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5ad4084bc758ec8a0b6d97ef211555ccbe78f3bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="a32ec-102">IAssemblyName::GetVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="a32ec-102">IAssemblyName::GetVersion Method</span></span>
<span data-ttu-id="a32ec-103">これによって参照されるアセンブリのバージョン情報を取得[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a32ec-103">Gets the version information for the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a32ec-104">構文</span><span class="sxs-lookup"><span data-stu-id="a32ec-104">Syntax</span></span>  
  
```  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a32ec-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a32ec-105">Parameters</span></span>  
 `pdwVersionHi`  
 <span data-ttu-id="a32ec-106">[out]バージョンの上位 32 ビット。</span><span class="sxs-lookup"><span data-stu-id="a32ec-106">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="a32ec-107">[out]バージョンの下位 32 ビット。</span><span class="sxs-lookup"><span data-stu-id="a32ec-107">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a32ec-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="a32ec-108">Requirements</span></span>  
 <span data-ttu-id="a32ec-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a32ec-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a32ec-110">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="a32ec-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a32ec-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a32ec-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a32ec-112">参照</span><span class="sxs-lookup"><span data-stu-id="a32ec-112">See Also</span></span>  
 [<span data-ttu-id="a32ec-113">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a32ec-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)

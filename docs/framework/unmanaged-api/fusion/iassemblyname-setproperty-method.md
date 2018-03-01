---
title: "IAssemblyName::SetProperty メソッド"
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
- IAssemblyName.SetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::SetProperty
helpviewer_keywords:
- IAssemblyName::SetProperty method [.NET Framework fusion]
- SetProperty method [.NET Framework fusion]
ms.assetid: 496c3add-f60b-4073-943f-d1bcf33330cb
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 60ef27021ec3431c90086e0dfbae56bb6e6ccc86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="5ac2b-102">IAssemblyName::SetProperty メソッド</span><span class="sxs-lookup"><span data-stu-id="5ac2b-102">IAssemblyName::SetProperty Method</span></span>
<span data-ttu-id="5ac2b-103">指定したプロパティの識別子によって参照されるプロパティの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="5ac2b-103">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ac2b-104">構文</span><span class="sxs-lookup"><span data-stu-id="5ac2b-104">Syntax</span></span>  
  
```  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5ac2b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5ac2b-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="5ac2b-106">[in]値が設定されるプロパティの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="5ac2b-106">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="5ac2b-107">[in]によって参照されるプロパティを設定する値`PropertyId`です。</span><span class="sxs-lookup"><span data-stu-id="5ac2b-107">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="5ac2b-108">[in]サイズをバイト単位での`pvProperty`します。</span><span class="sxs-lookup"><span data-stu-id="5ac2b-108">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ac2b-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="5ac2b-109">Requirements</span></span>  
 <span data-ttu-id="5ac2b-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5ac2b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ac2b-111">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="5ac2b-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="5ac2b-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ac2b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ac2b-113">参照</span><span class="sxs-lookup"><span data-stu-id="5ac2b-113">See Also</span></span>  
 [<span data-ttu-id="5ac2b-114">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ac2b-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)

---
title: "IAssemblyName::IsEqual メソッド"
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
- IAssemblyName.IsEqual
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 454226d45474abea67b944e8437cf53be5c8ed1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="7a0d7-102">IAssemblyName::IsEqual メソッド</span><span class="sxs-lookup"><span data-stu-id="7a0d7-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="7a0d7-103">指定したかどうかを決定[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)オブジェクトがこの`IAssemblyName`指定した比較フラグに基づいて、します。</span><span class="sxs-lookup"><span data-stu-id="7a0d7-103">Determines whether a specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a0d7-104">構文</span><span class="sxs-lookup"><span data-stu-id="7a0d7-104">Syntax</span></span>  
  
```  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a0d7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7a0d7-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="7a0d7-106">[in]`IAssemblyName`これと比較するオブジェクト`IAssemblyName`です。</span><span class="sxs-lookup"><span data-stu-id="7a0d7-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="7a0d7-107">[in]ビットごとの組み合わせ[ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md)比較に影響を与える値。</span><span class="sxs-lookup"><span data-stu-id="7a0d7-107">[in] A bitwise combination of [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a0d7-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="7a0d7-108">Requirements</span></span>  
 <span data-ttu-id="7a0d7-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7a0d7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a0d7-110">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="7a0d7-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7a0d7-111">**NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a0d7-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a0d7-112">参照</span><span class="sxs-lookup"><span data-stu-id="7a0d7-112">See Also</span></span>  
 [<span data-ttu-id="7a0d7-113">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7a0d7-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="7a0d7-114">Fusion 列挙型</span><span class="sxs-lookup"><span data-stu-id="7a0d7-114">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)

---
title: IAssemblyName::IsEqual メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 043394541f5ed91b85a57f4cb13c61cca442bfec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431842"
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="fb4a5-102">IAssemblyName::IsEqual メソッド</span><span class="sxs-lookup"><span data-stu-id="fb4a5-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="fb4a5-103">指定したかどうかを決定[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)オブジェクトがこの`IAssemblyName`指定した比較フラグに基づいて、します。</span><span class="sxs-lookup"><span data-stu-id="fb4a5-103">Determines whether a specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb4a5-104">構文</span><span class="sxs-lookup"><span data-stu-id="fb4a5-104">Syntax</span></span>  
  
```  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb4a5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fb4a5-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="fb4a5-106">[in]`IAssemblyName`これと比較するオブジェクト`IAssemblyName`です。</span><span class="sxs-lookup"><span data-stu-id="fb4a5-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="fb4a5-107">[in]ビットごとの組み合わせ[ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md)比較に影響を与える値。</span><span class="sxs-lookup"><span data-stu-id="fb4a5-107">[in] A bitwise combination of [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb4a5-108">要件</span><span class="sxs-lookup"><span data-stu-id="fb4a5-108">Requirements</span></span>  
 <span data-ttu-id="fb4a5-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fb4a5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb4a5-110">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="fb4a5-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="fb4a5-111">**NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb4a5-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb4a5-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="fb4a5-112">See Also</span></span>  
 [<span data-ttu-id="fb4a5-113">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fb4a5-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="fb4a5-114">Fusion 列挙型</span><span class="sxs-lookup"><span data-stu-id="fb4a5-114">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)

---
title: IAssemblyName::GetProperty メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetProperty
helpviewer_keywords:
- IAssemblyName::GetProperty method [.NET Framework fusion]
- GetProperty method [.NET Framework fusion]
ms.assetid: e59fda62-77d5-4e37-89cb-ce7ae4627975
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c297c2476cb35fef861cda77f4f6f536fd85557
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428192"
---
# <a name="iassemblynamegetproperty-method"></a><span data-ttu-id="40591-102">IAssemblyName::GetProperty メソッド</span><span class="sxs-lookup"><span data-stu-id="40591-102">IAssemblyName::GetProperty Method</span></span>
<span data-ttu-id="40591-103">指定したプロパティの識別子によって参照されるプロパティへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="40591-103">Gets a pointer to the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40591-104">構文</span><span class="sxs-lookup"><span data-stu-id="40591-104">Syntax</span></span>  
  
```  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="40591-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="40591-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="40591-106">[in]要求されたプロパティの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="40591-106">[in] The unique identifier for the requested property.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="40591-107">[out]返されるプロパティのデータ。</span><span class="sxs-lookup"><span data-stu-id="40591-107">[out] The returned property data.</span></span>  
  
 `pcbProperty`  
 <span data-ttu-id="40591-108">[入力、出力].サイズをバイト単位での`pvProperty`します。</span><span class="sxs-lookup"><span data-stu-id="40591-108">[in, out] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40591-109">要件</span><span class="sxs-lookup"><span data-stu-id="40591-109">Requirements</span></span>  
 <span data-ttu-id="40591-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="40591-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40591-111">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="40591-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="40591-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40591-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40591-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="40591-113">See Also</span></span>  
 [<span data-ttu-id="40591-114">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="40591-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)

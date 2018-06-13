---
title: IAssemblyName::SetProperty メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bcfb584fc2380a7ae1567d3d4d6203b537676220
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429700"
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="49553-102">IAssemblyName::SetProperty メソッド</span><span class="sxs-lookup"><span data-stu-id="49553-102">IAssemblyName::SetProperty Method</span></span>
<span data-ttu-id="49553-103">指定したプロパティの識別子によって参照されるプロパティの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="49553-103">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49553-104">構文</span><span class="sxs-lookup"><span data-stu-id="49553-104">Syntax</span></span>  
  
```  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49553-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="49553-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="49553-106">[in]値が設定されるプロパティの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="49553-106">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="49553-107">[in]によって参照されるプロパティを設定する値`PropertyId`です。</span><span class="sxs-lookup"><span data-stu-id="49553-107">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="49553-108">[in]サイズをバイト単位での`pvProperty`します。</span><span class="sxs-lookup"><span data-stu-id="49553-108">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49553-109">要件</span><span class="sxs-lookup"><span data-stu-id="49553-109">Requirements</span></span>  
 <span data-ttu-id="49553-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="49553-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49553-111">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="49553-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="49553-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49553-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49553-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="49553-113">See Also</span></span>  
 [<span data-ttu-id="49553-114">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="49553-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)

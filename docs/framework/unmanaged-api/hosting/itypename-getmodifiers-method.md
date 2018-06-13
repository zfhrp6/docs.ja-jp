---
title: ITypeName::GetModifiers メソッド
ms.date: 03/30/2017
api_name:
- ITypeName.GetModifiers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetModifiers
helpviewer_keywords:
- ITypeName::GetModifiers method [.NET Framework hosting]
- GetModifiers method [.NET Framework hosting]
ms.assetid: 75508c55-3e09-4135-80da-cc811003fa82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 66976b99b5686c62ad31c8a0365ce14f1bf33f85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439906"
---
# <a name="itypenamegetmodifiers-method"></a><span data-ttu-id="56623-102">ITypeName::GetModifiers メソッド</span><span class="sxs-lookup"><span data-stu-id="56623-102">ITypeName::GetModifiers Method</span></span>
<span data-ttu-id="56623-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="56623-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56623-104">構文</span><span class="sxs-lookup"><span data-stu-id="56623-104">Syntax</span></span>  
  
```  
HRESULT GetModifiers (  
    [in] DWORD           count,  
    [out] DWORD*         rgModifiers,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="56623-105">要件</span><span class="sxs-lookup"><span data-stu-id="56623-105">Requirements</span></span>  
 <span data-ttu-id="56623-106">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="56623-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56623-107">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="56623-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="56623-108">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="56623-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56623-109">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56623-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56623-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="56623-110">See Also</span></span>  
 [<span data-ttu-id="56623-111">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="56623-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

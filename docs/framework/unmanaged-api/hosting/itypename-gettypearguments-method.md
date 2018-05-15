---
title: ITypeName::GetTypeArguments メソッド
ms.date: 03/30/2017
api_name:
- ITypeName.GetTypeArguments
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetTypeArguments
helpviewer_keywords:
- ITypeName::GetTypeArguments method [.NET Framework hosting]
- GetTypeArguments method [.NET Framework hosting]
ms.assetid: 638d77df-ff9c-40d9-88ee-930f5f87ada1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77b3a898dd929a6eeadc466a04a0fdb10571ed7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="itypenamegettypearguments-method"></a><span data-ttu-id="cf951-102">ITypeName::GetTypeArguments メソッド</span><span class="sxs-lookup"><span data-stu-id="cf951-102">ITypeName::GetTypeArguments Method</span></span>
<span data-ttu-id="cf951-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="cf951-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf951-104">構文</span><span class="sxs-lookup"><span data-stu-id="cf951-104">Syntax</span></span>  
  
```  
HRESULT GetTypeArguments (  
    [in] DWORD           count,  
    [out] ITypeName**    rgpArguments,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="cf951-105">要件</span><span class="sxs-lookup"><span data-stu-id="cf951-105">Requirements</span></span>  
 <span data-ttu-id="cf951-106">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cf951-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf951-107">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cf951-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf951-108">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="cf951-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf951-109">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf951-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf951-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf951-110">See Also</span></span>  
 [<span data-ttu-id="cf951-111">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cf951-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

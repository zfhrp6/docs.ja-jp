---
title: ITypeName::GetAssemblyName メソッド
ms.date: 03/30/2017
api_name:
- ITypeName.GetAssemblyName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetAssemblyName
helpviewer_keywords:
- ITypeName::GetAssemblyName method [.NET Framework hosting]
- GetAssemblyName method [.NET Framework hosting]
ms.assetid: 97801d99-f5f1-4a30-882f-959827093fac
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b983491c3794603bea250e684ee097397aa004a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440175"
---
# <a name="itypenamegetassemblyname-method"></a><span data-ttu-id="2a65b-102">ITypeName::GetAssemblyName メソッド</span><span class="sxs-lookup"><span data-stu-id="2a65b-102">ITypeName::GetAssemblyName Method</span></span>
<span data-ttu-id="2a65b-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="2a65b-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a65b-104">構文</span><span class="sxs-lookup"><span data-stu-id="2a65b-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyName (  
    [out, retval] BSTR* rgbszAssemblyNames  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="2a65b-105">要件</span><span class="sxs-lookup"><span data-stu-id="2a65b-105">Requirements</span></span>  
 <span data-ttu-id="2a65b-106">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2a65b-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a65b-107">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2a65b-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2a65b-108">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="2a65b-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2a65b-109">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a65b-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a65b-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a65b-110">See Also</span></span>  
 [<span data-ttu-id="2a65b-111">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2a65b-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

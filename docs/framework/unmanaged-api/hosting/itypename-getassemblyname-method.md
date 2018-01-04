---
title: "ITypeName::GetAssemblyName メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ITypeName.GetAssemblyName
api_location: mscoree.dll
api_type: COM
f1_keywords: GetAssemblyName
helpviewer_keywords:
- ITypeName::GetAssemblyName method [.NET Framework hosting]
- GetAssemblyName method [.NET Framework hosting]
ms.assetid: 97801d99-f5f1-4a30-882f-959827093fac
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3b7e2c0a34a044f2b26b27c91afb078b80cb37e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="itypenamegetassemblyname-method"></a><span data-ttu-id="1a0a9-102">ITypeName::GetAssemblyName メソッド</span><span class="sxs-lookup"><span data-stu-id="1a0a9-102">ITypeName::GetAssemblyName Method</span></span>
<span data-ttu-id="1a0a9-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="1a0a9-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a0a9-104">構文</span><span class="sxs-lookup"><span data-stu-id="1a0a9-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyName (  
    [out, retval] BSTR* rgbszAssemblyNames  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="1a0a9-105">必要条件</span><span class="sxs-lookup"><span data-stu-id="1a0a9-105">Requirements</span></span>  
 <span data-ttu-id="1a0a9-106">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1a0a9-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a0a9-107">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1a0a9-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1a0a9-108">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="1a0a9-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a0a9-109">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a0a9-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a0a9-110">参照</span><span class="sxs-lookup"><span data-stu-id="1a0a9-110">See Also</span></span>  
 [<span data-ttu-id="1a0a9-111">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1a0a9-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

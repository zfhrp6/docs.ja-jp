---
title: ITypeNameFactory::ParseTypeName メソッド
ms.date: 03/30/2017
api_name:
- ITypeNameFactory.ParseTypeName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ParseTypeName
helpviewer_keywords:
- ITypeNameFactory::ParseTypeName method [.NET Framework hosting]
- ParseTypeName method [.NET Framework hosting]
ms.assetid: 13c9f063-371c-4911-a5e7-e1e0b88ae382
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: adc72eb1b50369e5219798cdb99618abc5e08a00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440390"
---
# <a name="itypenamefactoryparsetypename-method"></a><span data-ttu-id="c4ab7-102">ITypeNameFactory::ParseTypeName メソッド</span><span class="sxs-lookup"><span data-stu-id="c4ab7-102">ITypeNameFactory::ParseTypeName Method</span></span>
<span data-ttu-id="c4ab7-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="c4ab7-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4ab7-104">構文</span><span class="sxs-lookup"><span data-stu-id="c4ab7-104">Syntax</span></span>  
  
```  
HRESULT ParseTypeName (  
    [in]  LPCWSTR             szName,  
    [out] DWORD*              pError,  
    [out, retval] ITypeName** ppTypeName  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="c4ab7-105">要件</span><span class="sxs-lookup"><span data-stu-id="c4ab7-105">Requirements</span></span>  
 <span data-ttu-id="c4ab7-106">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c4ab7-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4ab7-107">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c4ab7-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c4ab7-108">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="c4ab7-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4ab7-109">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4ab7-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4ab7-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4ab7-110">See Also</span></span>  
 [<span data-ttu-id="c4ab7-111">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c4ab7-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

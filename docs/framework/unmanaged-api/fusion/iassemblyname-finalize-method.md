---
title: IAssemblyName::Finalize メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyName.Finalize
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::Finalize
helpviewer_keywords:
- Finalize method [.NET Framework fusion]
- IAssemblyName::Finalize method [.NET Framework fusion]
ms.assetid: 610e792d-98ef-411f-90b0-5b9a3813f547
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 736b9efa1abf0c8ce10d15465b1742879db04ab7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428177"
---
# <a name="iassemblynamefinalize-method"></a><span data-ttu-id="986a3-102">IAssemblyName::Finalize メソッド</span><span class="sxs-lookup"><span data-stu-id="986a3-102">IAssemblyName::Finalize Method</span></span>
<span data-ttu-id="986a3-103">これにより、 [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)オブジェクト リソースを解放し、そのデストラクターが呼び出される前に、他のクリーンアップ操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="986a3-103">Allows this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object to release resources and perform other cleanup operations before its destructor is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="986a3-104">構文</span><span class="sxs-lookup"><span data-stu-id="986a3-104">Syntax</span></span>  
  
```  
HRESULT Finalize ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="986a3-105">要件</span><span class="sxs-lookup"><span data-stu-id="986a3-105">Requirements</span></span>  
 <span data-ttu-id="986a3-106">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="986a3-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="986a3-107">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="986a3-107">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="986a3-108">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="986a3-108">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="986a3-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="986a3-109">See Also</span></span>  
 [<span data-ttu-id="986a3-110">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="986a3-110">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)

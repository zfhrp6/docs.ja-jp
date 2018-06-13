---
title: ICorRuntimeHost::SwitchOutLogicalThreadState メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchOutLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState method [.NET Framework hosting]
- SwitchOutLogicalThreadState method [.NET Framework hosting]
ms.assetid: e1968f0b-2675-4dc2-8507-46164e1df154
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff3bd9345825b5e7a4ccb41cd260b447b74cede3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437951"
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="4d380-102">ICorRuntimeHost::SwitchOutLogicalThreadState メソッド</span><span class="sxs-lookup"><span data-stu-id="4d380-102">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>
<span data-ttu-id="4d380-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="4d380-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d380-104">構文</span><span class="sxs-lookup"><span data-stu-id="4d380-104">Syntax</span></span>  
  
```  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d380-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4d380-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="4d380-106">[out]スイッチ アウトされるファイバーを示すクッキー。</span><span class="sxs-lookup"><span data-stu-id="4d380-106">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d380-107">要件</span><span class="sxs-lookup"><span data-stu-id="4d380-107">Requirements</span></span>  
 <span data-ttu-id="4d380-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4d380-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d380-109">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4d380-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4d380-110">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="4d380-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d380-111">**.NET framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="4d380-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d380-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d380-112">See Also</span></span>  
 [<span data-ttu-id="4d380-113">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4d380-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)

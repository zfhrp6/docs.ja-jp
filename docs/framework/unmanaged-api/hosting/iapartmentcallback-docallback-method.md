---
title: IApartmentCallback::DoCallback メソッド
ms.date: 03/30/2017
api_name:
- IApartmentCallback.DoCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- DoCallback
helpviewer_keywords:
- IApartmentCallback::DoCallback method [.NET Framework hosting]
- DoCallback method [.NET Framework hosting]
ms.assetid: 8edad30c-30ff-4bee-813c-75525a82fc93
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba1dc2a1ec8b0b3b5ec25036cab6362237efe98f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430757"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="dc611-102">IApartmentCallback::DoCallback メソッド</span><span class="sxs-lookup"><span data-stu-id="dc611-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="dc611-103">アパートメント内で指定された関数を実行します。</span><span class="sxs-lookup"><span data-stu-id="dc611-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc611-104">構文</span><span class="sxs-lookup"><span data-stu-id="dc611-104">Syntax</span></span>  
  
```  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc611-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dc611-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="dc611-106">[in]アパートメント内で実行される関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="dc611-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="dc611-107">[in]関数の引数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="dc611-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc611-108">要件</span><span class="sxs-lookup"><span data-stu-id="dc611-108">Requirements</span></span>  
 <span data-ttu-id="dc611-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dc611-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc611-110">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dc611-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dc611-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="dc611-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc611-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc611-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc611-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc611-113">See Also</span></span>  
 [<span data-ttu-id="dc611-114">IApartmentCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dc611-114">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)

---
title: "ICorRuntimeHost::LocksHeldByLogicalThread メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.LocksHeldByLogicalThread
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::LocksHeldByLogicalThread
helpviewer_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread method [.NET Framework hosting]
- LocksHeldByLogicalThread method [.NET Framework hosting]
ms.assetid: c3601255-d894-4d7c-b1df-c31334551700
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 82fa031e4842d81f7ddec3e7eeb64c9d7b02e566
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="82bc0-102">ICorRuntimeHost::LocksHeldByLogicalThread メソッド</span><span class="sxs-lookup"><span data-stu-id="82bc0-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="82bc0-103">現在のスレッドを保持するロックの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="82bc0-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="82bc0-104">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="82bc0-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82bc0-105">構文</span><span class="sxs-lookup"><span data-stu-id="82bc0-105">Syntax</span></span>  
  
```  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82bc0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="82bc0-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="82bc0-107">[out]現在のスレッドを保持するロックの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="82bc0-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82bc0-108">要件</span><span class="sxs-lookup"><span data-stu-id="82bc0-108">Requirements</span></span>  
 <span data-ttu-id="82bc0-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="82bc0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82bc0-110">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="82bc0-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="82bc0-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="82bc0-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82bc0-112">**.NET framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="82bc0-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82bc0-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="82bc0-113">See Also</span></span>  
 [<span data-ttu-id="82bc0-114">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="82bc0-114">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)

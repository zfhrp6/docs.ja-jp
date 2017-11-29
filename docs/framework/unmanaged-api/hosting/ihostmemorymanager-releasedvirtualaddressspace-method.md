---
title: "IHostMemoryManager::ReleasedVirtualAddressSpace メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.ReleasedVirtualAddressSpace
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::ReleasedVirtualAddressSpace
helpviewer_keywords:
- ReleasedVirtualAddressSpace method [.NET Framework hosting]
- IHostMemoryManager::ReleasedVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: d1876601-6ab9-48e1-8ebd-184af1d0cd76
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c0f2588c34429366794fcfb30c6d6e7038814506
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="05830-102">IHostMemoryManager::ReleasedVirtualAddressSpace メソッド</span><span class="sxs-lookup"><span data-stu-id="05830-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>
<span data-ttu-id="05830-103">共通言語ランタイム (CLR) の指定されたメモリの使用が完了したことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="05830-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05830-104">構文</span><span class="sxs-lookup"><span data-stu-id="05830-104">Syntax</span></span>  
  
```  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05830-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="05830-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="05830-106">[in]解放されるメモリの開始アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="05830-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05830-107">コメント</span><span class="sxs-lookup"><span data-stu-id="05830-107">Remarks</span></span>  
 <span data-ttu-id="05830-108">`ReleasedVirtualAddressSpace`メソッドはコールバック メソッドであり、ホスト アプリケーションの作成者によって実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05830-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="05830-109">これは、CLR によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="05830-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05830-110">要件</span><span class="sxs-lookup"><span data-stu-id="05830-110">Requirements</span></span>  
 <span data-ttu-id="05830-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="05830-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05830-112">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="05830-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05830-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="05830-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05830-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05830-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05830-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="05830-115">See Also</span></span>  
 [<span data-ttu-id="05830-116">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="05830-116">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)

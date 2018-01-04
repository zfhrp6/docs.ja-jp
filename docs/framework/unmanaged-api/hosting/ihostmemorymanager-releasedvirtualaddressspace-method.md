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
ms.workload: dotnet
ms.openlocfilehash: d6db2868405aadb5879241e12128c6db40c0a5c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="aeb31-102">IHostMemoryManager::ReleasedVirtualAddressSpace メソッド</span><span class="sxs-lookup"><span data-stu-id="aeb31-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>
<span data-ttu-id="aeb31-103">共通言語ランタイム (CLR) の指定されたメモリの使用が完了したことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="aeb31-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeb31-104">構文</span><span class="sxs-lookup"><span data-stu-id="aeb31-104">Syntax</span></span>  
  
```  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aeb31-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aeb31-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="aeb31-106">[in]解放されるメモリの開始アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aeb31-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aeb31-107">コメント</span><span class="sxs-lookup"><span data-stu-id="aeb31-107">Remarks</span></span>  
 <span data-ttu-id="aeb31-108">`ReleasedVirtualAddressSpace`メソッドはコールバック メソッドであり、ホスト アプリケーションの作成者によって実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aeb31-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="aeb31-109">これは、CLR によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="aeb31-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeb31-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="aeb31-110">Requirements</span></span>  
 <span data-ttu-id="aeb31-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="aeb31-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aeb31-112">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aeb31-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aeb31-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="aeb31-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aeb31-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aeb31-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeb31-115">参照</span><span class="sxs-lookup"><span data-stu-id="aeb31-115">See Also</span></span>  
 [<span data-ttu-id="aeb31-116">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aeb31-116">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)

---
title: "IHostMemoryManager::NeedsVirtualAddressSpace メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.NeedsVirtualAddressSpace
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 62ceb9e5b4d5843b8e2adad344b3ffb662ab3aff
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="0406f-102">IHostMemoryManager::NeedsVirtualAddressSpace メソッド</span><span class="sxs-lookup"><span data-stu-id="0406f-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>
<span data-ttu-id="0406f-103">共通言語ランタイム (CLR) が指定されたメモリを使用しようとしています。 しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="0406f-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0406f-104">構文</span><span class="sxs-lookup"><span data-stu-id="0406f-104">Syntax</span></span>  
  
```  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0406f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0406f-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="0406f-106">[in]メモリの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="0406f-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="0406f-107">[in]メモリのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="0406f-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0406f-108">コメント</span><span class="sxs-lookup"><span data-stu-id="0406f-108">Remarks</span></span>  
 <span data-ttu-id="0406f-109">`NeedsVirtualAddressSpace`メソッドはコールバック メソッドであり、ホスト アプリケーションの作成者によって実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0406f-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="0406f-110">これは、CLR によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0406f-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="0406f-111">ホストが指定されたメモリを使用する CLR をしない場合、E_OUTOFMEMORY HRESULT から返される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0406f-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0406f-112">要件</span><span class="sxs-lookup"><span data-stu-id="0406f-112">Requirements</span></span>  
 <span data-ttu-id="0406f-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0406f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0406f-114">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0406f-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0406f-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="0406f-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0406f-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0406f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0406f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0406f-117">See Also</span></span>  
 [<span data-ttu-id="0406f-118">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0406f-118">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)

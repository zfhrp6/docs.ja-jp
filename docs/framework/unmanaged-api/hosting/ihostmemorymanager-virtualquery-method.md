---
title: "IHostMemoryManager::VirtualQuery メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.VirtualQuery
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::VirtualQuery
helpviewer_keywords:
- IHostMemoryManager::VirtualQuery method [.NET Framework hosting]
- VirtualQuery method [.NET Framework hosting]
ms.assetid: 757af1e6-b9e8-49e7-b5db-342be3aa205f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 82c76ce908dd73fba0a2a0039894f51790b46583
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ihostmemorymanagervirtualquery-method"></a><span data-ttu-id="a6a4b-102">IHostMemoryManager::VirtualQuery メソッド</span><span class="sxs-lookup"><span data-stu-id="a6a4b-102">IHostMemoryManager::VirtualQuery Method</span></span>
<span data-ttu-id="a6a4b-103">対応する Win32 関数の論理ラッパーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="a6a4b-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="a6a4b-104">Win32 実装`VirtualQuery`呼び出しプロセスの仮想アドレス空間内のページの範囲に関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="a6a4b-104">The Win32 implementation of `VirtualQuery` retrieves information about a range of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6a4b-105">構文</span><span class="sxs-lookup"><span data-stu-id="a6a4b-105">Syntax</span></span>  
  
```  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6a4b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a6a4b-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="a6a4b-107">[in]クエリを実行する仮想メモリ内のアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a6a4b-107">[in] A pointer to the address in virtual memory to be queried.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="a6a4b-108">[out]指定したメモリ領域に関する情報を格納する構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a6a4b-108">[out] A pointer to a structure that contains information about the specified memory region.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="a6a4b-109">[in]バッファーのバイト単位のサイズを`lpBuffer`を指します。</span><span class="sxs-lookup"><span data-stu-id="a6a4b-109">[in] The size, in bytes, of the buffer that `lpBuffer` points to.</span></span>  
  
 `pResult`  
 <span data-ttu-id="a6a4b-110">[out]情報バッファーによって返されたバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a6a4b-110">[out] A pointer to the number of bytes returned by the information buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6a4b-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="a6a4b-111">Return Value</span></span>  
  
|<span data-ttu-id="a6a4b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a6a4b-112">HRESULT</span></span>|<span data-ttu-id="a6a4b-113">説明</span><span class="sxs-lookup"><span data-stu-id="a6a4b-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a6a4b-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="a6a4b-114">S_OK</span></span>|<span data-ttu-id="a6a4b-115">`VirtualQuery`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="a6a4b-115">`VirtualQuery` returned successfully.</span></span>|  
|<span data-ttu-id="a6a4b-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a6a4b-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a6a4b-117">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="a6a4b-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a6a4b-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a6a4b-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a6a4b-119">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="a6a4b-119">The call timed out.</span></span>|  
|<span data-ttu-id="a6a4b-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a6a4b-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a6a4b-121">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="a6a4b-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a6a4b-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a6a4b-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a6a4b-123">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="a6a4b-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a6a4b-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a6a4b-124">E_FAIL</span></span>|<span data-ttu-id="a6a4b-125">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="a6a4b-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a6a4b-126">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="a6a4b-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a6a4b-127">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="a6a4b-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6a4b-128">コメント</span><span class="sxs-lookup"><span data-stu-id="a6a4b-128">Remarks</span></span>  
 <span data-ttu-id="a6a4b-129">`VirtualQuery`呼び出し元のプロセス仮想アドレス空間内のページの範囲に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="a6a4b-129">`VirtualQuery` provides information about a range of pages in the virtual address space of the calling process.</span></span> <span data-ttu-id="a6a4b-130">この実装の値を設定する、`pResult`のバイト数のパラメーター情報バッファーに返され、HRESULT 値を返します。</span><span class="sxs-lookup"><span data-stu-id="a6a4b-130">This implementation sets the value of the `pResult` parameter to the number of bytes returned in the information buffer, and returns an HRESULT value.</span></span> <span data-ttu-id="a6a4b-131">Win32 で`VirtualQuery`関数、戻り値は、バッファー サイズ。</span><span class="sxs-lookup"><span data-stu-id="a6a4b-131">In the Win32 `VirtualQuery` function, the return value is the buffer size.</span></span> <span data-ttu-id="a6a4b-132">詳細については、Windows プラットフォームのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6a4b-132">For more information, see the Windows Platform documentation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a6a4b-133">オペレーティング システムの実装`VirtualQuery`デッドロックが発生しないと、ユーザー コードで中断されているランダムなスレッドで完了するまで実行できます。</span><span class="sxs-lookup"><span data-stu-id="a6a4b-133">The operating system's implementation of `VirtualQuery` does not incur deadlock and can run to completion with random threads suspended in user code.</span></span> <span data-ttu-id="a6a4b-134">このメソッドのホストされているバージョンを実装する場合は、注意深くを使用します。</span><span class="sxs-lookup"><span data-stu-id="a6a4b-134">Use great caution when implementing a hosted version of this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6a4b-135">要件</span><span class="sxs-lookup"><span data-stu-id="a6a4b-135">Requirements</span></span>  
 <span data-ttu-id="a6a4b-136">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a6a4b-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6a4b-137">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a6a4b-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a6a4b-138">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="a6a4b-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6a4b-139">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6a4b-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6a4b-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6a4b-140">See Also</span></span>  
 [<span data-ttu-id="a6a4b-141">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6a4b-141">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)

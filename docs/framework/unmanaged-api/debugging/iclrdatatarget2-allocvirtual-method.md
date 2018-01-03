---
title: "ICLRDataTarget2::AllocVirtual メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget2.AllocVirtual
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget2::AllocVirtual
helpviewer_keywords:
- ICLRDataTarget2::AllocVirtual method [.NET Framework debugging]
- AllocVirtual method [.NET Framework debugging]
ms.assetid: e3226230-964b-47fb-9f53-d6fdbeda1e9e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6d869b350217903dda209699f94897b70bc57132
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget2allocvirtual-method"></a><span data-ttu-id="20bfb-102">ICLRDataTarget2::AllocVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="20bfb-102">ICLRDataTarget2::AllocVirtual Method</span></span>
<span data-ttu-id="20bfb-103">このターゲット プロセスのアドレス空間内のメモリを割り当てられません共通言語ランタイム (CLR) データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="20bfb-103">Called by the common language runtime (CLR) data access services to allocate memory in the address space of this target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20bfb-104">構文</span><span class="sxs-lookup"><span data-stu-id="20bfb-104">Syntax</span></span>  
  
```  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20bfb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="20bfb-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="20bfb-106">[in]A`CLRDATA_ADDRESS`割り当てられるメモリの要求の開始アドレスを指定する値。</span><span class="sxs-lookup"><span data-stu-id="20bfb-106">[in] A `CLRDATA_ADDRESS` value that specifies the requested starting address of the memory to be allocated.</span></span>  
  
 `size`  
 <span data-ttu-id="20bfb-107">[in]割り当てられるメモリのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="20bfb-107">[in] The size, in bytes, of the memory to be allocated.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="20bfb-108">[in]メモリの割り当てを制御するフラグ。</span><span class="sxs-lookup"><span data-stu-id="20bfb-108">[in] Flags that control the allocation of memory.</span></span> <span data-ttu-id="20bfb-109">Win32 を参照してください`VirtualAlloc`関数。</span><span class="sxs-lookup"><span data-stu-id="20bfb-109">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `protectFlags`  
 <span data-ttu-id="20bfb-110">[in]割り当てられたメモリの保護属性。</span><span class="sxs-lookup"><span data-stu-id="20bfb-110">[in] The protection attributes for the allocated memory.</span></span> <span data-ttu-id="20bfb-111">Win32 を参照してください`VirtualAlloc`関数。</span><span class="sxs-lookup"><span data-stu-id="20bfb-111">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `virt`  
 <span data-ttu-id="20bfb-112">[out]ポインター、`CLRDATA_ADDRESS`割り当てられたメモリの実際の開始アドレスを指定する値。</span><span class="sxs-lookup"><span data-stu-id="20bfb-112">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the actual starting address of the allocated memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20bfb-113">コメント</span><span class="sxs-lookup"><span data-stu-id="20bfb-113">Remarks</span></span>  
 <span data-ttu-id="20bfb-114">`AllocVirtual`メソッドは、Win32 の論理ラッパーとして機能`VirtualAlloc`関数。</span><span class="sxs-lookup"><span data-stu-id="20bfb-114">The `AllocVirtual` method serves as a logical wrapper for the Win32 `VirtualAlloc` function.</span></span>  
  
 <span data-ttu-id="20bfb-115">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="20bfb-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20bfb-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="20bfb-116">Requirements</span></span>  
 <span data-ttu-id="20bfb-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="20bfb-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20bfb-118">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="20bfb-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="20bfb-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20bfb-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20bfb-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20bfb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20bfb-121">参照</span><span class="sxs-lookup"><span data-stu-id="20bfb-121">See Also</span></span>  
 [<span data-ttu-id="20bfb-122">ICLRDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20bfb-122">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="20bfb-123">FreeVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="20bfb-123">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)

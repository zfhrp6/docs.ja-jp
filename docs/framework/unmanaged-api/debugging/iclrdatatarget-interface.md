---
title: "ICLRDataTarget インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget
helpviewer_keywords: ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 73966ffe89f0e84d5a516f20962472d900332faa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="87fff-102">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87fff-102">ICLRDataTarget Interface</span></span>
<span data-ttu-id="87fff-103">共通言語ランタイム (CLR) のターゲット項目と対話するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="87fff-103">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="87fff-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="87fff-104">Methods</span></span>  
  
|<span data-ttu-id="87fff-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="87fff-105">Method</span></span>|<span data-ttu-id="87fff-106">説明</span><span class="sxs-lookup"><span data-stu-id="87fff-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="87fff-107">GetCurrentThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="87fff-107">GetCurrentThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="87fff-108">現在のスレッドのオペレーティング システムの識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="87fff-108">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="87fff-109">GetImageBase メソッド</span><span class="sxs-lookup"><span data-stu-id="87fff-109">GetImageBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="87fff-110">指定したイメージのメモリのベース アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="87fff-110">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="87fff-111">GetMachineType メソッド</span><span class="sxs-lookup"><span data-stu-id="87fff-111">GetMachineType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="87fff-112">ターゲット プロセスを使用している命令セットの種類の識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="87fff-112">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="87fff-113">GetPointerSize メソッド</span><span class="sxs-lookup"><span data-stu-id="87fff-113">GetPointerSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="87fff-114">(バイト単位)、現在のターゲットへのポインターのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="87fff-114">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="87fff-115">GetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="87fff-115">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="87fff-116">指定した識別子のスレッドのコンテキストへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="87fff-116">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="87fff-117">GetTLSValue メソッド</span><span class="sxs-lookup"><span data-stu-id="87fff-117">GetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="87fff-118">指定したスレッドの指定したインデックスにあるスレッド ローカル ストレージ (TLS) の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="87fff-118">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="87fff-119">ReadVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="87fff-119">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="87fff-120">指定されたバッファーに指定された仮想メモリ アドレスからデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="87fff-120">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="87fff-121">Request メソッド</span><span class="sxs-lookup"><span data-stu-id="87fff-121">Request Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|<span data-ttu-id="87fff-122">実装によって定義されているように、操作を要求する共通言語ランタイム (CLR) データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="87fff-122">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="87fff-123">SetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="87fff-123">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="87fff-124">ターゲット プロセスで指定されたスレッドの現在のコンテキストを設定します。</span><span class="sxs-lookup"><span data-stu-id="87fff-124">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="87fff-125">SetTLSValue メソッド</span><span class="sxs-lookup"><span data-stu-id="87fff-125">SetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="87fff-126">ターゲット プロセス内の指定されたスレッドのスレッド ローカル ストレージ (TLS) の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="87fff-126">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="87fff-127">WriteVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="87fff-127">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="87fff-128">指定された仮想メモリ アドレスに指定されたバッファーからデータを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="87fff-128">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87fff-129">コメント</span><span class="sxs-lookup"><span data-stu-id="87fff-129">Remarks</span></span>  
 <span data-ttu-id="87fff-130">API クライアント (つまりデバッガー) は、特定のターゲット項目に応じてこのインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="87fff-130">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="87fff-131">たとえば、ライブ プロセスの実装は、メモリ ダンプの実装とは異なります。</span><span class="sxs-lookup"><span data-stu-id="87fff-131">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87fff-132">必要条件</span><span class="sxs-lookup"><span data-stu-id="87fff-132">Requirements</span></span>  
 <span data-ttu-id="87fff-133">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="87fff-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87fff-134">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="87fff-134">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="87fff-135">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87fff-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87fff-136">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87fff-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87fff-137">参照</span><span class="sxs-lookup"><span data-stu-id="87fff-137">See Also</span></span>  
 [<span data-ttu-id="87fff-138">ICLRDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87fff-138">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="87fff-139">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87fff-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

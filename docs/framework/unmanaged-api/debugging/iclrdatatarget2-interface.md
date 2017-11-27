---
title: "ICLRDataTarget2 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget2
helpviewer_keywords: ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1780df0a4659d232a27faf4fdc2f6c9b13db98a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="2afd7-102">ICLRDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2afd7-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="2afd7-103">サブクラス[ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)ターゲット プロセスの仮想メモリ領域を操作するデータ アクセス サービス層で使用されます。</span><span class="sxs-lookup"><span data-stu-id="2afd7-103">A subclass of [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2afd7-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="2afd7-104">Methods</span></span>  
  
|<span data-ttu-id="2afd7-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="2afd7-105">Method</span></span>|<span data-ttu-id="2afd7-106">説明</span><span class="sxs-lookup"><span data-stu-id="2afd7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2afd7-107">AllocVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="2afd7-107">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="2afd7-108">ターゲット プロセスのアドレス空間内のメモリを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="2afd7-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="2afd7-109">FreeVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="2afd7-109">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="2afd7-110">ターゲット プロセスのアドレス空間に割り当てられていたメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="2afd7-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2afd7-111">コメント</span><span class="sxs-lookup"><span data-stu-id="2afd7-111">Remarks</span></span>  
 <span data-ttu-id="2afd7-112">API クライアント (つまりデバッガー) は、特定のターゲット プロセスに応じてこのインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2afd7-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="2afd7-113">たとえば、ライブ プロセスの実装は、メモリ ダンプの実装とは異なります。</span><span class="sxs-lookup"><span data-stu-id="2afd7-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="2afd7-114">ターゲットは、メモリ領域の変更をサポートしない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2afd7-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2afd7-115">要件</span><span class="sxs-lookup"><span data-stu-id="2afd7-115">Requirements</span></span>  
 <span data-ttu-id="2afd7-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2afd7-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2afd7-117">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="2afd7-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="2afd7-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2afd7-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2afd7-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2afd7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2afd7-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="2afd7-120">See Also</span></span>  
 [<span data-ttu-id="2afd7-121">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2afd7-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [<span data-ttu-id="2afd7-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="2afd7-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

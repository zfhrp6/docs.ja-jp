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
ms.workload: dotnet
ms.openlocfilehash: a8d8dc7aad35e38b2f9d3b5fb48dacbe1d22bd34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="051e3-102">ICLRDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="051e3-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="051e3-103">サブクラス[ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)ターゲット プロセスの仮想メモリ領域を操作するデータ アクセス サービス層で使用されます。</span><span class="sxs-lookup"><span data-stu-id="051e3-103">A subclass of [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="051e3-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="051e3-104">Methods</span></span>  
  
|<span data-ttu-id="051e3-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="051e3-105">Method</span></span>|<span data-ttu-id="051e3-106">説明</span><span class="sxs-lookup"><span data-stu-id="051e3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="051e3-107">AllocVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="051e3-107">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="051e3-108">ターゲット プロセスのアドレス空間内のメモリを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="051e3-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="051e3-109">FreeVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="051e3-109">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="051e3-110">ターゲット プロセスのアドレス空間に割り当てられていたメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="051e3-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="051e3-111">コメント</span><span class="sxs-lookup"><span data-stu-id="051e3-111">Remarks</span></span>  
 <span data-ttu-id="051e3-112">API クライアント (つまりデバッガー) は、特定のターゲット プロセスに応じてこのインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="051e3-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="051e3-113">たとえば、ライブ プロセスの実装は、メモリ ダンプの実装とは異なります。</span><span class="sxs-lookup"><span data-stu-id="051e3-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="051e3-114">ターゲットは、メモリ領域の変更をサポートしない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="051e3-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="051e3-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="051e3-115">Requirements</span></span>  
 <span data-ttu-id="051e3-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="051e3-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="051e3-117">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="051e3-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="051e3-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="051e3-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="051e3-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="051e3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="051e3-120">参照</span><span class="sxs-lookup"><span data-stu-id="051e3-120">See Also</span></span>  
 [<span data-ttu-id="051e3-121">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="051e3-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [<span data-ttu-id="051e3-122">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="051e3-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

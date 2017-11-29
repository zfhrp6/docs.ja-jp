---
title: "ICLRDataTarget3 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget3
api_location: mscordbi.dll
api_type: COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16e2d2aa1a2626f4124e1b43ff85abcdd17f6990
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="dcaae-102">ICLRDataTarget3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dcaae-102">ICLRDataTarget3 Interface</span></span>
<span data-ttu-id="dcaae-103">サブクラス[ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)例外情報へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="dcaae-103">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dcaae-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="dcaae-104">Methods</span></span>  
  
|<span data-ttu-id="dcaae-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="dcaae-105">Method</span></span>|<span data-ttu-id="dcaae-106">説明</span><span class="sxs-lookup"><span data-stu-id="dcaae-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dcaae-107">GetExceptionRecord メソッド</span><span class="sxs-lookup"><span data-stu-id="dcaae-107">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="dcaae-108">ターゲット プロセスに関連付けられた例外レコードを取得するために、共通言語ランタイム (CLR: Common Language Runtime) データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="dcaae-108">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="dcaae-109">GetExceptionContextRecord メソッド</span><span class="sxs-lookup"><span data-stu-id="dcaae-109">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="dcaae-110">ターゲット プロセスに関連付けられているコンテキスト レコードを取得するために、CLR データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="dcaae-110">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="dcaae-111">GetExceptionThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="dcaae-111">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="dcaae-112">例外をスローしたスレッドの ID を取得するために、CLR データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="dcaae-112">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcaae-113">コメント</span><span class="sxs-lookup"><span data-stu-id="dcaae-113">Remarks</span></span>  
 <span data-ttu-id="dcaae-114">API クライアント (つまりデバッガー) は、特定のターゲット プロセスに応じてこのインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dcaae-114">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="dcaae-115">たとえば、ライブ プロセスの実装は、メモリ ダンプの実装とは異なります。</span><span class="sxs-lookup"><span data-stu-id="dcaae-115">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="dcaae-116">ターゲットは、メモリ領域の変更をサポートしない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dcaae-116">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcaae-117">要件</span><span class="sxs-lookup"><span data-stu-id="dcaae-117">Requirements</span></span>  
 <span data-ttu-id="dcaae-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dcaae-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcaae-119">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="dcaae-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="dcaae-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dcaae-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcaae-121">**.NET framework のバージョン:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcaae-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcaae-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="dcaae-122">See Also</span></span>  
 [<span data-ttu-id="dcaae-123">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dcaae-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [<span data-ttu-id="dcaae-124">ICLRDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dcaae-124">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="dcaae-125">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="dcaae-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

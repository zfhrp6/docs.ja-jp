---
title: "ICorDebugDataTarget インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugDataTarget
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugDataTarget
helpviewer_keywords: ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 030ad5e61d215bd840da5b16a56e4b8f8b7791ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget-interface"></a><span data-ttu-id="11c24-102">ICorDebugDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11c24-102">ICorDebugDataTarget Interface</span></span>
<span data-ttu-id="11c24-103">特定のターゲット プロセスにアクセスするためのコールバック インターフェイスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="11c24-103">Provides a callback interface that provides access to a particular target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="11c24-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="11c24-104">Methods</span></span>  
  
|<span data-ttu-id="11c24-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="11c24-105">Method</span></span>|<span data-ttu-id="11c24-106">説明</span><span class="sxs-lookup"><span data-stu-id="11c24-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="11c24-107">GetPlatform メソッド</span><span class="sxs-lookup"><span data-stu-id="11c24-107">GetPlatform Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|<span data-ttu-id="11c24-108">プロセッサ アーキテクチャと、ターゲット プロセスが実行されているオペレーティング システムを含む、プラットフォームに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="11c24-108">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>|  
|[<span data-ttu-id="11c24-109">ReadVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="11c24-109">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|<span data-ttu-id="11c24-110">指定したアドレスから始まる連続したメモリのブロックを取得し、指定されたバッファーで返します。</span><span class="sxs-lookup"><span data-stu-id="11c24-110">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>|  
|[<span data-ttu-id="11c24-111">GetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="11c24-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|<span data-ttu-id="11c24-112">指定したスレッドの現在のスレッド コンテキストを要求します。</span><span class="sxs-lookup"><span data-stu-id="11c24-112">Requests the current thread context for the specified thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11c24-113">コメント</span><span class="sxs-lookup"><span data-stu-id="11c24-113">Remarks</span></span>  
 <span data-ttu-id="11c24-114">`ICorDebugDataTarget`そのメソッドに次の特性があります。</span><span class="sxs-lookup"><span data-stu-id="11c24-114">`ICorDebugDataTarget` and its methods have the following characteristics:</span></span>  
  
-   <span data-ttu-id="11c24-115">デバッグ サービスでは、メモリやターゲット プロセスの他のデータにアクセスするには、このインターフェイスでメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="11c24-115">The debugging services call methods on this interface to access memory and other data in the target process.</span></span>  
  
-   <span data-ttu-id="11c24-116">デバッガー クライアントでは、特定のターゲット (たとえば、ライブ プロセスまたはメモリ ダンプ) に応じてこのインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11c24-116">The debugger client must implement this interface as appropriate for the particular target (for example, a live process or a memory dump).</span></span>  
  
-   <span data-ttu-id="11c24-117">`ICorDebugDataTarget`メソッドは、他の実装されているメソッド内からのみ呼び出すことができます`ICorDebug*`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="11c24-117">The `ICorDebugDataTarget` methods can be invoked only from within methods implemented in other `ICorDebug*` interfaces.</span></span> <span data-ttu-id="11c24-118">これにより、どのスレッドが呼び出されると、デバッガーのクライアントが制御することです。</span><span class="sxs-lookup"><span data-stu-id="11c24-118">This ensures that the debugger client has control over which thread it is invoked on, and when.</span></span>  
  
-   <span data-ttu-id="11c24-119">`ICorDebugDataTarget`実装では、ターゲットに関する最新の情報を返す必要があります常にします。</span><span class="sxs-lookup"><span data-stu-id="11c24-119">The `ICorDebugDataTarget` implementation must always return up-to-date information about the target.</span></span>  
  
 <span data-ttu-id="11c24-120">ターゲット プロセスを停止しているときに任意の方法で変更されていない必要があります`ICorDebug*`インターフェイス (および`ICorDebugDataTarget`メソッド) が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="11c24-120">The target process should be stopped and not changed in any way while `ICorDebug*` interfaces (and therefore `ICorDebugDataTarget` methods) are being called.</span></span> <span data-ttu-id="11c24-121">ターゲットがライブ プロセスとその状態の変更の場合、 [iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)置換 ICorDebugProcess インスタンスを提供する、もう一度呼び出されるメソッドには。</span><span class="sxs-lookup"><span data-stu-id="11c24-121">If the target is a live process and its state changes, the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method has to be called again to provide a replacement ICorDebugProcess instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11c24-122">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="11c24-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11c24-123">要件</span><span class="sxs-lookup"><span data-stu-id="11c24-123">Requirements</span></span>  
 <span data-ttu-id="11c24-124">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="11c24-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11c24-125">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11c24-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11c24-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11c24-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11c24-127">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11c24-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11c24-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="11c24-128">See Also</span></span>  
 [<span data-ttu-id="11c24-129">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="11c24-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="11c24-130">デバッグ</span><span class="sxs-lookup"><span data-stu-id="11c24-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

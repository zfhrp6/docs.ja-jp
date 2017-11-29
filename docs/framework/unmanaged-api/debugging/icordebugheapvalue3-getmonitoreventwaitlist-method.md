---
title: "ICorDebugHeapValue3::GetMonitorEventWaitList メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3.GetMonitorEventWaitList
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2624a5dcd2179f35567d19e33e4f981c5d049063
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a><span data-ttu-id="789db-102">ICorDebugHeapValue3::GetMonitorEventWaitList メソッド</span><span class="sxs-lookup"><span data-stu-id="789db-102">ICorDebugHeapValue3::GetMonitorEventWaitList Method</span></span>
<span data-ttu-id="789db-103">モニター ロックに関連付けられているイベントでは、キュー内のスレッドの順序付きリストを提供します。</span><span class="sxs-lookup"><span data-stu-id="789db-103">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="789db-104">構文</span><span class="sxs-lookup"><span data-stu-id="789db-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="789db-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="789db-105">Parameters</span></span>  
 `ppThreadEnum`  
 <span data-ttu-id="789db-106">[out]スレッドの順序付きリストを提供する ICorDebugThreadEnum 列挙子。</span><span class="sxs-lookup"><span data-stu-id="789db-106">[out] The ICorDebugThreadEnum enumerator that provides the ordered list of threads.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="789db-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="789db-107">Return Value</span></span>  
 <span data-ttu-id="789db-108">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="789db-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="789db-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="789db-109">HRESULT</span></span>|<span data-ttu-id="789db-110">説明</span><span class="sxs-lookup"><span data-stu-id="789db-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="789db-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="789db-111">S_OK</span></span>|<span data-ttu-id="789db-112">The list is not empty.</span><span class="sxs-lookup"><span data-stu-id="789db-112">The list is not empty.</span></span>|  
|<span data-ttu-id="789db-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="789db-113">S_FALSE</span></span>|<span data-ttu-id="789db-114">リストが空です。</span><span class="sxs-lookup"><span data-stu-id="789db-114">The list is empty.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="789db-115">例外</span><span class="sxs-lookup"><span data-stu-id="789db-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="789db-116">コメント</span><span class="sxs-lookup"><span data-stu-id="789db-116">Remarks</span></span>  
 <span data-ttu-id="789db-117">一覧の最初のスレッドは、次の呼び出しによってリリースされた最初のスレッド<xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="789db-117">The first thread in the list is the first thread that is released by the next call to <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span></span> <span data-ttu-id="789db-118">一覧で、[次へ] のスレッドは、次の呼び出し時に解放されます。</span><span class="sxs-lookup"><span data-stu-id="789db-118">The next thread in the list is released on the following call, and so on.</span></span>  
  
 <span data-ttu-id="789db-119">リストが空でない場合、このメソッドは、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="789db-119">If the list is not empty, this method returns S_OK.</span></span> <span data-ttu-id="789db-120">メソッドは S_FALSE; を返します、リストが空の場合ここでは、列挙体がまだ有効では空です。</span><span class="sxs-lookup"><span data-stu-id="789db-120">If the list is empty, the method returns S_FALSE; in this case, the enumeration is still valid, although it is empty.</span></span>  
  
 <span data-ttu-id="789db-121">どちらの場合、列挙インターフェイスは、現在の同期状態の期間に対してのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="789db-121">In either case, the enumeration interface is usable only for the duration of the current synchronized state.</span></span> <span data-ttu-id="789db-122">ただし、これから管理されているスレッドのインターフェイスは、スレッドを終了するまで無効です。</span><span class="sxs-lookup"><span data-stu-id="789db-122">However, the thread's interfaces dispensed from it are valid until the thread exits.</span></span>  
  
 <span data-ttu-id="789db-123">場合`ppThreadEnum`は有効なポインターではありません、結果は未定義です。</span><span class="sxs-lookup"><span data-stu-id="789db-123">If `ppThreadEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="789db-124">スレッドが、モニターを待機している場合、これを確認できないように、エラーが発生した場合、メソッドは失敗を示す HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="789db-124">If an error occurs such that it cannot be determined which, if any, threads are waiting for the monitor, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="789db-125">要件</span><span class="sxs-lookup"><span data-stu-id="789db-125">Requirements</span></span>  
 <span data-ttu-id="789db-126">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="789db-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="789db-127">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="789db-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="789db-128">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="789db-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="789db-129">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="789db-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="789db-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="789db-130">See Also</span></span>  
 [<span data-ttu-id="789db-131">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="789db-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="789db-132">デバッグ</span><span class="sxs-lookup"><span data-stu-id="789db-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

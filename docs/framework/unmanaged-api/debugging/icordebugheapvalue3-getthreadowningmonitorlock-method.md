---
title: "ICorDebugHeapValue3::GetThreadOwningMonitorLock メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1a2198e54c764fde0248563b040ac98984001888
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="715c6-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock メソッド</span><span class="sxs-lookup"><span data-stu-id="715c6-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>
<span data-ttu-id="715c6-103">このオブジェクトのモニター ロックを所有するマネージ スレッドを返します。</span><span class="sxs-lookup"><span data-stu-id="715c6-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="715c6-104">構文</span><span class="sxs-lookup"><span data-stu-id="715c6-104">Syntax</span></span>  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="715c6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="715c6-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="715c6-106">[out]このオブジェクトのモニター ロックを所有するマネージ スレッドです。</span><span class="sxs-lookup"><span data-stu-id="715c6-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="715c6-107">[out]このスレッドが所有されていない中に返す前に、ロックを解除する必要があります回数。</span><span class="sxs-lookup"><span data-stu-id="715c6-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="715c6-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="715c6-108">Return Value</span></span>  
 <span data-ttu-id="715c6-109">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="715c6-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="715c6-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="715c6-110">HRESULT</span></span>|<span data-ttu-id="715c6-111">説明</span><span class="sxs-lookup"><span data-stu-id="715c6-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="715c6-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="715c6-112">S_OK</span></span>|<span data-ttu-id="715c6-113">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="715c6-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="715c6-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="715c6-114">S_FALSE</span></span>|<span data-ttu-id="715c6-115">このオブジェクトのモニター ロックを所有するマネージ スレッドがありません。</span><span class="sxs-lookup"><span data-stu-id="715c6-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="715c6-116">例外</span><span class="sxs-lookup"><span data-stu-id="715c6-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="715c6-117">コメント</span><span class="sxs-lookup"><span data-stu-id="715c6-117">Remarks</span></span>  
 <span data-ttu-id="715c6-118">マネージ スレッドは、このオブジェクトのモニター ロックを所有している: 場合</span><span class="sxs-lookup"><span data-stu-id="715c6-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
-   <span data-ttu-id="715c6-119">このメソッドは、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="715c6-119">The method returns S_OK.</span></span>  
  
-   <span data-ttu-id="715c6-120">スレッド オブジェクトは、スレッドが終了するまで有効です。</span><span class="sxs-lookup"><span data-stu-id="715c6-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="715c6-121">マネージ スレッドに、このオブジェクトのモニター ロックを所有していない場合`ppThread`と`pAcquisitionCount`は変更されず、S_FALSE が返されます。</span><span class="sxs-lookup"><span data-stu-id="715c6-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="715c6-122">場合`ppThread`または`pAcquisitionCount`は有効なポインターではありません、結果は未定義です。</span><span class="sxs-lookup"><span data-stu-id="715c6-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="715c6-123">スレッドがこのオブジェクトのモニター ロックを所有している場合、これを確認できないように、エラーが発生した場合、メソッドは失敗を示す HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="715c6-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="715c6-124">必要条件</span><span class="sxs-lookup"><span data-stu-id="715c6-124">Requirements</span></span>  
 <span data-ttu-id="715c6-125">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="715c6-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="715c6-126">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="715c6-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="715c6-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="715c6-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="715c6-128">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="715c6-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="715c6-129">参照</span><span class="sxs-lookup"><span data-stu-id="715c6-129">See Also</span></span>  
 [<span data-ttu-id="715c6-130">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="715c6-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="715c6-131">デバッグ</span><span class="sxs-lookup"><span data-stu-id="715c6-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

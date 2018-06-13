---
title: ICorDebugThread4::HadUnhandledException メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.HadUnhandledException Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8215ddfd0f59f835d0b0dcd278b8cae9c12027d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422111"
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="050d6-102">ICorDebugThread4::HadUnhandledException メソッド</span><span class="sxs-lookup"><span data-stu-id="050d6-102">ICorDebugThread4::HadUnhandledException Method</span></span>
<span data-ttu-id="050d6-103">スレッドが未処理の例外をしたかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="050d6-103">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="050d6-104">構文</span><span class="sxs-lookup"><span data-stu-id="050d6-104">Syntax</span></span>  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="050d6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="050d6-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="050d6-106">[out]順序付けされた列挙体のアドレスへのポインター [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)構造体。</span><span class="sxs-lookup"><span data-stu-id="050d6-106">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="050d6-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="050d6-107">Return Value</span></span>  
 <span data-ttu-id="050d6-108">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="050d6-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="050d6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="050d6-109">HRESULT</span></span>|<span data-ttu-id="050d6-110">説明</span><span class="sxs-lookup"><span data-stu-id="050d6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="050d6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="050d6-111">S_OK</span></span>|<span data-ttu-id="050d6-112">スレッドは、未処理の例外の作成後で発生しました。</span><span class="sxs-lookup"><span data-stu-id="050d6-112">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="050d6-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="050d6-113">S_FALSE</span></span>|<span data-ttu-id="050d6-114">スレッドは、未処理の例外にしたことがないです。</span><span class="sxs-lookup"><span data-stu-id="050d6-114">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="050d6-115">コメント</span><span class="sxs-lookup"><span data-stu-id="050d6-115">Remarks</span></span>  
 <span data-ttu-id="050d6-116">このメソッドは、スレッドが未処理の例外をしたかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="050d6-116">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="050d6-117">時間でハンドルされない例外コールバックをトリガーまたはネイティブの JIT アタッチが開始されると、このメソッドが S_OK を返す保証します。</span><span class="sxs-lookup"><span data-stu-id="050d6-117">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="050d6-118">保証がないこと、 [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)メソッドは、未処理の例外を返します以外のかどうか、プロセスが続行されていないかしたときに、ハンドルされない例外コールバックを取得した後、ただし、ネイティブ JIT アタッチします。</span><span class="sxs-lookup"><span data-stu-id="050d6-118">There is no guarantee that the [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="050d6-119">さらに、可能であれば (可能性は低いですが、ネイティブ JIT アタッチがトリガーされた時点で未処理の例外を持つ複数のスレッドにします。</span><span class="sxs-lookup"><span data-stu-id="050d6-119">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="050d6-120">このような場合は、どの例外が JIT アタッチをトリガーを決定する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="050d6-120">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="050d6-121">要件</span><span class="sxs-lookup"><span data-stu-id="050d6-121">Requirements</span></span>  
 <span data-ttu-id="050d6-122">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="050d6-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="050d6-123">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="050d6-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="050d6-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="050d6-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="050d6-125">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="050d6-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="050d6-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="050d6-126">See Also</span></span>  
 [<span data-ttu-id="050d6-127">ICorDebugThread4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="050d6-127">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="050d6-128">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="050d6-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="050d6-129">デバッグ</span><span class="sxs-lookup"><span data-stu-id="050d6-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

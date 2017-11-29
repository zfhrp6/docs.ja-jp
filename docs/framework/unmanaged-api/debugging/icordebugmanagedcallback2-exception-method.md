---
title: "ICorDebugManagedCallback2::Exception メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.Exception
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a78900a6e37c3ae136489c35da7b0cd2931f24a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="42783-102">ICorDebugManagedCallback2::Exception メソッド</span><span class="sxs-lookup"><span data-stu-id="42783-102">ICorDebugManagedCallback2::Exception Method</span></span>
<span data-ttu-id="42783-103">例外ハンドラーの検索が開始されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="42783-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42783-104">構文</span><span class="sxs-lookup"><span data-stu-id="42783-104">Syntax</span></span>  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42783-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="42783-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="42783-106">[in]ICorDebugAppDomain を表すオブジェクトを含む例外がスローされたスレッドのアプリケーション ドメインへのポインター。</span><span class="sxs-lookup"><span data-stu-id="42783-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="42783-107">[in]例外がスローされたスレッドを表す ICorDebugThread オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="42783-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="42783-108">[in]によって決定されたように、フレームを表す ICorDebugFrame オブジェクトへのポインター、`dwEventType`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="42783-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="42783-109">詳細については、「解説」セクションの表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42783-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="42783-110">[in]によって決定される、オフセットを指定する整数、`dwEventType`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="42783-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="42783-111">詳細については、「解説」セクションの表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42783-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="42783-112">[in]この例外コールバックの型を指定する CorDebugExceptionCallbackType 列挙型の値です。</span><span class="sxs-lookup"><span data-stu-id="42783-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="42783-113">[in]値、 [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)例外に関する追加情報を指定する列挙体</span><span class="sxs-lookup"><span data-stu-id="42783-113">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42783-114">コメント</span><span class="sxs-lookup"><span data-stu-id="42783-114">Remarks</span></span>  
 <span data-ttu-id="42783-115">`Exception`フェーズでは、検索、例外処理プロセスのさまざまな時点で呼び出されるコールバック。</span><span class="sxs-lookup"><span data-stu-id="42783-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="42783-116">つまり、呼び出すことができますを超える 1 回、例外のアンワインド中にします。</span><span class="sxs-lookup"><span data-stu-id="42783-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="42783-117">によって参照される ICorDebugThread オブジェクトから処理される例外を取得できる、`pThread`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="42783-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="42783-118">特定のフレームとのオフセットによって決定されます、`dwEventType`次のようにパラメーター。</span><span class="sxs-lookup"><span data-stu-id="42783-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="42783-119">`dwEventType` の値</span><span class="sxs-lookup"><span data-stu-id="42783-119">Value of `dwEventType`</span></span>|<span data-ttu-id="42783-120">`pFrame` の値</span><span class="sxs-lookup"><span data-stu-id="42783-120">Value of `pFrame`</span></span>|<span data-ttu-id="42783-121">`nOffset` の値</span><span class="sxs-lookup"><span data-stu-id="42783-121">Value of `nOffset`</span></span>|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="42783-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="42783-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="42783-123">例外をスローしたフレームです。</span><span class="sxs-lookup"><span data-stu-id="42783-123">The frame that threw the exception.</span></span>|<span data-ttu-id="42783-124">フレーム内の命令ポインター。</span><span class="sxs-lookup"><span data-stu-id="42783-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="42783-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="42783-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="42783-126">スローされた例外の位置に最も近いユーザー コード フレーム。</span><span class="sxs-lookup"><span data-stu-id="42783-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="42783-127">フレーム内の命令ポインター。</span><span class="sxs-lookup"><span data-stu-id="42783-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="42783-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="42783-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="42783-129">Catch ハンドラーを含むフレーム。</span><span class="sxs-lookup"><span data-stu-id="42783-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="42783-130">Catch ハンドラーの最初の Microsoft intermediate language (MSIL) オフセットします。</span><span class="sxs-lookup"><span data-stu-id="42783-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="42783-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="42783-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="42783-132">NULL</span><span class="sxs-lookup"><span data-stu-id="42783-132">NULL</span></span>|<span data-ttu-id="42783-133">定義されていません。</span><span class="sxs-lookup"><span data-stu-id="42783-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="42783-134">要件</span><span class="sxs-lookup"><span data-stu-id="42783-134">Requirements</span></span>  
 <span data-ttu-id="42783-135">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="42783-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42783-136">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42783-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42783-137">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42783-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42783-138">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42783-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42783-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="42783-139">See Also</span></span>  
 [<span data-ttu-id="42783-140">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42783-140">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="42783-141">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42783-141">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

---
title: "ICorDebugModule3::CreateReaderForInMemorySymbols メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule3.CreateReaderForInMemorySymbols
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fbab155e783d3b5e40da466fef56633317c67042
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="cd158-102">ICorDebugModule3::CreateReaderForInMemorySymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="cd158-102">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>
<span data-ttu-id="cd158-103">動的モジュールのデバッグ シンボル リーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="cd158-103">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd158-104">構文</span><span class="sxs-lookup"><span data-stu-id="cd158-104">Syntax</span></span>  
  
```  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd158-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cd158-105">Parameters</span></span>  
 <span data-ttu-id="cd158-106">riid</span><span class="sxs-lookup"><span data-stu-id="cd158-106">riid</span></span>  
 <span data-ttu-id="cd158-107">[in]返す COM インターフェイスの IID です。</span><span class="sxs-lookup"><span data-stu-id="cd158-107">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="cd158-108">通常、これは、 [ISymUnmanagedReader インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="cd158-108">Typically, this is an [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="cd158-109">ppObj</span><span class="sxs-lookup"><span data-stu-id="cd158-109">ppObj</span></span>  
 <span data-ttu-id="cd158-110">[out]返されたインターフェイスへのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="cd158-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd158-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="cd158-111">Return Value</span></span>  
 <span data-ttu-id="cd158-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="cd158-112">S_OK</span></span>  
 <span data-ttu-id="cd158-113">リーダーが正常に作成します。</span><span class="sxs-lookup"><span data-stu-id="cd158-113">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="cd158-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="cd158-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="cd158-115">モジュールは、メモリ内または動的モジュールではありません。</span><span class="sxs-lookup"><span data-stu-id="cd158-115">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="cd158-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cd158-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="cd158-117">シンボルは、アプリケーションによって提供されていないまたはまだ利用できません。</span><span class="sxs-lookup"><span data-stu-id="cd158-117">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="cd158-118">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="cd158-118">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="cd158-119">リーダーを作成できません。</span><span class="sxs-lookup"><span data-stu-id="cd158-119">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd158-120">コメント</span><span class="sxs-lookup"><span data-stu-id="cd158-120">Remarks</span></span>  
 <span data-ttu-id="cd158-121">このメソッドも、メモリ内の (動的ではない) モジュールのシンボル リーダー オブジェクトを作成するために使用されるのみするシンボルが利用可能にした後 (によって示される、 [UpdateModuleSymbols メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)コールバック)。</span><span class="sxs-lookup"><span data-stu-id="cd158-121">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="cd158-122">このメソッドが呼び出されるたびに、新しいリーダー インスタンスを返します (と同様に[CComPtrBase::CoCreateInstance](http://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6))。</span><span class="sxs-lookup"><span data-stu-id="cd158-122">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](http://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6)).</span></span> <span data-ttu-id="cd158-123">そのため、デバッガーが結果をキャッシュして、基になるデータが変更された場合にのみ、新しいインスタンスを要求する必要があります (つまり場合、 [LoadClass メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)コールバックを受信した)。</span><span class="sxs-lookup"><span data-stu-id="cd158-123">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="cd158-124">最初の型が読み込まれるまで動的モジュールは使用可能なすべてのシンボルはありません (によって示される、 [LoadClass メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)コールバック)。</span><span class="sxs-lookup"><span data-stu-id="cd158-124">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd158-125">要件</span><span class="sxs-lookup"><span data-stu-id="cd158-125">Requirements</span></span>  
 <span data-ttu-id="cd158-126">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cd158-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd158-127">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd158-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd158-128">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd158-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd158-129">**.NET framework のバージョン:** 4.5、4、3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="cd158-129">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd158-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd158-130">See Also</span></span>  
 [<span data-ttu-id="cd158-131">ICorDebugRemoteTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd158-131">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="cd158-132">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd158-132">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="cd158-133">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd158-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

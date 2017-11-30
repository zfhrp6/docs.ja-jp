---
title: "ICorDebugProcess2::SetDesiredNGENCompilerFlags メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.SetDesiredNGENCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::SetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags method [.NET Framework debugging]
- SetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: 98320175-7c5e-4dbb-8683-86fa82e2641f
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 278f1f79fd929aa8a0c3233e68b30b1154e913ef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a><span data-ttu-id="9ca65-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="9ca65-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="9ca65-103">ランタイムが現在のプロセスにそのイメージを読み込むために、プリコンパイル済みイメージに埋め込む必要があるフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="9ca65-103">Sets the flags that must be embedded in a precompiled image in order for the runtime to load that image into the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ca65-104">構文</span><span class="sxs-lookup"><span data-stu-id="9ca65-104">Syntax</span></span>  
  
```  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ca65-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ca65-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="9ca65-106">[in]値、 [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)コンパイラ フラグを指定する列挙体は正しいのコンパイル済みのイメージを選択して使用します。</span><span class="sxs-lookup"><span data-stu-id="9ca65-106">[in] A value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the compiler flags used to select the correct pre-compiled image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ca65-107">コメント</span><span class="sxs-lookup"><span data-stu-id="9ca65-107">Remarks</span></span>  
 <span data-ttu-id="9ca65-108">`SetDesiredNGENCompilerFlags`メソッドは、ランタイムはこのプロセスにそのイメージを読み込むようにプリコンパイル済みイメージに埋め込む必要があるフラグを指定します。</span><span class="sxs-lookup"><span data-stu-id="9ca65-108">The `SetDesiredNGENCompilerFlags` method specifies the flags that must be embedded in a precompiled image so that the runtime will load that image into this process.</span></span> <span data-ttu-id="9ca65-109">このメソッドによって設定されたフラグは、適切なプリコンパイル済みイメージを選択するだけに使用されます。</span><span class="sxs-lookup"><span data-stu-id="9ca65-109">The flags set by this method are used only to select the correct precompiled image.</span></span> <span data-ttu-id="9ca65-110">このようなイメージが存在しない場合、ランタイムは Microsoft intermediate language (MSIL) のイメージを読み込み、・ イン タイム (JIT) コンパイラ代わりにします。</span><span class="sxs-lookup"><span data-stu-id="9ca65-110">If no such image exists, the runtime will load the Microsoft intermediate language (MSIL) image and the just-in-time (JIT) compiler instead.</span></span> <span data-ttu-id="9ca65-111">その場合は、デバッガーを使用する必要がありますが、 [icordebugmodule 2::setjitcompilerflags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) JIT コンパイルの必要に応じて、フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="9ca65-111">In that case, the debugger must still use the [ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) method to set the flags as desired for the JIT compilation.</span></span>  
  
 <span data-ttu-id="9ca65-112">イメージが読み込まれましたが、JIT のコンパイルのいくつか行う必要があります (される場合、イメージには、ジェネリックが含まれている場合) そのイメージの場合、コンパイラ フラグで指定された、`SetDesiredNGENCompilerFlags`余分の JIT コンパイルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="9ca65-112">If an image is loaded, but some JIT compiling must take place for that image (which will be the case if the image contains generics), the compiler flags specified by the `SetDesiredNGENCompilerFlags` method will apply to the extra JIT compilation.</span></span>  
  
 <span data-ttu-id="9ca65-113">`SetDesiredNGENCompilerFlags`中にメソッドを呼び出す必要があります、 [icordebugmanagedcallback::createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="9ca65-113">The `SetDesiredNGENCompilerFlags` method must be called during the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="9ca65-114">呼び出そうとすると、`SetDesiredNGENCompilerFlags`後メソッドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="9ca65-114">Attempts to call the `SetDesiredNGENCompilerFlags` method afterwards will fail.</span></span> <span data-ttu-id="9ca65-115">もないか、フラグを設定しようとが定義されている、`CorDebugJITCompilerFlags`列挙型、または特定のプロセスに対して有効でないは失敗します。</span><span class="sxs-lookup"><span data-stu-id="9ca65-115">Also, attempts to set flags that are either not defined in the `CorDebugJITCompilerFlags` enumeration or are not legal for the given process will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ca65-116">要件</span><span class="sxs-lookup"><span data-stu-id="9ca65-116">Requirements</span></span>  
 <span data-ttu-id="9ca65-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ca65-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ca65-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ca65-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ca65-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ca65-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ca65-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ca65-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ca65-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ca65-121">See Also</span></span>  
 [<span data-ttu-id="9ca65-122">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ca65-122">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="9ca65-123">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ca65-123">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

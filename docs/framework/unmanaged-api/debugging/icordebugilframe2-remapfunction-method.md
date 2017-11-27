---
title: "ICorDebugILFrame2::RemapFunction メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame2.RemapFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4def20bc51d1b01b1c05b81a89fc3c983b4d1219
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframe2remapfunction-method"></a><span data-ttu-id="a070b-102">ICorDebugILFrame2::RemapFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="a070b-102">ICorDebugILFrame2::RemapFunction Method</span></span>
<span data-ttu-id="a070b-103">新しい Microsoft intermediate language (MSIL) オフセットを指定することによって編集された関数を再配置します。</span><span class="sxs-lookup"><span data-stu-id="a070b-103">Remaps an edited function by specifying the new Microsoft intermediate language (MSIL) offset</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a070b-104">構文</span><span class="sxs-lookup"><span data-stu-id="a070b-104">Syntax</span></span>  
  
```  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a070b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a070b-105">Parameters</span></span>  
 `newILOffset`  
 <span data-ttu-id="a070b-106">[in]スタック フレームの新しい MSIL のオフセットの命令ポインターを配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a070b-106">[in] The stack frame's new MSIL offset at which the instruction pointer should be placed.</span></span> <span data-ttu-id="a070b-107">この値は、シーケンス ポイントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a070b-107">This value must be a sequence point.</span></span>  
  
 <span data-ttu-id="a070b-108">この値の有効性を確保する、呼び出し元の役割です。</span><span class="sxs-lookup"><span data-stu-id="a070b-108">It is the caller’s responsibility to ensure the validity of this value.</span></span> <span data-ttu-id="a070b-109">たとえば、MSIL オフセットが、関数の範囲外である場合は無効です。</span><span class="sxs-lookup"><span data-stu-id="a070b-109">For example, the MSIL offset is not valid if it is outside the bounds of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a070b-110">コメント</span><span class="sxs-lookup"><span data-stu-id="a070b-110">Remarks</span></span>  
 <span data-ttu-id="a070b-111">フレームの関数は編集されている場合、デバッガーを呼び出して、`RemapFunction`フレームの関数の最新バージョンにスワップ実行できるようにするメソッド。</span><span class="sxs-lookup"><span data-stu-id="a070b-111">When a frame’s function has been edited, the debugger can call the `RemapFunction` method to swap in the latest version of the frame's function so it can be executed.</span></span> <span data-ttu-id="a070b-112">コードの実行は、指定された MSIL オフセットから開始されます。</span><span class="sxs-lookup"><span data-stu-id="a070b-112">The code execution will begin at the given MSIL offset.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a070b-113">呼び出す`RemapFunction`と同様、呼び出す[icordebugilframe::setip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)、すぐに、スレッドのスタック トレースの生成に関連するすべてのデバッグのインターフェイスを無効になります。</span><span class="sxs-lookup"><span data-stu-id="a070b-113">Calling `RemapFunction`, like calling [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), will immediately invalidate all debugging interfaces that are related to generating a stack trace for the thread.</span></span> <span data-ttu-id="a070b-114">これらのインターフェイスを含める[ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)ICorDebugILFrame、ICorDebugInternalFrame、および ICorDebugNativeFrame です。</span><span class="sxs-lookup"><span data-stu-id="a070b-114">These interfaces include [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame, and ICorDebugNativeFrame.</span></span>  
  
 <span data-ttu-id="a070b-115">`RemapFunction`メソッドは、現在のフレームのコンテキストのみで、次のいずれかでのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="a070b-115">The `RemapFunction` method can be called only in the context of the current frame, and only in one of the following cases:</span></span>  
  
-   <span data-ttu-id="a070b-116">受信後、 [icordebugmanagedcallback 2::functionremapopportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)続行されていないコールバック。</span><span class="sxs-lookup"><span data-stu-id="a070b-116">After receipt of a [ICorDebugManagedCallback2::FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) callback that has not yet been continued.</span></span>  
  
-   <span data-ttu-id="a070b-117">ためにコードの実行が停止している間、 [icordebugmanagedcallback::editandcontinueremap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)このフレームのイベントです。</span><span class="sxs-lookup"><span data-stu-id="a070b-117">While code execution is stopped because of an [ICorDebugManagedCallback::EditAndContinueRemap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) event for this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a070b-118">要件</span><span class="sxs-lookup"><span data-stu-id="a070b-118">Requirements</span></span>  
 <span data-ttu-id="a070b-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a070b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a070b-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a070b-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a070b-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a070b-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a070b-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a070b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

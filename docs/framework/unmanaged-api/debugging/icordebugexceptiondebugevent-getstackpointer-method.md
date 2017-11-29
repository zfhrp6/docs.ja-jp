---
title: "ICorDebugExceptionDebugEvent::GetStackPointer メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 17a7540c25eb1273add430c3a8ae01eea35497e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="c9e4d-102">ICorDebugExceptionDebugEvent::GetStackPointer メソッド</span><span class="sxs-lookup"><span data-stu-id="c9e4d-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="c9e4d-103">この例外デバッグ イベントのスタック ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="c9e4d-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9e4d-104">構文</span><span class="sxs-lookup"><span data-stu-id="c9e4d-104">Syntax</span></span>  
  
```  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9e4d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c9e4d-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="c9e4d-106">[out] この例外デバッグ イベントのスタック ポインターのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c9e4d-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="c9e4d-107">詳細については、次の「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9e4d-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9e4d-108">コメント</span><span class="sxs-lookup"><span data-stu-id="c9e4d-108">Remarks</span></span>  
 <span data-ttu-id="c9e4d-109">このスタック ポインターの意味は、次の表に示すように、イベントの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="c9e4d-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="c9e4d-110">イベントの種類</span><span class="sxs-lookup"><span data-stu-id="c9e4d-110">Event type</span></span>|<span data-ttu-id="c9e4d-111">`pStackPointer` 値の意味</span><span class="sxs-lookup"><span data-stu-id="c9e4d-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="c9e4d-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="c9e4d-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="c9e4d-113">例外をスローしたフレームのスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="c9e4d-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="c9e4d-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="c9e4d-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="c9e4d-115">スローされた例外の位置に最も近いユーザー コード フレームのスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="c9e4d-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="c9e4d-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="c9e4d-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="c9e4d-117">catch ハンドラーを含むフレームのスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="c9e4d-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="c9e4d-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="c9e4d-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="c9e4d-119">`pStackPointer` が **null** です。</span><span class="sxs-lookup"><span data-stu-id="c9e4d-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="c9e4d-120">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c9e4d-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="c9e4d-121">イベントの種類がから利用可能な[icordebugdebugevent::geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="c9e4d-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9e4d-122">要件</span><span class="sxs-lookup"><span data-stu-id="c9e4d-122">Requirements</span></span>  
 <span data-ttu-id="c9e4d-123">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c9e4d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9e4d-124">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c9e4d-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9e4d-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9e4d-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9e4d-126">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9e4d-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9e4d-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9e4d-127">See Also</span></span>  
 [<span data-ttu-id="c9e4d-128">ICorDebugExceptionDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c9e4d-128">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="c9e4d-129">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c9e4d-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

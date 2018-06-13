---
title: ICorDebugExceptionDebugEvent::GetStackPointer メソッド
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e724b3a928a23bb44c3d1005024f803b5974e6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415556"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="522fe-102">ICorDebugExceptionDebugEvent::GetStackPointer メソッド</span><span class="sxs-lookup"><span data-stu-id="522fe-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="522fe-103">この例外デバッグ イベントのスタック ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="522fe-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="522fe-104">構文</span><span class="sxs-lookup"><span data-stu-id="522fe-104">Syntax</span></span>  
  
```  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="522fe-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="522fe-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="522fe-106">[out] この例外デバッグ イベントのスタック ポインターのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="522fe-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="522fe-107">詳細については、次の「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="522fe-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="522fe-108">コメント</span><span class="sxs-lookup"><span data-stu-id="522fe-108">Remarks</span></span>  
 <span data-ttu-id="522fe-109">このスタック ポインターの意味は、次の表に示すように、イベントの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="522fe-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="522fe-110">イベントの種類</span><span class="sxs-lookup"><span data-stu-id="522fe-110">Event type</span></span>|<span data-ttu-id="522fe-111">`pStackPointer` 値の意味</span><span class="sxs-lookup"><span data-stu-id="522fe-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="522fe-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="522fe-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="522fe-113">例外をスローしたフレームのスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="522fe-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="522fe-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="522fe-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="522fe-115">スローされた例外の位置に最も近いユーザー コード フレームのスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="522fe-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="522fe-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="522fe-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="522fe-117">catch ハンドラーを含むフレームのスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="522fe-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="522fe-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="522fe-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="522fe-119">`pStackPointer` が **null** です。</span><span class="sxs-lookup"><span data-stu-id="522fe-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="522fe-120">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="522fe-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="522fe-121">イベントの種類がから利用可能な[icordebugdebugevent::geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="522fe-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="522fe-122">要件</span><span class="sxs-lookup"><span data-stu-id="522fe-122">Requirements</span></span>  
 <span data-ttu-id="522fe-123">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="522fe-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="522fe-124">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="522fe-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="522fe-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="522fe-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="522fe-126">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="522fe-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="522fe-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="522fe-127">See Also</span></span>  
 [<span data-ttu-id="522fe-128">ICorDebugExceptionDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="522fe-128">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="522fe-129">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="522fe-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

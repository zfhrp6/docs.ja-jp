---
title: ICorDebugExceptionDebugEvent インターフェイス
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cedbbf2067a94aa73e40bd4651fc97b72aa9afef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416303"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="3e491-102">ICorDebugExceptionDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3e491-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="3e491-103">拡張、 [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)例外イベントをサポートするインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="3e491-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3e491-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="3e491-104">Methods</span></span>  
  
|<span data-ttu-id="3e491-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="3e491-105">Method</span></span>|<span data-ttu-id="3e491-106">説明</span><span class="sxs-lookup"><span data-stu-id="3e491-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3e491-107">GetFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="3e491-107">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="3e491-108">例外をインターセプトできるかどうかを示すフラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="3e491-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="3e491-109">GetNativeIP メソッド</span><span class="sxs-lookup"><span data-stu-id="3e491-109">GetNativeIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="3e491-110">この例外デバッグ イベントのネイティブ インターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="3e491-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="3e491-111">GetStackPointer メソッド</span><span class="sxs-lookup"><span data-stu-id="3e491-111">GetStackPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="3e491-112">この例外デバッグ イベントのスタック ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="3e491-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e491-113">コメント</span><span class="sxs-lookup"><span data-stu-id="3e491-113">Remarks</span></span>  
 <span data-ttu-id="3e491-114">`ICorDebugExceptionDebugEvent` インターフェイスは、次のイベントの種類によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="3e491-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
-   [<span data-ttu-id="3e491-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="3e491-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="3e491-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="3e491-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="3e491-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="3e491-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="3e491-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="3e491-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
>  <span data-ttu-id="3e491-119">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="3e491-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="3e491-120">インターフェイス ポインターを取得するために `QueryInterface` を呼び出そうとすると、.NET ネイティブ外の ICorDebug シナリオに対して `E_NOINTERFACE` が返されます。</span><span class="sxs-lookup"><span data-stu-id="3e491-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e491-121">要件</span><span class="sxs-lookup"><span data-stu-id="3e491-121">Requirements</span></span>  
 <span data-ttu-id="3e491-122">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3e491-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e491-123">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e491-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e491-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e491-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e491-125">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e491-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e491-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e491-126">See Also</span></span>  
 [<span data-ttu-id="3e491-127">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3e491-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="3e491-128">デバッグ</span><span class="sxs-lookup"><span data-stu-id="3e491-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

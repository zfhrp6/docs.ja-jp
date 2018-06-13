---
title: ICorDebugDebugEvent インターフェイス
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a2543a9629c60fde2b2f14c11898ba3e9df3c82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419313"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="e6729-102">ICorDebugDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6729-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="e6729-103">すべての `ICorDebug` デバッグ イベントを派生させる基本インターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="e6729-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e6729-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="e6729-104">Methods</span></span>  
  
|<span data-ttu-id="e6729-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e6729-105">Method</span></span>|<span data-ttu-id="e6729-106">説明</span><span class="sxs-lookup"><span data-stu-id="e6729-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e6729-107">GetEventKind メソッド</span><span class="sxs-lookup"><span data-stu-id="e6729-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="e6729-108">この `ICorDebugDebugEvent` オブジェクトが表すイベントの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="e6729-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="e6729-109">GetThread メソッド</span><span class="sxs-lookup"><span data-stu-id="e6729-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="e6729-110">イベントが発生したスレッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="e6729-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6729-111">コメント</span><span class="sxs-lookup"><span data-stu-id="e6729-111">Remarks</span></span>  
 <span data-ttu-id="e6729-112">次のインターフェイスは、`ICorDebugDebugEvent` インターフェイスから派生したものです。</span><span class="sxs-lookup"><span data-stu-id="e6729-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
-   [<span data-ttu-id="e6729-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="e6729-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
-   [<span data-ttu-id="e6729-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="e6729-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="e6729-115">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="e6729-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="e6729-116">インターフェイス ポインターを取得するために `QueryInterface` を呼び出そうとすると、.NET ネイティブ外の ICorDebug シナリオに対して `E_NOINTERFACE` が返されます。</span><span class="sxs-lookup"><span data-stu-id="e6729-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6729-117">要件</span><span class="sxs-lookup"><span data-stu-id="e6729-117">Requirements</span></span>  
 <span data-ttu-id="e6729-118">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e6729-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6729-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e6729-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6729-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6729-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6729-121">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6729-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6729-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="e6729-122">See Also</span></span>  
 [<span data-ttu-id="e6729-123">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6729-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="e6729-124">デバッグ</span><span class="sxs-lookup"><span data-stu-id="e6729-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

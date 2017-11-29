---
title: "ICorDebugLoadedModule インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5cdc89ec81d76a3ce7d39a53e097745d6c9822f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="68994-102">ICorDebugLoadedModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="68994-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="68994-103">読み込まれたモジュールに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="68994-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="68994-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="68994-104">Methods</span></span>  
  
|<span data-ttu-id="68994-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="68994-105">Method</span></span>|<span data-ttu-id="68994-106">説明</span><span class="sxs-lookup"><span data-stu-id="68994-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="68994-107">GetBaseAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="68994-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="68994-108">読み込まれたモジュールのベース アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="68994-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="68994-109">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="68994-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="68994-110">読み込まれたモジュールの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="68994-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="68994-111">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="68994-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="68994-112">読み込まれたモジュールのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="68994-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68994-113">コメント</span><span class="sxs-lookup"><span data-stu-id="68994-113">Remarks</span></span>  
 <span data-ttu-id="68994-114">`ICorDebugLoadedModule` インターフェイスはデバッガーによって実装され、CLR デバッグ インターフェイスが、デバッガーから読み込まれたモジュールに関する情報を取得するために使用します。</span><span class="sxs-lookup"><span data-stu-id="68994-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68994-115">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="68994-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="68994-116">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="68994-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68994-117">要件</span><span class="sxs-lookup"><span data-stu-id="68994-117">Requirements</span></span>  
 <span data-ttu-id="68994-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="68994-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68994-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68994-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68994-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68994-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68994-121">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68994-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68994-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="68994-122">See Also</span></span>  
 [<span data-ttu-id="68994-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="68994-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="68994-124">デバッグ</span><span class="sxs-lookup"><span data-stu-id="68994-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

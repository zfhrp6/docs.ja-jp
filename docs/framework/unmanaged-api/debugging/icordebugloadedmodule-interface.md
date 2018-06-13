---
title: ICorDebugLoadedModule インターフェイス
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07d6dcc1873e24f84f97c877e8198c27eceef0c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420792"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="6e42b-102">ICorDebugLoadedModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6e42b-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="6e42b-103">読み込まれたモジュールに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="6e42b-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e42b-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="6e42b-104">Methods</span></span>  
  
|<span data-ttu-id="6e42b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="6e42b-105">Method</span></span>|<span data-ttu-id="6e42b-106">説明</span><span class="sxs-lookup"><span data-stu-id="6e42b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e42b-107">GetBaseAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="6e42b-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="6e42b-108">読み込まれたモジュールのベース アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="6e42b-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="6e42b-109">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="6e42b-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="6e42b-110">読み込まれたモジュールの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="6e42b-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="6e42b-111">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="6e42b-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="6e42b-112">読み込まれたモジュールのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="6e42b-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e42b-113">コメント</span><span class="sxs-lookup"><span data-stu-id="6e42b-113">Remarks</span></span>  
 <span data-ttu-id="6e42b-114">`ICorDebugLoadedModule` インターフェイスはデバッガーによって実装され、CLR デバッグ インターフェイスが、デバッガーから読み込まれたモジュールに関する情報を取得するために使用します。</span><span class="sxs-lookup"><span data-stu-id="6e42b-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e42b-115">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="6e42b-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="6e42b-116">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="6e42b-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e42b-117">要件</span><span class="sxs-lookup"><span data-stu-id="6e42b-117">Requirements</span></span>  
 <span data-ttu-id="6e42b-118">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6e42b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e42b-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e42b-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e42b-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e42b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e42b-121">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e42b-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e42b-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="6e42b-122">See Also</span></span>  
 [<span data-ttu-id="6e42b-123">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6e42b-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6e42b-124">デバッグ</span><span class="sxs-lookup"><span data-stu-id="6e42b-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

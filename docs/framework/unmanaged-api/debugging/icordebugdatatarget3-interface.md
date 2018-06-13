---
title: ICorDebugDataTarget3 インターフェイス
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6392d1040c9d76944f79dc3a39213ae6c2191bef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415569"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="d4d78-102">ICorDebugDataTarget3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d4d78-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="d4d78-103">論理的に拡張し、 [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)読み込まれたモジュールに関する情報を提供するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="d4d78-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="d4d78-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="d4d78-104">Method</span></span>  
  
|<span data-ttu-id="d4d78-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d4d78-105">Method</span></span>|<span data-ttu-id="d4d78-106">説明</span><span class="sxs-lookup"><span data-stu-id="d4d78-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d4d78-107">GetLoadedModules メソッド</span><span class="sxs-lookup"><span data-stu-id="d4d78-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="d4d78-108">これまでに読み込まれたモジュールの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="d4d78-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4d78-109">コメント</span><span class="sxs-lookup"><span data-stu-id="d4d78-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4d78-110">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="d4d78-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="d4d78-111">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="d4d78-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4d78-112">要件</span><span class="sxs-lookup"><span data-stu-id="d4d78-112">Requirements</span></span>  
 <span data-ttu-id="d4d78-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d4d78-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4d78-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4d78-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4d78-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4d78-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4d78-116">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4d78-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4d78-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4d78-117">See Also</span></span>  
 [<span data-ttu-id="d4d78-118">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d4d78-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="d4d78-119">デバッグ</span><span class="sxs-lookup"><span data-stu-id="d4d78-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

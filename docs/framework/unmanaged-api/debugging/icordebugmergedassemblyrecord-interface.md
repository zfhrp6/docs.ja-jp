---
title: ICorDebugMergedAssemblyRecord インターフェイス
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e135166b79bb130e271549228418881b0c7587c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419677"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="c4800-102">ICorDebugMergedAssemblyRecord インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c4800-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="c4800-103">マージされたアセンブリに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="c4800-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c4800-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="c4800-104">Methods</span></span>  
  
|<span data-ttu-id="c4800-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c4800-105">Method</span></span>|<span data-ttu-id="c4800-106">説明</span><span class="sxs-lookup"><span data-stu-id="c4800-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c4800-107">GetCulture メソッド</span><span class="sxs-lookup"><span data-stu-id="c4800-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="c4800-108">アセンブリのカルチャ名文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="c4800-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="c4800-109">GetIndex メソッド</span><span class="sxs-lookup"><span data-stu-id="c4800-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="c4800-110">アセンブリのプレフィックス インデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="c4800-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="c4800-111">GetPublicKey メソッド</span><span class="sxs-lookup"><span data-stu-id="c4800-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="c4800-112">アセンブリの公開キーを取得します。</span><span class="sxs-lookup"><span data-stu-id="c4800-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="c4800-113">GetPublicKeyToken メソッド</span><span class="sxs-lookup"><span data-stu-id="c4800-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="c4800-114">アセンブリの公開キー トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="c4800-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="c4800-115">GetSimpleName メソッド</span><span class="sxs-lookup"><span data-stu-id="c4800-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="c4800-116">アセンブリの簡易名を取得します。</span><span class="sxs-lookup"><span data-stu-id="c4800-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="c4800-117">GetVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="c4800-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="c4800-118">アセンブリのバージョン情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="c4800-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4800-119">コメント</span><span class="sxs-lookup"><span data-stu-id="c4800-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4800-120">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="c4800-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="c4800-121">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="c4800-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4800-122">要件</span><span class="sxs-lookup"><span data-stu-id="c4800-122">Requirements</span></span>  
 <span data-ttu-id="c4800-123">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c4800-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4800-124">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4800-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4800-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4800-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4800-126">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4800-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4800-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4800-127">See Also</span></span>  
 [<span data-ttu-id="c4800-128">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c4800-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="c4800-129">デバッグ</span><span class="sxs-lookup"><span data-stu-id="c4800-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

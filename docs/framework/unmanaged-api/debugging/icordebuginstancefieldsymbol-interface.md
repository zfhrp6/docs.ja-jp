---
title: ICorDebugInstanceFieldSymbol インターフェイス
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82f6ccd43059f33a69b8b052f9efa34c4e4f2c1e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="ac444-102">ICorDebugInstanceFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ac444-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="ac444-103">インスタンス フィールドのデバッグ シンボル情報を表します。</span><span class="sxs-lookup"><span data-stu-id="ac444-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ac444-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="ac444-104">Methods</span></span>  
  
|<span data-ttu-id="ac444-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ac444-105">Method</span></span>|<span data-ttu-id="ac444-106">説明</span><span class="sxs-lookup"><span data-stu-id="ac444-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ac444-107">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="ac444-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="ac444-108">インスタンス フィールドの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="ac444-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="ac444-109">GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="ac444-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="ac444-110">このインスタンス フィールドの親クラスにおける、このインスタンス フィールドのオフセット (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="ac444-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="ac444-111">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="ac444-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="ac444-112">インスタンス フィールドのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="ac444-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac444-113">コメント</span><span class="sxs-lookup"><span data-stu-id="ac444-113">Remarks</span></span>  
 <span data-ttu-id="ac444-114">`ICorDebugInstanceFieldSymbol` インターフェイスは、インスタンス フィールドのデバッグ シンボル情報を取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ac444-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac444-115">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="ac444-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="ac444-116">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="ac444-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac444-117">要件</span><span class="sxs-lookup"><span data-stu-id="ac444-117">Requirements</span></span>  
 <span data-ttu-id="ac444-118">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ac444-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac444-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac444-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac444-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac444-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac444-121">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac444-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac444-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac444-122">See Also</span></span>  
 [<span data-ttu-id="ac444-123">ICorDebugStaticFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ac444-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="ac444-124">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ac444-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="ac444-125">デバッグ</span><span class="sxs-lookup"><span data-stu-id="ac444-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

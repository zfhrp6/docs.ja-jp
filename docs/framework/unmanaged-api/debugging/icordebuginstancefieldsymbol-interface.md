---
title: "ICorDebugInstanceFieldSymbol インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fbf3f07f5669c4fcafa4d3cc4119fc715539651d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="dafe0-102">ICorDebugInstanceFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dafe0-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="dafe0-103">インスタンス フィールドのデバッグ シンボル情報を表します。</span><span class="sxs-lookup"><span data-stu-id="dafe0-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dafe0-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="dafe0-104">Methods</span></span>  
  
|<span data-ttu-id="dafe0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="dafe0-105">Method</span></span>|<span data-ttu-id="dafe0-106">説明</span><span class="sxs-lookup"><span data-stu-id="dafe0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dafe0-107">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="dafe0-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="dafe0-108">インスタンス フィールドの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="dafe0-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="dafe0-109">GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="dafe0-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="dafe0-110">このインスタンス フィールドの親クラスにおける、このインスタンス フィールドのオフセット (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="dafe0-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="dafe0-111">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="dafe0-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="dafe0-112">インスタンス フィールドのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="dafe0-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dafe0-113">コメント</span><span class="sxs-lookup"><span data-stu-id="dafe0-113">Remarks</span></span>  
 <span data-ttu-id="dafe0-114">`ICorDebugInstanceFieldSymbol` インターフェイスは、インスタンス フィールドのデバッグ シンボル情報を取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="dafe0-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dafe0-115">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="dafe0-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="dafe0-116">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="dafe0-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dafe0-117">要件</span><span class="sxs-lookup"><span data-stu-id="dafe0-117">Requirements</span></span>  
 <span data-ttu-id="dafe0-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dafe0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dafe0-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dafe0-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dafe0-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dafe0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dafe0-121">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dafe0-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dafe0-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="dafe0-122">See Also</span></span>  
 [<span data-ttu-id="dafe0-123">ICorDebugStaticFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dafe0-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="dafe0-124">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="dafe0-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="dafe0-125">デバッグ</span><span class="sxs-lookup"><span data-stu-id="dafe0-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

---
title: "ICorDebugGCReferenceEnum インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGCReferenceEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGCReferenceEnum
helpviewer_keywords: ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 89e516bba3d9dd8a13e1beb2bdc231b0a639dbf0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="bbdde-102">ICorDebugGCReferenceEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bbdde-102">ICorDebugGCReferenceEnum Interface</span></span>
<span data-ttu-id="bbdde-103">ガベージ コレクトされるオブジェクトの列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="bbdde-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bbdde-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="bbdde-104">Methods</span></span>  
  
|<span data-ttu-id="bbdde-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="bbdde-105">Method</span></span>|<span data-ttu-id="bbdde-106">説明</span><span class="sxs-lookup"><span data-stu-id="bbdde-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bbdde-107">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="bbdde-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="bbdde-108">指定した数を取得[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)ガベージ コレクトされるオブジェクトに関する情報が含まれているインスタンス。</span><span class="sxs-lookup"><span data-stu-id="bbdde-108">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbdde-109">コメント</span><span class="sxs-lookup"><span data-stu-id="bbdde-109">Remarks</span></span>  
 <span data-ttu-id="bbdde-110">`ICorDebugGCReferenceEnum`インターフェイスは、"ICorDebugEnum"インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="bbdde-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="bbdde-111">`ICorDebugGCReferenceEnum`インスタンスが格納されます[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)を呼び出してインスタンス、 [icordebugprocess 5::enumerategcreferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="bbdde-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="bbdde-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)を呼び出してオブジェクトを列挙することができます、 [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="bbdde-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="bbdde-113">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)このメソッドによって設定されます。 コレクション内のオブジェクトは、3 種類のオブジェクトを表します。</span><span class="sxs-lookup"><span data-stu-id="bbdde-113">The [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
-   <span data-ttu-id="bbdde-114">すべてのマネージ スタックからオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="bbdde-114">Objects from all managed stacks.</span></span> <span data-ttu-id="bbdde-115">これには、マネージ コードだけでなく、共通言語ランタイムによって作成されたオブジェクトのライブ参照が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bbdde-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
-   <span data-ttu-id="bbdde-116">オブジェクト ハンドル テーブルをします。</span><span class="sxs-lookup"><span data-stu-id="bbdde-116">Objects from the handle table.</span></span> <span data-ttu-id="bbdde-117">これには、強い参照が含まれます (`HNDTYPE_STRONG`と`HNDTYPE_REFCOUNT`) とモジュールの静的変数。</span><span class="sxs-lookup"><span data-stu-id="bbdde-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
-   <span data-ttu-id="bbdde-118">ファイナライザー キューからのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="bbdde-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="bbdde-119">ファイナライザー キューは、ファイナライザーが実行されるまで、オブジェクトをルートします。</span><span class="sxs-lookup"><span data-stu-id="bbdde-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbdde-120">要件</span><span class="sxs-lookup"><span data-stu-id="bbdde-120">Requirements</span></span>  
 <span data-ttu-id="bbdde-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bbdde-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbdde-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bbdde-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bbdde-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bbdde-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbdde-124">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbdde-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbdde-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="bbdde-125">See Also</span></span>  
 [<span data-ttu-id="bbdde-126">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="bbdde-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

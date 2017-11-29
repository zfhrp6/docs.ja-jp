---
title: "デバッグ構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0293a20f5f735dd38b1d167ebc5057f645fa011a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-structures"></a><span data-ttu-id="8b98a-102">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="8b98a-102">Debugging Structures</span></span>
<span data-ttu-id="8b98a-103">このセクションでは、デバッグ API が使用するアンマネージ構造体について説明します。</span><span class="sxs-lookup"><span data-stu-id="8b98a-103">This section describes the unmanaged structures that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b98a-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="8b98a-104">In This Section</span></span>  
 [<span data-ttu-id="8b98a-105">CLR_DEBUGGING_VERSION 構造体</span><span class="sxs-lookup"><span data-stu-id="8b98a-105">CLR_DEBUGGING_VERSION Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)  
 <span data-ttu-id="8b98a-106">デバッグのために共通言語ランタイム (CLR) の製品バージョンを定義します。</span><span class="sxs-lookup"><span data-stu-id="8b98a-106">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
 [<span data-ttu-id="8b98a-107">CodeChunkInfo Structure1</span><span class="sxs-lookup"><span data-stu-id="8b98a-107">CodeChunkInfo Structure1</span></span>](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)  
 <span data-ttu-id="8b98a-108">メモリ内のコードの単一のチャンクを表しています。</span><span class="sxs-lookup"><span data-stu-id="8b98a-108">Represents a single chunk of code in memory.</span></span>  
  
 [<span data-ttu-id="8b98a-109">CorDebugBlockingObject 構造体</span><span class="sxs-lookup"><span data-stu-id="8b98a-109">CorDebugBlockingObject Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)  
 <span data-ttu-id="8b98a-110">スレッドをブロックしているオブジェクトとスレッドがブロックされている理由を定義します。</span><span class="sxs-lookup"><span data-stu-id="8b98a-110">Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>  
  
 [<span data-ttu-id="8b98a-111">CorDebugEHClause 構造体</span><span class="sxs-lookup"><span data-stu-id="8b98a-111">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 <span data-ttu-id="8b98a-112">中間言語 (IL) の特定の部分の例外処理 (EH) 句を表しています。</span><span class="sxs-lookup"><span data-stu-id="8b98a-112">Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>  
  
 [<span data-ttu-id="8b98a-113">CorDebugExceptionObjectStackFrame 構造体</span><span class="sxs-lookup"><span data-stu-id="8b98a-113">CorDebugExceptionObjectStackFrame Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 <span data-ttu-id="8b98a-114">例外オブジェクトのスタック フレームの情報を表しています。</span><span class="sxs-lookup"><span data-stu-id="8b98a-114">Represents stack frame information from an exception object.</span></span>  
  
 [<span data-ttu-id="8b98a-115">CorDebugExceptionObjectStackFrame 構造体</span><span class="sxs-lookup"><span data-stu-id="8b98a-115">CorDebugExceptionObjectStackFrame Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 <span data-ttu-id="8b98a-116">マップ、[!INCLUDE[wrt](../../../../includes/wrt-md.md)]を対応する GUID [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8b98a-116">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) object.</span></span>  
  
 <span data-ttu-id="8b98a-117">COR_ACTIVE_FUNCTION</span><span class="sxs-lookup"><span data-stu-id="8b98a-117">COR_ACTIVE_FUNCTION</span></span>  
 <span data-ttu-id="8b98a-118">スレッドのフレームで現在アクティブな機能に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8b98a-118">Contains information about the functions that are currently active in a thread's frames.</span></span>  
  
 [<span data-ttu-id="8b98a-119">COR_ARRAY_LAYOUT 構造体</span><span class="sxs-lookup"><span data-stu-id="8b98a-119">COR_ARRAY_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)  
 <span data-ttu-id="8b98a-120">メモリ内の配列オブジェクトのレイアウトに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="8b98a-120">Provides information about the layout of an array object in memory.</span></span>  
  
 <span data-ttu-id="8b98a-121">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="8b98a-121">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
 <span data-ttu-id="8b98a-122">Microsoft intermediate language (MSIL) コードをネイティブ コードにマップするために使用するオフセットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8b98a-122">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
 <span data-ttu-id="8b98a-123">COR_DEBUG_STEP_RANGE</span><span class="sxs-lookup"><span data-stu-id="8b98a-123">COR_DEBUG_STEP_RANGE</span></span>  
 <span data-ttu-id="8b98a-124">コードの範囲に関するオフセット情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8b98a-124">Contains the offset information for a range of code.</span></span>  
  
 [<span data-ttu-id="8b98a-125">COR_FIELD 構造体</span><span class="sxs-lookup"><span data-stu-id="8b98a-125">COR_FIELD Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)  
 <span data-ttu-id="8b98a-126">オブジェクトのフィールドに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="8b98a-126">Provides information about a field in an object.</span></span>  
  
 [<span data-ttu-id="8b98a-127">COR_GC_REFERENCE 構造体</span><span class="sxs-lookup"><span data-stu-id="8b98a-127">COR_GC_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)  
 <span data-ttu-id="8b98a-128">ガベージ コレクトされるオブジェクトに関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8b98a-128">Contains information about an object that is to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="8b98a-129">COR_HEAPINFO 構造体</span><span class="sxs-lookup"><span data-stu-id="8b98a-129">COR_HEAPINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)  
 <span data-ttu-id="8b98a-130">列挙可能かどうかなど、ガベージ コレクション ヒープに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="8b98a-130">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
 [<span data-ttu-id="8b98a-131">COR_HEAPOBJECT 構造体</span><span class="sxs-lookup"><span data-stu-id="8b98a-131">COR_HEAPOBJECT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)  
 <span data-ttu-id="8b98a-132">マネージ ヒープ上のオブジェクトに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="8b98a-132">Provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="8b98a-133">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="8b98a-133">COR_IL_MAP</span></span>  
 <span data-ttu-id="8b98a-134">機能の相対オフセットでの変更を指定します。</span><span class="sxs-lookup"><span data-stu-id="8b98a-134">Specifies changes in the relative offset of a function.</span></span>  
  
 [<span data-ttu-id="8b98a-135">COR_SEGMENT 構造体</span><span class="sxs-lookup"><span data-stu-id="8b98a-135">COR_SEGMENT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)  
 <span data-ttu-id="8b98a-136">マネージ ヒープのメモリ領域に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8b98a-136">Contains information about a region of memory in the managed heap.</span></span>  
  
 [<span data-ttu-id="8b98a-137">COR_TYPEID 構造体</span><span class="sxs-lookup"><span data-stu-id="8b98a-137">COR_TYPEID Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)  
 <span data-ttu-id="8b98a-138">型識別子が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8b98a-138">Contains a type identifier.</span></span>  
  
 [<span data-ttu-id="8b98a-139">COR_TYPE_LAYOUT 構造体</span><span class="sxs-lookup"><span data-stu-id="8b98a-139">COR_TYPE_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 <span data-ttu-id="8b98a-140">メモリ内のオブジェクトのレイアウトに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="8b98a-140">Provides information about the layout of an object in memory.</span></span>  
  
 <span data-ttu-id="8b98a-141">COR_VERSION</span><span class="sxs-lookup"><span data-stu-id="8b98a-141">COR_VERSION</span></span>  
 <span data-ttu-id="8b98a-142">共通言語ランタイムの標準の 4 つの部分のバージョン番号を保存します。</span><span class="sxs-lookup"><span data-stu-id="8b98a-142">Stores the standard four-part version number of the common language runtime.</span></span>  
  
 [<span data-ttu-id="8b98a-143">StackTrace_SimpleContext 構造体</span><span class="sxs-lookup"><span data-stu-id="8b98a-143">StackTrace_SimpleContext Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)  
 <span data-ttu-id="8b98a-144">完全な `CONTEXT` 構造の代わりに使用できる単純なコンテキストを提供します。</span><span class="sxs-lookup"><span data-stu-id="8b98a-144">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8b98a-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b98a-145">Related Sections</span></span>  
 [<span data-ttu-id="8b98a-146">デバッグ コクラス</span><span class="sxs-lookup"><span data-stu-id="8b98a-146">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="8b98a-147">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8b98a-147">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="8b98a-148">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="8b98a-148">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="8b98a-149">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="8b98a-149">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="8b98a-150">デバッグ</span><span class="sxs-lookup"><span data-stu-id="8b98a-150">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

---
title: "COR_TYPEID 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_TYPEID
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_TYPEID
helpviewer_keywords: COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ca6c9b3b02314843a3eaf01d8cd4a9eac5513efa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cortypeid-structure"></a><span data-ttu-id="4ec5e-102">COR_TYPEID 構造体</span><span class="sxs-lookup"><span data-stu-id="4ec5e-102">COR_TYPEID Structure</span></span>
<span data-ttu-id="4ec5e-103">型識別子が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4ec5e-103">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ec5e-104">構文</span><span class="sxs-lookup"><span data-stu-id="4ec5e-104">Syntax</span></span>  
  
```  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="4ec5e-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="4ec5e-105">Members</span></span>  
  
|<span data-ttu-id="4ec5e-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="4ec5e-106">Member</span></span>|<span data-ttu-id="4ec5e-107">説明</span><span class="sxs-lookup"><span data-stu-id="4ec5e-107">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="4ec5e-108">最初のトークンです。</span><span class="sxs-lookup"><span data-stu-id="4ec5e-108">The first token.</span></span>|  
|`token2`|<span data-ttu-id="4ec5e-109">2 番目のトークンです。</span><span class="sxs-lookup"><span data-stu-id="4ec5e-109">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ec5e-110">コメント</span><span class="sxs-lookup"><span data-stu-id="4ec5e-110">Remarks</span></span>  
 <span data-ttu-id="4ec5e-111">`COR_TYPEID`構造体は、多数のオブジェクトをガベージ コレクションに関する情報を提供するデバッグ メソッドによって返されます。</span><span class="sxs-lookup"><span data-stu-id="4ec5e-111">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="4ec5e-112">これは、そのアイテムに関する追加情報を提供するその他のデバッグ方法の引数として渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="4ec5e-112">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="4ec5e-113">列挙することによってなど、 [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)オブジェクト、個々 が取得することができます[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)マネージ ヒープ上の個々 のオブジェクトを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="4ec5e-113">For example, by enumerating an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="4ec5e-114">パススルーすることができます、`COR_TYPEID`値から、`COR_HEAPOBJECT.type`フィールドを[icordebugprocess 5::gettypefortypeid](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)オブジェクトに関する型情報を提供する ICorDebugType オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="4ec5e-114">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="4ec5e-115">A`COR_TYPEID`オブジェクトは不透明にするためのものです。</span><span class="sxs-lookup"><span data-stu-id="4ec5e-115">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="4ec5e-116">その個々 のフィールドをアクセスまたは操作する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ec5e-116">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="4ec5e-117">として指定されている識別子としてのみ使用することは、`out`さらに、メソッドの呼び出しとそのには、パラメーターが追加情報を提供するその他のメソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="4ec5e-117">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ec5e-118">必要条件</span><span class="sxs-lookup"><span data-stu-id="4ec5e-118">Requirements</span></span>  
 <span data-ttu-id="4ec5e-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4ec5e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ec5e-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4ec5e-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ec5e-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ec5e-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ec5e-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ec5e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ec5e-123">参照</span><span class="sxs-lookup"><span data-stu-id="4ec5e-123">See Also</span></span>  
 [<span data-ttu-id="4ec5e-124">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="4ec5e-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="4ec5e-125">デバッグ</span><span class="sxs-lookup"><span data-stu-id="4ec5e-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

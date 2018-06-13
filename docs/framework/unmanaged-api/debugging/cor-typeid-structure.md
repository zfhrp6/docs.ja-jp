---
title: COR_TYPEID 構造体
ms.date: 03/30/2017
api_name:
- COR_TYPEID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPEID
helpviewer_keywords:
- COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d4e07fb3d0988838fde662f4bb7d4719cc2d50f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408341"
---
# <a name="cortypeid-structure"></a><span data-ttu-id="0929a-102">COR_TYPEID 構造体</span><span class="sxs-lookup"><span data-stu-id="0929a-102">COR_TYPEID Structure</span></span>
<span data-ttu-id="0929a-103">型識別子が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0929a-103">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0929a-104">構文</span><span class="sxs-lookup"><span data-stu-id="0929a-104">Syntax</span></span>  
  
```  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="0929a-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="0929a-105">Members</span></span>  
  
|<span data-ttu-id="0929a-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="0929a-106">Member</span></span>|<span data-ttu-id="0929a-107">説明</span><span class="sxs-lookup"><span data-stu-id="0929a-107">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="0929a-108">最初のトークンです。</span><span class="sxs-lookup"><span data-stu-id="0929a-108">The first token.</span></span>|  
|`token2`|<span data-ttu-id="0929a-109">2 番目のトークンです。</span><span class="sxs-lookup"><span data-stu-id="0929a-109">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0929a-110">コメント</span><span class="sxs-lookup"><span data-stu-id="0929a-110">Remarks</span></span>  
 <span data-ttu-id="0929a-111">`COR_TYPEID`構造体は、多数のオブジェクトをガベージ コレクションに関する情報を提供するデバッグ メソッドによって返されます。</span><span class="sxs-lookup"><span data-stu-id="0929a-111">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="0929a-112">これは、そのアイテムに関する追加情報を提供するその他のデバッグ方法の引数として渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="0929a-112">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="0929a-113">列挙することによってなど、 [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)オブジェクト、個々 が取得することができます[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)マネージ ヒープ上の個々 のオブジェクトを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0929a-113">For example, by enumerating an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="0929a-114">パススルーすることができます、`COR_TYPEID`値から、`COR_HEAPOBJECT.type`フィールドを[icordebugprocess 5::gettypefortypeid](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)オブジェクトに関する型情報を提供する ICorDebugType オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="0929a-114">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="0929a-115">A`COR_TYPEID`オブジェクトは不透明にするためのものです。</span><span class="sxs-lookup"><span data-stu-id="0929a-115">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="0929a-116">その個々 のフィールドをアクセスまたは操作する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0929a-116">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="0929a-117">として指定されている識別子としてのみ使用することは、`out`さらに、メソッドの呼び出しとそのには、パラメーターが追加情報を提供するその他のメソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="0929a-117">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0929a-118">要件</span><span class="sxs-lookup"><span data-stu-id="0929a-118">Requirements</span></span>  
 <span data-ttu-id="0929a-119">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0929a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0929a-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0929a-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0929a-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0929a-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0929a-122">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0929a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0929a-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="0929a-123">See Also</span></span>  
 [<span data-ttu-id="0929a-124">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="0929a-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="0929a-125">デバッグ</span><span class="sxs-lookup"><span data-stu-id="0929a-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

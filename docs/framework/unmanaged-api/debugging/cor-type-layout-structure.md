---
title: "COR_TYPE_LAYOUT 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_TYPE_LAYOUT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_TYPE_LAYOUT
helpviewer_keywords: COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fc23e33abf47d19792c25d36a62bf95a098ee7a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="cortypelayout-structure"></a><span data-ttu-id="c7954-102">COR_TYPE_LAYOUT 構造体</span><span class="sxs-lookup"><span data-stu-id="c7954-102">COR_TYPE_LAYOUT Structure</span></span>
<span data-ttu-id="c7954-103">メモリ内のオブジェクトのレイアウトに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="c7954-103">Provides information about the layout of an object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7954-104">構文</span><span class="sxs-lookup"><span data-stu-id="c7954-104">Syntax</span></span>  
  
```  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="c7954-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="c7954-105">Members</span></span>  
  
|<span data-ttu-id="c7954-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="c7954-106">Member</span></span>|<span data-ttu-id="c7954-107">説明</span><span class="sxs-lookup"><span data-stu-id="c7954-107">Description</span></span>|  
|------------|-----------------|  
|`parentID`|<span data-ttu-id="c7954-108">親の識別子は、この種類に入力します。</span><span class="sxs-lookup"><span data-stu-id="c7954-108">The identifier of the parent type to this type.</span></span> <span data-ttu-id="c7954-109">これは、NULL 型の id になります (token1 = 0、token2 = 0) に、型 id が対応している場合<xref:System.Object?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="c7954-109">This will be the NULL type id (token1= 0, token2 = 0) if the type id corresponds to <xref:System.Object?displayProperty=nameWithType>.</span></span>|  
|`objectSize`|<span data-ttu-id="c7954-110">この型のオブジェクトの基本サイズ。</span><span class="sxs-lookup"><span data-stu-id="c7954-110">The base size of an object of this type.</span></span> <span data-ttu-id="c7954-111">非可変サイズのオブジェクトの合計サイズです。</span><span class="sxs-lookup"><span data-stu-id="c7954-111">This is the total size for non-variable sized objects.</span></span>|  
|`numFields`|<span data-ttu-id="c7954-112">この型のオブジェクトに含まれるフィールドの数。</span><span class="sxs-lookup"><span data-stu-id="c7954-112">The number of fields included in objects of this type.</span></span>|  
|`boxOffset`|<span data-ttu-id="c7954-113">この型をボックス化する場合、先頭は、オブジェクトのフィールドのオフセット。</span><span class="sxs-lookup"><span data-stu-id="c7954-113">If this type is boxed, the beginning offset of an object's fields.</span></span> <span data-ttu-id="c7954-114">このフィールドは、プリミティブおよび構造体などの値の型に対してのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="c7954-114">This field is valid only for value types such as primitives and structures.</span></span>|  
|`type`|<span data-ttu-id="c7954-115">この型が所属する CorElementType です。</span><span class="sxs-lookup"><span data-stu-id="c7954-115">The CorElementType to which this type belongs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7954-116">コメント</span><span class="sxs-lookup"><span data-stu-id="c7954-116">Remarks</span></span>  
 <span data-ttu-id="c7954-117">場合`numFields`はゼロより大きく、呼び出すことができます、 [icordebugprocess 5::gettypefields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)メソッドをこの種類のフィールドに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="c7954-117">If `numFields` is greater than zero, you can call the [ICorDebugProcess5::GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) method to obtain information about the fields in this type.</span></span> <span data-ttu-id="c7954-118">場合`type`は`ELEMENT_TYPE_STRING`、 `ELEMENT_TYPE_ARRAY`、または`ELEMENT_TYPE_SZARRAY`、この型のオブジェクトのサイズは変数、および渡すことができます、 [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)に構造体、 [icordebugprocess 5::getarraylayout](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="c7954-118">If `type` is `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, or `ELEMENT_TYPE_SZARRAY`, the size of objects of this type is variable, and you can pass the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) structure to the [ICorDebugProcess5::GetArrayLayout](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7954-119">要件</span><span class="sxs-lookup"><span data-stu-id="c7954-119">Requirements</span></span>  
 <span data-ttu-id="c7954-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c7954-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7954-121">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7954-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7954-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7954-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7954-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7954-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7954-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7954-124">See Also</span></span>  
 [<span data-ttu-id="c7954-125">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="c7954-125">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="c7954-126">デバッグ</span><span class="sxs-lookup"><span data-stu-id="c7954-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
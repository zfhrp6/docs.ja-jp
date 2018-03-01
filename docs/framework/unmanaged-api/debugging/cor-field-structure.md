---
title: "COR_FIELD 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- COR_FIELD
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_FIELD
helpviewer_keywords:
- COR_FIELD structure [.NET Framework debugging]
ms.assetid: c0822423-a9df-4961-950d-50dcc152f863
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 09a96a22a653688540bcc2ea3a03d86e242c10f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corfield-structure"></a><span data-ttu-id="98287-102">COR_FIELD 構造体</span><span class="sxs-lookup"><span data-stu-id="98287-102">COR_FIELD Structure</span></span>
<span data-ttu-id="98287-103">オブジェクトのフィールドに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="98287-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98287-104">構文</span><span class="sxs-lookup"><span data-stu-id="98287-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="98287-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="98287-105">Members</span></span>  
  
|<span data-ttu-id="98287-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="98287-106">Member</span></span>|<span data-ttu-id="98287-107">説明</span><span class="sxs-lookup"><span data-stu-id="98287-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="98287-108">`mdFieldDef`フィールド情報を取得するために使用するトークン。</span><span class="sxs-lookup"><span data-stu-id="98287-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="98287-109">オブジェクトのフィールドのデータをバイト単位でのオフセット。</span><span class="sxs-lookup"><span data-stu-id="98287-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="98287-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)をこのフィールドの種類を識別する値。</span><span class="sxs-lookup"><span data-stu-id="98287-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="98287-111">フィールドの型を示す CorElementType 列挙型値。</span><span class="sxs-lookup"><span data-stu-id="98287-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98287-112">コメント</span><span class="sxs-lookup"><span data-stu-id="98287-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98287-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="98287-113">Requirements</span></span>  
 <span data-ttu-id="98287-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="98287-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98287-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98287-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98287-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98287-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98287-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98287-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98287-118">参照</span><span class="sxs-lookup"><span data-stu-id="98287-118">See Also</span></span>  
 [<span data-ttu-id="98287-119">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="98287-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="98287-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="98287-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

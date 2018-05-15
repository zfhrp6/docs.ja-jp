---
title: COR_FIELD 構造体
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0898936665b3b337f2fd4e4d53bcc9f6071469b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="corfield-structure"></a><span data-ttu-id="99865-102">COR_FIELD 構造体</span><span class="sxs-lookup"><span data-stu-id="99865-102">COR_FIELD Structure</span></span>
<span data-ttu-id="99865-103">オブジェクトのフィールドに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="99865-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99865-104">構文</span><span class="sxs-lookup"><span data-stu-id="99865-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="99865-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="99865-105">Members</span></span>  
  
|<span data-ttu-id="99865-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="99865-106">Member</span></span>|<span data-ttu-id="99865-107">説明</span><span class="sxs-lookup"><span data-stu-id="99865-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="99865-108">`mdFieldDef`フィールド情報を取得するために使用するトークン。</span><span class="sxs-lookup"><span data-stu-id="99865-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="99865-109">オブジェクトのフィールドのデータをバイト単位でのオフセット。</span><span class="sxs-lookup"><span data-stu-id="99865-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="99865-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)をこのフィールドの種類を識別する値。</span><span class="sxs-lookup"><span data-stu-id="99865-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="99865-111">フィールドの型を示す CorElementType 列挙型値。</span><span class="sxs-lookup"><span data-stu-id="99865-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99865-112">コメント</span><span class="sxs-lookup"><span data-stu-id="99865-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99865-113">要件</span><span class="sxs-lookup"><span data-stu-id="99865-113">Requirements</span></span>  
 <span data-ttu-id="99865-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="99865-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99865-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99865-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99865-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99865-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99865-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99865-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99865-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="99865-118">See Also</span></span>  
 [<span data-ttu-id="99865-119">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="99865-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="99865-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="99865-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

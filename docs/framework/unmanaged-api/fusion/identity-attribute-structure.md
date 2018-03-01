---
title: "IDENTITY_ATTRIBUTE 構造体"
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
- IDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE
helpviewer_keywords:
- IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2c0d09bf4c24f977a490f946cbc35b2b3f53dfc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="identityattribute-structure"></a><span data-ttu-id="7073b-102">IDENTITY_ATTRIBUTE 構造体</span><span class="sxs-lookup"><span data-stu-id="7073b-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="7073b-103">メタデータ属性について説明、 [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="7073b-103">Contains metadata attribute information about an [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7073b-104">構文</span><span class="sxs-lookup"><span data-stu-id="7073b-104">Syntax</span></span>  
  
```  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="7073b-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="7073b-105">Members</span></span>  
  
|<span data-ttu-id="7073b-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="7073b-106">Member</span></span>|<span data-ttu-id="7073b-107">説明</span><span class="sxs-lookup"><span data-stu-id="7073b-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="7073b-108">属性はで、名前空間を表す null で終わる文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="7073b-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="7073b-109">属性の名前を表す null で終わる文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="7073b-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="7073b-110">属性の値を表す null で終わる文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="7073b-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7073b-111">コメント</span><span class="sxs-lookup"><span data-stu-id="7073b-111">Remarks</span></span>  
 <span data-ttu-id="7073b-112">`IDENTITY_ATTRIBUTE`構造には、null で終わる文字列への 3 つのポインターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7073b-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="7073b-113">これら 3 つの文字列では、1 つの属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="7073b-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="7073b-114">インスタンス、`IDENTITY_ATTRIBUTE`構造体のインスタンスを関連付け、 [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)構造体。</span><span class="sxs-lookup"><span data-stu-id="7073b-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="7073b-115">`IDENTITY_ATTRIBUTE`実際の文字列と、対応する構造に含まれる`IDENTITY_ATTRIBUTE_BLOB`構造で表示されている 3 つの文字列にオフセットを一覧表示、`IDENTITY_ATTRIBUTE`構造体。</span><span class="sxs-lookup"><span data-stu-id="7073b-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7073b-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="7073b-116">Requirements</span></span>  
 <span data-ttu-id="7073b-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7073b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7073b-118">**ヘッダー:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="7073b-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="7073b-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7073b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7073b-120">参照</span><span class="sxs-lookup"><span data-stu-id="7073b-120">See Also</span></span>  
 [<span data-ttu-id="7073b-121">IDefinitionIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7073b-121">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 [<span data-ttu-id="7073b-122">IDENTITY_ATTRIBUTE_BLOB 構造体</span><span class="sxs-lookup"><span data-stu-id="7073b-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)  
 [<span data-ttu-id="7073b-123">Fusion 構造体</span><span class="sxs-lookup"><span data-stu-id="7073b-123">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)

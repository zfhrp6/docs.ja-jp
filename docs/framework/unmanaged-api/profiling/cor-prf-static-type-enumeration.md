---
title: "COR_PRF_STATIC_TYPE 列挙型"
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
- COR_PRF_STATIC_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_STATIC_TYPE
helpviewer_keywords:
- COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 76d43a620b64c771427cd30af770e70642dabe7a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corprfstatictype-enumeration"></a><span data-ttu-id="586f1-102">COR_PRF_STATIC_TYPE 列挙型</span><span class="sxs-lookup"><span data-stu-id="586f1-102">COR_PRF_STATIC_TYPE Enumeration</span></span>
<span data-ttu-id="586f1-103">フィールドが静的であるかどうかを示し、静的な場合は、フィールドに適用される静的なクオリティを示します。</span><span class="sxs-lookup"><span data-stu-id="586f1-103">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span> <span data-ttu-id="586f1-104">これらの値は、フィールドを複数持つことを示すために、ビットごとの OR 演算を使用して結合できます異なる静的品質。</span><span class="sxs-lookup"><span data-stu-id="586f1-104">These values can be combined using the bitwise OR operation to indicate that the field has multiple, different static qualities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="586f1-105">構文</span><span class="sxs-lookup"><span data-stu-id="586f1-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="586f1-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="586f1-106">Members</span></span>  
  
|<span data-ttu-id="586f1-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="586f1-107">Member</span></span>|<span data-ttu-id="586f1-108">説明</span><span class="sxs-lookup"><span data-stu-id="586f1-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|<span data-ttu-id="586f1-109">フィールドは静的ではありません。</span><span class="sxs-lookup"><span data-stu-id="586f1-109">The field is not static.</span></span>|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|<span data-ttu-id="586f1-110">フィールドは、アプリケーション ドメインの静的です。</span><span class="sxs-lookup"><span data-stu-id="586f1-110">The field is application domain-static.</span></span>|  
|`COR_PRF_FIELD_THREAD_STATIC`|<span data-ttu-id="586f1-111">フィールドは、スレッド内静的です。</span><span class="sxs-lookup"><span data-stu-id="586f1-111">The field is thread-static.</span></span>|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|<span data-ttu-id="586f1-112">このフィールドは、静的コンテキストです。</span><span class="sxs-lookup"><span data-stu-id="586f1-112">The field is context-static.</span></span>|  
|`COR_PRF_FIELD_RVA_STATIC`|<span data-ttu-id="586f1-113">このフィールドは相対仮想アドレス (RVA)-静的です。</span><span class="sxs-lookup"><span data-stu-id="586f1-113">The field is relative virtual address (RVA)-static.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="586f1-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="586f1-114">Requirements</span></span>  
 <span data-ttu-id="586f1-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="586f1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="586f1-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="586f1-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="586f1-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="586f1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="586f1-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="586f1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="586f1-119">参照</span><span class="sxs-lookup"><span data-stu-id="586f1-119">See Also</span></span>  
 [<span data-ttu-id="586f1-120">列挙型のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="586f1-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)

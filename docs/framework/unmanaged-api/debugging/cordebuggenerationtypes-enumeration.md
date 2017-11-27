---
title: "CorDebugGenerationTypes 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugGenerationTypes
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugGenerationTypes
helpviewer_keywords: CorDebugGenerationTypes enumeration [.NET Framework debugging]
ms.assetid: 9f25b64f-eedd-4ae5-8b0e-cfdfb9b6c5d8
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: adefc0de4ba09419660c214df75365c90ec2c66e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="6d9bc-102">CorDebugGenerationTypes 列挙型</span><span class="sxs-lookup"><span data-stu-id="6d9bc-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="6d9bc-103">マネージ ヒープ上のメモリ領域の生成を指定します。</span><span class="sxs-lookup"><span data-stu-id="6d9bc-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d9bc-104">構文</span><span class="sxs-lookup"><span data-stu-id="6d9bc-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="6d9bc-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="6d9bc-105">Members</span></span>  
  
|<span data-ttu-id="6d9bc-106">メンバー名</span><span class="sxs-lookup"><span data-stu-id="6d9bc-106">Member name</span></span>|<span data-ttu-id="6d9bc-107">説明</span><span class="sxs-lookup"><span data-stu-id="6d9bc-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="6d9bc-108">ジェネレーション 0。</span><span class="sxs-lookup"><span data-stu-id="6d9bc-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="6d9bc-109">ジェネレーション 1。</span><span class="sxs-lookup"><span data-stu-id="6d9bc-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="6d9bc-110">ジェネレーション 2。</span><span class="sxs-lookup"><span data-stu-id="6d9bc-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="6d9bc-111">大きなオブジェクト ヒープ。</span><span class="sxs-lookup"><span data-stu-id="6d9bc-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d9bc-112">コメント</span><span class="sxs-lookup"><span data-stu-id="6d9bc-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d9bc-113">要件</span><span class="sxs-lookup"><span data-stu-id="6d9bc-113">Requirements</span></span>  
 <span data-ttu-id="6d9bc-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6d9bc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d9bc-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d9bc-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d9bc-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d9bc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d9bc-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d9bc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d9bc-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d9bc-118">See Also</span></span>  
 [<span data-ttu-id="6d9bc-119">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="6d9bc-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

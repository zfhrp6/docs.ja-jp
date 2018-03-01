---
title: "CorDebugGCType 列挙型"
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
- CorDebugGCType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGCType
helpviewer_keywords:
- CorDebugGCType enumeration [.NET Framework debugging]
ms.assetid: 880ca92a-42d4-42a5-9b9c-c2848eb39c6a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2045c2edd129c2e4154d24b43d96f6ea8ad64cab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="b44dc-102">CorDebugGCType 列挙型</span><span class="sxs-lookup"><span data-stu-id="b44dc-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="b44dc-103">ガベージ コレクターがワークステーションまたはサーバーのどちらで実行されているかを示します。</span><span class="sxs-lookup"><span data-stu-id="b44dc-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b44dc-104">構文</span><span class="sxs-lookup"><span data-stu-id="b44dc-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b44dc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b44dc-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="b44dc-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b44dc-106">Members</span></span>  
  
|<span data-ttu-id="b44dc-107">メンバー名</span><span class="sxs-lookup"><span data-stu-id="b44dc-107">Member name</span></span>|<span data-ttu-id="b44dc-108">説明</span><span class="sxs-lookup"><span data-stu-id="b44dc-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="b44dc-109">ガベージ コレクターは、ワークステーション上で実行されています。</span><span class="sxs-lookup"><span data-stu-id="b44dc-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="b44dc-110">ガベージ コレクターは、サーバーで実行します。</span><span class="sxs-lookup"><span data-stu-id="b44dc-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b44dc-111">コメント</span><span class="sxs-lookup"><span data-stu-id="b44dc-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b44dc-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="b44dc-112">Requirements</span></span>  
 <span data-ttu-id="b44dc-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b44dc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b44dc-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b44dc-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b44dc-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b44dc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b44dc-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b44dc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b44dc-117">参照</span><span class="sxs-lookup"><span data-stu-id="b44dc-117">See Also</span></span>  
 [<span data-ttu-id="b44dc-118">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="b44dc-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

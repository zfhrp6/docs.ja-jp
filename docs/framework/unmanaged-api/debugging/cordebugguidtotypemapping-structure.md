---
title: "CorDebugGuidToTypeMapping 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: CorDebugGuidToTypeMapping
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugGuidToTypeMapping
helpviewer_keywords: CorDebugGuidToTypeMapping structure [.NET Framework debugging]
ms.assetid: 57dbccd9-b16d-4da3-ae25-7a2cf9adf679
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ecdadc96c0fb850fef13ba978fc97eef91dadd65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="8409f-102">CorDebugGuidToTypeMapping 構造体</span><span class="sxs-lookup"><span data-stu-id="8409f-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="8409f-103">マップ、[!INCLUDE[wrt](../../../../includes/wrt-md.md)]を対応する ICorDebugType オブジェクトの GUID。</span><span class="sxs-lookup"><span data-stu-id="8409f-103">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8409f-104">構文</span><span class="sxs-lookup"><span data-stu-id="8409f-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="8409f-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="8409f-105">Members</span></span>  
  
|<span data-ttu-id="8409f-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="8409f-106">Member</span></span>|<span data-ttu-id="8409f-107">説明</span><span class="sxs-lookup"><span data-stu-id="8409f-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="8409f-108">キャッシュされた GUID[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型です。</span><span class="sxs-lookup"><span data-stu-id="8409f-108">The GUID of the cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`pType`|<span data-ttu-id="8409f-109">キャッシュの種類に関する情報を提供する ICorDebugType オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8409f-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8409f-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="8409f-110">Requirements</span></span>  
 <span data-ttu-id="8409f-111">**プラットフォーム:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="8409f-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span></span>  
  
 <span data-ttu-id="8409f-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8409f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8409f-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8409f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8409f-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8409f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8409f-115">参照</span><span class="sxs-lookup"><span data-stu-id="8409f-115">See Also</span></span>  
 [<span data-ttu-id="8409f-116">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="8409f-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="8409f-117">デバッグ</span><span class="sxs-lookup"><span data-stu-id="8409f-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

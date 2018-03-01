---
title: "LogSwitchCallReason 列挙型"
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
- LogSwitchCallReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LogSwitchCallReason
helpviewer_keywords:
- LogSwitchCallReason enumeration [.NET Framework debugging]
ms.assetid: 5bbb8d1b-bbc4-47b0-b1b1-2d54cc0be291
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3dcd91001dfd823416b08ba49ba4ed12a2c4d058
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="89abb-102">LogSwitchCallReason 列挙型</span><span class="sxs-lookup"><span data-stu-id="89abb-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="89abb-103">デバッグとトレースの切り替えで実行された操作を示します。</span><span class="sxs-lookup"><span data-stu-id="89abb-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89abb-104">構文</span><span class="sxs-lookup"><span data-stu-id="89abb-104">Syntax</span></span>  
  
```  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="89abb-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="89abb-105">Members</span></span>  
  
|<span data-ttu-id="89abb-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="89abb-106">Member</span></span>|<span data-ttu-id="89abb-107">説明</span><span class="sxs-lookup"><span data-stu-id="89abb-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="89abb-108">デバッグとトレース スイッチが作成されました。</span><span class="sxs-lookup"><span data-stu-id="89abb-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="89abb-109">デバッグとトレースの切り替えが変更されました。</span><span class="sxs-lookup"><span data-stu-id="89abb-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="89abb-110">デバッグとトレース スイッチが削除されました。</span><span class="sxs-lookup"><span data-stu-id="89abb-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89abb-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="89abb-111">Requirements</span></span>  
 <span data-ttu-id="89abb-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="89abb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89abb-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89abb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89abb-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89abb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89abb-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89abb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89abb-116">参照</span><span class="sxs-lookup"><span data-stu-id="89abb-116">See Also</span></span>  
 [<span data-ttu-id="89abb-117">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="89abb-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

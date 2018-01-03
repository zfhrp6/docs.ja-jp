---
title: "CorDebugMDAFlags 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugMDAFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugMDAFlags
helpviewer_keywords: CorDebugMDAFlags enumeration [.NET Framework debugging]
ms.assetid: 7c0c92fe-8bd2-477f-b307-aca0143732ca
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: defd2572d6f925cf557539983308b3b3e900eebd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="748a6-102">CorDebugMDAFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="748a6-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="748a6-103">マネージ デバッグ アシスタント (MDA) が生成されるスレッドのステータスを指定します。</span><span class="sxs-lookup"><span data-stu-id="748a6-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="748a6-104">構文</span><span class="sxs-lookup"><span data-stu-id="748a6-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="748a6-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="748a6-105">Members</span></span>  
  
|<span data-ttu-id="748a6-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="748a6-106">Member</span></span>|<span data-ttu-id="748a6-107">説明</span><span class="sxs-lookup"><span data-stu-id="748a6-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="748a6-108">MDA が起動されたので、MDA が起動されたスレッドが変更されました。</span><span class="sxs-lookup"><span data-stu-id="748a6-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="748a6-109">コメント</span><span class="sxs-lookup"><span data-stu-id="748a6-109">Remarks</span></span>  
 <span data-ttu-id="748a6-110">呼び出し履歴では、この MDA を発生した記述されていない、ときに、スレッドが持つと見なされます*スリップ*です。</span><span class="sxs-lookup"><span data-stu-id="748a6-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="748a6-111">これは、異常終了時に無効な操作のスレッドの実行によってもたらさです。</span><span class="sxs-lookup"><span data-stu-id="748a6-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="748a6-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="748a6-112">Requirements</span></span>  
 <span data-ttu-id="748a6-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="748a6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="748a6-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="748a6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="748a6-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="748a6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="748a6-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="748a6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="748a6-117">参照</span><span class="sxs-lookup"><span data-stu-id="748a6-117">See Also</span></span>  
 [<span data-ttu-id="748a6-118">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="748a6-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

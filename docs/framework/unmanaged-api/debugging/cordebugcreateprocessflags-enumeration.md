---
title: "CorDebugCreateProcessFlags 列挙型"
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
- CorDebugCreateProcessFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugCreateProcessFlags
helpviewer_keywords:
- CorDebugCreateProcessFlags enumeration [.NET Framework debugging]
ms.assetid: e709acce-6a17-4346-b38a-467dba567358
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9e35aa2656a1e950cead94480eb06cde96e4c811
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="caa7b-102">CorDebugCreateProcessFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="caa7b-102">CorDebugCreateProcessFlags Enumeration</span></span>
<span data-ttu-id="caa7b-103">呼び出しで使用できる追加のデバッグ オプションを提供、 [icordebug::createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="caa7b-103">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caa7b-104">構文</span><span class="sxs-lookup"><span data-stu-id="caa7b-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="caa7b-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="caa7b-105">Members</span></span>  
  
|<span data-ttu-id="caa7b-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="caa7b-106">Member</span></span>|<span data-ttu-id="caa7b-107">説明</span><span class="sxs-lookup"><span data-stu-id="caa7b-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="caa7b-108">特殊なオプションが設定されていません。</span><span class="sxs-lookup"><span data-stu-id="caa7b-108">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="caa7b-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="caa7b-109">Requirements</span></span>  
 <span data-ttu-id="caa7b-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="caa7b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caa7b-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="caa7b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="caa7b-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="caa7b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="caa7b-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caa7b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caa7b-114">参照</span><span class="sxs-lookup"><span data-stu-id="caa7b-114">See Also</span></span>  
 [<span data-ttu-id="caa7b-115">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="caa7b-115">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

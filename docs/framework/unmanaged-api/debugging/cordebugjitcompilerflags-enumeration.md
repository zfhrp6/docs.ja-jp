---
title: "CorDebugJITCompilerFlags 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugJITCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugJITCompilerFlags
helpviewer_keywords: CorDebugJITCompilerFlags enumeration [.NET Framework debugging]
ms.assetid: c0774f70-5bed-45e8-9922-fdad778c4c33
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d7eb8421dcd68c67536e0de038f7038500556c47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="cd126-102">CorDebugJITCompilerFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="cd126-102">CorDebugJITCompilerFlags Enumeration</span></span>
<span data-ttu-id="cd126-103">マネージ Just-In-Time (JIT) コンパイラの動作に影響を与える値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="cd126-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd126-104">構文</span><span class="sxs-lookup"><span data-stu-id="cd126-104">Syntax</span></span>  
  
```  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="cd126-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="cd126-105">Members</span></span>  
  
|<span data-ttu-id="cd126-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="cd126-106">Member</span></span>|<span data-ttu-id="cd126-107">説明</span><span class="sxs-lookup"><span data-stu-id="cd126-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="cd126-108">コンパイラがコンパイル データを追跡し、により、最適化を指定します。</span><span class="sxs-lookup"><span data-stu-id="cd126-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="cd126-109">コンパイラが最適化の無効になりますが、コンパイルのデータを追跡する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd126-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="cd126-110">コンパイラ追跡コンパイル データの最適化を無効にしをエディット コンティニュのテクノロジを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd126-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd126-111">要件</span><span class="sxs-lookup"><span data-stu-id="cd126-111">Requirements</span></span>  
 <span data-ttu-id="cd126-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cd126-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd126-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd126-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd126-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd126-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd126-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd126-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd126-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd126-116">See Also</span></span>  
 [<span data-ttu-id="cd126-117">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="cd126-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

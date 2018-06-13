---
title: CorDebugJITCompilerFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlags
helpviewer_keywords:
- CorDebugJITCompilerFlags enumeration [.NET Framework debugging]
ms.assetid: c0774f70-5bed-45e8-9922-fdad778c4c33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5835da6ee20673c2662f1166d304a45ca3e9daeb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405321"
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="cadec-102">CorDebugJITCompilerFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="cadec-102">CorDebugJITCompilerFlags Enumeration</span></span>
<span data-ttu-id="cadec-103">マネージ Just-In-Time (JIT) コンパイラの動作に影響を与える値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="cadec-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cadec-104">構文</span><span class="sxs-lookup"><span data-stu-id="cadec-104">Syntax</span></span>  
  
```  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="cadec-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="cadec-105">Members</span></span>  
  
|<span data-ttu-id="cadec-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="cadec-106">Member</span></span>|<span data-ttu-id="cadec-107">説明</span><span class="sxs-lookup"><span data-stu-id="cadec-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="cadec-108">コンパイラがコンパイル データを追跡し、により、最適化を指定します。</span><span class="sxs-lookup"><span data-stu-id="cadec-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="cadec-109">コンパイラが最適化の無効になりますが、コンパイルのデータを追跡する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="cadec-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="cadec-110">コンパイラ追跡コンパイル データの最適化を無効にしをエディット コンティニュのテクノロジを指定します。</span><span class="sxs-lookup"><span data-stu-id="cadec-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cadec-111">要件</span><span class="sxs-lookup"><span data-stu-id="cadec-111">Requirements</span></span>  
 <span data-ttu-id="cadec-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cadec-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cadec-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cadec-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cadec-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cadec-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cadec-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cadec-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cadec-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="cadec-116">See Also</span></span>  
 [<span data-ttu-id="cadec-117">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="cadec-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

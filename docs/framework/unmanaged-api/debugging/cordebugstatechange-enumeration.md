---
title: CorDebugStateChange 列挙体
ms.date: 03/30/2017
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 841108457293e3377ee87f9c7d7c6898340e51b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404347"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="8ce45-102">CorDebugStateChange 列挙体</span><span class="sxs-lookup"><span data-stu-id="8ce45-102">CorDebugStateChange Enumeration</span></span>
<span data-ttu-id="8ce45-103">プロセスへの変更に基づいて破棄が必要となった、キャッシュされたデータの量を示します。</span><span class="sxs-lookup"><span data-stu-id="8ce45-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ce45-104">構文</span><span class="sxs-lookup"><span data-stu-id="8ce45-104">Syntax</span></span>  
  
```  
typedef enum CorDebugStateChange  
{  
    PROCESS_RUNNING = 0x0000001,   
    FLUSH_ALL       = 0x0000002,   
} CorDebugStateChange;  
```  
  
## <a name="members"></a><span data-ttu-id="8ce45-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="8ce45-105">Members</span></span>  
  
|<span data-ttu-id="8ce45-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="8ce45-106">Member</span></span>|<span data-ttu-id="8ce45-107">説明</span><span class="sxs-lookup"><span data-stu-id="8ce45-107">Description</span></span>|  
|------------|-----------------|  
|`PROCESS_RUNNING`|<span data-ttu-id="8ce45-108">プロセスはフォワード実行によって新しいメモリ状態に達しています。</span><span class="sxs-lookup"><span data-stu-id="8ce45-108">The process reached a new memory state via forward execution.</span></span>|  
|`SET_CONTEXT_FLAG_UNWIND_FRAME`|<span data-ttu-id="8ce45-109">プロセスのメモリは、以前とは異なる状態になっている場合があります。</span><span class="sxs-lookup"><span data-stu-id="8ce45-109">The process' memory may be arbitrarily different than it was previously.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ce45-110">コメント</span><span class="sxs-lookup"><span data-stu-id="8ce45-110">Remarks</span></span>  
 <span data-ttu-id="8ce45-111">メンバー、`CorDebugStateChange`列挙体は、デバッガーが、引数として指定される、 [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)メソッド</span><span class="sxs-lookup"><span data-stu-id="8ce45-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) method</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ce45-112">この列挙体は .NET ネイティブのデバッグ シナリオのみで使用することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="8ce45-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ce45-113">要件</span><span class="sxs-lookup"><span data-stu-id="8ce45-113">Requirements</span></span>  
 <span data-ttu-id="8ce45-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8ce45-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ce45-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ce45-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ce45-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ce45-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ce45-117">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ce45-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ce45-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ce45-118">See Also</span></span>  
 [<span data-ttu-id="8ce45-119">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="8ce45-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="8ce45-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="8ce45-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

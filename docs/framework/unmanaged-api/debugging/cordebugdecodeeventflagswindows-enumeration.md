---
title: "CorDebugDecodeEventFlagsWindows 列挙体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugDecodeEventFlagsWindows
api_location: mscordbi.dll
api_type: COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cbbc275fd87ab9059959c2b770060ae1e11daa9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="b3d34-102">CorDebugDecodeEventFlagsWindows 列挙体</span><span class="sxs-lookup"><span data-stu-id="b3d34-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="b3d34-103">Windows プラットフォームのデバッグ イベントに関する追加情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="b3d34-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3d34-104">構文</span><span class="sxs-lookup"><span data-stu-id="b3d34-104">Syntax</span></span>  
  
```  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="b3d34-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="b3d34-105">Members</span></span>  
  
|<span data-ttu-id="b3d34-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b3d34-106">Member</span></span>|<span data-ttu-id="b3d34-107">説明</span><span class="sxs-lookup"><span data-stu-id="b3d34-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="b3d34-108">デバッグ イベントが初回例外であることを示します。</span><span class="sxs-lookup"><span data-stu-id="b3d34-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3d34-109">コメント</span><span class="sxs-lookup"><span data-stu-id="b3d34-109">Remarks</span></span>  
 <span data-ttu-id="b3d34-110">[Icordebugprocess 6::decodeevent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)メソッドが含まれています、`dwFlags`パラメーター デバッグ イベントに関する追加情報を提供する値を持つターゲット アーキテクチャに依存します。</span><span class="sxs-lookup"><span data-stu-id="b3d34-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="b3d34-111">`CorDebugDecodeEventFlagsWindows` 列挙体は、Windows プラットフォームでデバッグ イベントと共に使用できます。</span><span class="sxs-lookup"><span data-stu-id="b3d34-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3d34-112">この列挙体は .NET ネイティブのデバッグ シナリオのみで使用することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="b3d34-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3d34-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="b3d34-113">Requirements</span></span>  
 <span data-ttu-id="b3d34-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b3d34-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3d34-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3d34-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3d34-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3d34-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3d34-117">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3d34-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3d34-118">参照</span><span class="sxs-lookup"><span data-stu-id="b3d34-118">See Also</span></span>  
 [<span data-ttu-id="b3d34-119">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="b3d34-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

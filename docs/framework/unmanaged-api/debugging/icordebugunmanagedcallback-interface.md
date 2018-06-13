---
title: ICorDebugUnmanagedCallback インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback
helpviewer_keywords:
- ICorDebugUnmanagedCallback interface [.NET Framework debugging]
ms.assetid: bc71cbca-7d73-40e5-84dd-2109fade3c2a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b55b27d45ef3efea10215c8a4163b5981f9d145
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422860"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="e95c0-102">ICorDebugUnmanagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e95c0-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="e95c0-103">共通言語ランタイム (CLR) に直接関連付けられていないネイティブ イベントについて通知を提供します。</span><span class="sxs-lookup"><span data-stu-id="e95c0-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e95c0-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="e95c0-104">Methods</span></span>  
  
|<span data-ttu-id="e95c0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e95c0-105">Method</span></span>|<span data-ttu-id="e95c0-106">説明</span><span class="sxs-lookup"><span data-stu-id="e95c0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e95c0-107">DebugEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="e95c0-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="e95c0-108">ネイティブ イベントが発生したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e95c0-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e95c0-109">コメント</span><span class="sxs-lookup"><span data-stu-id="e95c0-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e95c0-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e95c0-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e95c0-111">要件</span><span class="sxs-lookup"><span data-stu-id="e95c0-111">Requirements</span></span>  
 <span data-ttu-id="e95c0-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e95c0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e95c0-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e95c0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e95c0-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e95c0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e95c0-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e95c0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e95c0-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e95c0-116">See Also</span></span>  
 [<span data-ttu-id="e95c0-117">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e95c0-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

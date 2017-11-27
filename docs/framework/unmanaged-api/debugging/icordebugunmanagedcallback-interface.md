---
title: "ICorDebugUnmanagedCallback インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugUnmanagedCallback
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugUnmanagedCallback
helpviewer_keywords: ICorDebugUnmanagedCallback interface [.NET Framework debugging]
ms.assetid: bc71cbca-7d73-40e5-84dd-2109fade3c2a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aa104bee5171b3b28731cf18a4d26e32f49169ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="3328a-102">ICorDebugUnmanagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3328a-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="3328a-103">共通言語ランタイム (CLR) に直接関連付けられていないネイティブ イベントについて通知を提供します。</span><span class="sxs-lookup"><span data-stu-id="3328a-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3328a-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="3328a-104">Methods</span></span>  
  
|<span data-ttu-id="3328a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="3328a-105">Method</span></span>|<span data-ttu-id="3328a-106">説明</span><span class="sxs-lookup"><span data-stu-id="3328a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3328a-107">DebugEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="3328a-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="3328a-108">ネイティブ イベントが発生したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="3328a-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3328a-109">コメント</span><span class="sxs-lookup"><span data-stu-id="3328a-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3328a-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="3328a-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3328a-111">要件</span><span class="sxs-lookup"><span data-stu-id="3328a-111">Requirements</span></span>  
 <span data-ttu-id="3328a-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3328a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3328a-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3328a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3328a-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3328a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3328a-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3328a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3328a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="3328a-116">See Also</span></span>  
 [<span data-ttu-id="3328a-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3328a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

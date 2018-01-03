---
title: "ICorDebugMDA インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMDA
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMDA
helpviewer_keywords: ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9c53e03acddc5d732a684cf825bce49a65bb4c31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="804eb-102">ICorDebugMDA インターフェイス</span><span class="sxs-lookup"><span data-stu-id="804eb-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="804eb-103">マネージ デバッグ アシスタント (MDA) メッセージを表します。</span><span class="sxs-lookup"><span data-stu-id="804eb-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="804eb-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="804eb-104">Methods</span></span>  
  
|<span data-ttu-id="804eb-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="804eb-105">Method</span></span>|<span data-ttu-id="804eb-106">説明</span><span class="sxs-lookup"><span data-stu-id="804eb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="804eb-107">GetDescription メソッド</span><span class="sxs-lookup"><span data-stu-id="804eb-107">GetDescription Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|<span data-ttu-id="804eb-108">この MDA の説明を含む文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="804eb-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="804eb-109">GetFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="804eb-109">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|<span data-ttu-id="804eb-110">この MDA に関連付けられているフラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="804eb-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="804eb-111">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="804eb-111">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|<span data-ttu-id="804eb-112">この MDA の名前を含む文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="804eb-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="804eb-113">GetOSThreadId メソッド</span><span class="sxs-lookup"><span data-stu-id="804eb-113">GetOSThreadId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|<span data-ttu-id="804eb-114">この MDA を実行して基になるオペレーティング システムのスレッド識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="804eb-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="804eb-115">GetXML メソッド</span><span class="sxs-lookup"><span data-stu-id="804eb-115">GetXML Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|<span data-ttu-id="804eb-116">この MDA に関連付けられている満杯になった XML ストリームを取得します。</span><span class="sxs-lookup"><span data-stu-id="804eb-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="804eb-117">コメント</span><span class="sxs-lookup"><span data-stu-id="804eb-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="804eb-118">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="804eb-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="804eb-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="804eb-119">Requirements</span></span>  
 <span data-ttu-id="804eb-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="804eb-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="804eb-121">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="804eb-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="804eb-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="804eb-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="804eb-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="804eb-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="804eb-124">参照</span><span class="sxs-lookup"><span data-stu-id="804eb-124">See Also</span></span>  
 [<span data-ttu-id="804eb-125">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="804eb-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="804eb-126">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="804eb-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

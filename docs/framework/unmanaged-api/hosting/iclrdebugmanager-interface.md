---
title: ICLRDebugManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRDebugManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager
helpviewer_keywords:
- ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d123177bf9f1b5eee1a2ba4d9b7f2042ddc07aa2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434940"
---
# <a name="iclrdebugmanager-interface"></a><span data-ttu-id="69c14-102">ICLRDebugManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="69c14-102">ICLRDebugManager Interface</span></span>
<span data-ttu-id="69c14-103">識別子と表示名に一連のタスクを関連付けるホストをできるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="69c14-103">Provides methods that allow a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="69c14-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="69c14-104">Methods</span></span>  
  
|<span data-ttu-id="69c14-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="69c14-105">Method</span></span>|<span data-ttu-id="69c14-106">説明</span><span class="sxs-lookup"><span data-stu-id="69c14-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="69c14-107">BeginConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="69c14-107">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|<span data-ttu-id="69c14-108">識別子とフレンドリ名を持つタスクを関連付けるには、ホストとデバッガーの間の新しい接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="69c14-108">Establishes a new connection between the host and the debugger to associate tasks with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="69c14-109">EndConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="69c14-109">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|<span data-ttu-id="69c14-110">タスクの一覧、識別子、およびフレンドリ名の間の関連付けを削除します。</span><span class="sxs-lookup"><span data-stu-id="69c14-110">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="69c14-111">GetDacl メソッド</span><span class="sxs-lookup"><span data-stu-id="69c14-111">GetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|<span data-ttu-id="69c14-112">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="69c14-112">This method is not implemented.</span></span>|  
|[<span data-ttu-id="69c14-113">IsDebuggerAttached メソッド</span><span class="sxs-lookup"><span data-stu-id="69c14-113">IsDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|<span data-ttu-id="69c14-114">デバッガーがプロセスにアタッチされているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="69c14-114">Gets a value that indicates whether a debugger is attached to the process.</span></span>|  
|[<span data-ttu-id="69c14-115">SetConnectionTasks メソッド</span><span class="sxs-lookup"><span data-stu-id="69c14-115">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|<span data-ttu-id="69c14-116">リストを関連付けます[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)インスタンス識別子とフレンドリ名を使用します。</span><span class="sxs-lookup"><span data-stu-id="69c14-116">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="69c14-117">SetDacl メソッド</span><span class="sxs-lookup"><span data-stu-id="69c14-117">SetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|<span data-ttu-id="69c14-118">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="69c14-118">This method is not implemented.</span></span>|  
|[<span data-ttu-id="69c14-119">SetSymbolReadingPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="69c14-119">SetSymbolReadingPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|<span data-ttu-id="69c14-120">プログラム データベース (PDB) ファイルを読み取るためのポリシーを設定します。</span><span class="sxs-lookup"><span data-stu-id="69c14-120">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="69c14-121">ポリシーは、呼び出し履歴に行番号およびファイルに関する情報が含まれているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="69c14-121">The policy determines whether information about line numbers and files is included in call stacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69c14-122">コメント</span><span class="sxs-lookup"><span data-stu-id="69c14-122">Remarks</span></span>  
 <span data-ttu-id="69c14-123">デバッグする場合、ホストは、独自のプログラミング ロジックに従ってタスクをグループ化をする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="69c14-123">In debugging scenarios, a host might want to group tasks according to its own programming logic.</span></span> <span data-ttu-id="69c14-124">たとえば、グループ化では、開発者は、プロセスで実行されているすべてのタスクを表示せず、開発者の Api で必要なタスクのみが表示とできます。</span><span class="sxs-lookup"><span data-stu-id="69c14-124">For example, a grouping would allow a developer to see only the tasks required by the developer's APIs, instead of seeing every task running in the process.</span></span> <span data-ttu-id="69c14-125">`ICLRDebugManager` このようなグループ化を実装をホストできるようにします。</span><span class="sxs-lookup"><span data-stu-id="69c14-125">`ICLRDebugManager` allows the host to implement this kind of grouping.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="69c14-126">次の 3 つ`ICLRDebugManager`メソッド、 `BeginConnection`、`SetConnectionTasks`と`EndConnection`、互いに依存します。</span><span class="sxs-lookup"><span data-stu-id="69c14-126">Three `ICLRDebugManager` methods, `BeginConnection`, `SetConnectionTasks` and `EndConnection`, are dependent upon each other.</span></span> <span data-ttu-id="69c14-127">期待どおりに動作するように指定された順序で呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="69c14-127">They must be called in the given order to work as expected.</span></span>  
  
 <span data-ttu-id="69c14-128">グループ化識別子とホストは、グループに割り当てます。 フレンドリ名なしの意味を持ちます共通言語ランタイム (CLR)。</span><span class="sxs-lookup"><span data-stu-id="69c14-128">The grouping, and the identifiers and friendly names that the host assigns to the grouping, have no meaning for the common language runtime (CLR).</span></span> <span data-ttu-id="69c14-129">CLR は、デバッガーに情報を渡すだけです。</span><span class="sxs-lookup"><span data-stu-id="69c14-129">The CLR merely passes the information along to the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69c14-130">要件</span><span class="sxs-lookup"><span data-stu-id="69c14-130">Requirements</span></span>  
 <span data-ttu-id="69c14-131">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="69c14-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69c14-132">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="69c14-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="69c14-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="69c14-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="69c14-134">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69c14-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69c14-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="69c14-135">See Also</span></span>  
 [<span data-ttu-id="69c14-136">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="69c14-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

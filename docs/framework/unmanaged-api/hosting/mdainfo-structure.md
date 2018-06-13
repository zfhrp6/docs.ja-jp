---
title: MDAInfo 構造体
ms.date: 03/30/2017
api_name:
- MDAInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MDAInfo
helpviewer_keywords:
- MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5164e85ecc97de99dcc493c2ba5efa8fc3468471
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443181"
---
# <a name="mdainfo-structure"></a><span data-ttu-id="3a219-102">MDAInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="3a219-102">MDAInfo Structure</span></span>
<span data-ttu-id="3a219-103">詳細について説明、`Event_MDAFired`マネージ デバッグ アシスタント (MDA) の作成をトリガーするイベントです。</span><span class="sxs-lookup"><span data-stu-id="3a219-103">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a219-104">構文</span><span class="sxs-lookup"><span data-stu-id="3a219-104">Syntax</span></span>  
  
```  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="3a219-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="3a219-105">Members</span></span>  
  
|<span data-ttu-id="3a219-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="3a219-106">Member</span></span>|<span data-ttu-id="3a219-107">説明</span><span class="sxs-lookup"><span data-stu-id="3a219-107">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="3a219-108">現在の MDA のタイトル。</span><span class="sxs-lookup"><span data-stu-id="3a219-108">The title of the current MDA.</span></span> <span data-ttu-id="3a219-109">タイトルを引き起こしたエラーの種類を記述する、`Event_MDAFired`イベント。</span><span class="sxs-lookup"><span data-stu-id="3a219-109">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="3a219-110">現在の MDA によって提供される出力メッセージです。</span><span class="sxs-lookup"><span data-stu-id="3a219-110">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a219-111">コメント</span><span class="sxs-lookup"><span data-stu-id="3a219-111">Remarks</span></span>  
 <span data-ttu-id="3a219-112">マネージ デバッグ アシスタント (Mda) がデバッグでランタイム実行エンジンは、共通言語ランタイム (CLR) で無効な条件を識別するなどのタスクを実行すると連携して動作する支援またはの状態に関する追加情報をダンプしますエンジン。</span><span class="sxs-lookup"><span data-stu-id="3a219-112">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="3a219-113">Mda は、それ以外の場合トラップが難しいイベントに関する XML メッセージを生成します。</span><span class="sxs-lookup"><span data-stu-id="3a219-113">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="3a219-114">マネージ コードとアンマネージ コード間の遷移のデバッグに特に役立つは。</span><span class="sxs-lookup"><span data-stu-id="3a219-114">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="3a219-115">MDA の作成をトリガーするイベントが発生したときに、ランタイムは、次の手順を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="3a219-115">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
-   <span data-ttu-id="3a219-116">ホストが登録されていない場合、 [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)を呼び出してインスタンス[iclroneventmanager::registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)の通知を受信する、`Event_MDAFired`イベント、ランタイム処理を実行、既定値は、ホストなしの動作です。</span><span class="sxs-lookup"><span data-stu-id="3a219-116">If the host has not registered an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
-   <span data-ttu-id="3a219-117">ホストがこのイベントのハンドラーを登録済みの場合、ランタイムは、デバッガーがプロセスにアタッチされているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="3a219-117">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="3a219-118">場合は、ランタイムはデバッガーを中断します。</span><span class="sxs-lookup"><span data-stu-id="3a219-118">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="3a219-119">デバッガーが引き続き発生する場合は、ホストを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3a219-119">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="3a219-120">デバッガーがアタッチされていない場合、ランタイムが呼び出す`IActionOnCLREvent::OnEvent`へのポインターを渡すと、`MDAInfo`インスタンスとして、`data`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="3a219-120">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="3a219-121">Mda をアクティブ化して、MDA がアクティブ化されたときに通知するホストを選択できます。</span><span class="sxs-lookup"><span data-stu-id="3a219-121">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="3a219-122">これにより、ホストは、営業案件を既定の動作をオーバーライドして、プロセス状態が破損を防ぐため、イベントを発生させたマネージ スレッドを中止します。</span><span class="sxs-lookup"><span data-stu-id="3a219-122">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="3a219-123">Mda の使用に関する詳細については、次を参照してください。[マネージ デバッグ アシスタントによるエラーの診断](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)です。</span><span class="sxs-lookup"><span data-stu-id="3a219-123">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a219-124">要件</span><span class="sxs-lookup"><span data-stu-id="3a219-124">Requirements</span></span>  
 <span data-ttu-id="3a219-125">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3a219-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a219-126">**ヘッダー:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="3a219-126">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="3a219-127">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="3a219-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a219-128">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a219-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a219-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a219-129">See Also</span></span>  
 [<span data-ttu-id="3a219-130">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="3a219-130">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="3a219-131">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="3a219-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

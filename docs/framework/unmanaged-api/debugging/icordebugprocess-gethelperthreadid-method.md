---
title: ICorDebugProcess::GetHelperThreadID メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHelperThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c3f879e04a710d65f812a5165c3edbfa31f8542
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419069"
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="fedc2-102">ICorDebugProcess::GetHelperThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="fedc2-102">ICorDebugProcess::GetHelperThreadID Method</span></span>
<span data-ttu-id="fedc2-103">デバッガーの内部ヘルパー スレッドのオペレーティング システム (OS) のスレッド ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="fedc2-103">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fedc2-104">構文</span><span class="sxs-lookup"><span data-stu-id="fedc2-104">Syntax</span></span>  
  
```  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fedc2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fedc2-105">Parameters</span></span>  
 `pThreadID`  
 <span data-ttu-id="fedc2-106">[out]オペレーティング システムへのポインターは、デバッガーの内部ヘルパー スレッドの ID をスレッドです。</span><span class="sxs-lookup"><span data-stu-id="fedc2-106">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fedc2-107">コメント</span><span class="sxs-lookup"><span data-stu-id="fedc2-107">Remarks</span></span>  
 <span data-ttu-id="fedc2-108">マネージ コードとアンマネージ デバッグ中には、指定した ID を持つスレッドを実行したまま、デバッガーにより配置されたブレークポイントにヒットする場合ことを確認する、デバッガーの責任です。</span><span class="sxs-lookup"><span data-stu-id="fedc2-108">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="fedc2-109">デバッガーは、ユーザーからこのスレッドを非表示にすることもします。</span><span class="sxs-lookup"><span data-stu-id="fedc2-109">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="fedc2-110">ヘルパー スレッドが存在しない場合、プロセスで、まだ、`GetHelperThreadID`メソッドで 0 を返します \*`pThreadID`です。</span><span class="sxs-lookup"><span data-stu-id="fedc2-110">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in \*`pThreadID`.</span></span>  
  
 <span data-ttu-id="fedc2-111">時間の経過と共に変更可能性がありますので、ヘルパー スレッドのスレッド ID をキャッシュすることはできません。</span><span class="sxs-lookup"><span data-stu-id="fedc2-111">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="fedc2-112">停止イベントごとにスレッド ID を再クエリする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fedc2-112">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="fedc2-113">デバッガーのヘルパー スレッドのスレッド ID が上で正しいできるようすべてアンマネージ[icordebugmanagedcallback::createthread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)できるので、そのヘルパー スレッドのスレッド ID を特定し、ユーザーに対して非表示にするデバッガー イベントです。</span><span class="sxs-lookup"><span data-stu-id="fedc2-113">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="fedc2-114">アンマネージの中にヘルパー スレッドとして識別されるスレッド`ICorDebugManagedCallback::CreateThread`イベント マネージ ユーザー コードは実行されません。</span><span class="sxs-lookup"><span data-stu-id="fedc2-114">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fedc2-115">要件</span><span class="sxs-lookup"><span data-stu-id="fedc2-115">Requirements</span></span>  
 <span data-ttu-id="fedc2-116">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fedc2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fedc2-117">**ヘッダー:** CorDebug.idl です。</span><span class="sxs-lookup"><span data-stu-id="fedc2-117">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="fedc2-118">CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fedc2-118">CorDebug.h</span></span>  
  
 <span data-ttu-id="fedc2-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fedc2-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fedc2-120">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fedc2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

---
title: "ICorDebugThread::EnumerateChains メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugThread.EnumerateChains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8e6a9637edb4a846b4d10dd6565533a9219ad558
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="3f4df-102">ICorDebugThread::EnumerateChains メソッド</span><span class="sxs-lookup"><span data-stu-id="3f4df-102">ICorDebugThread::EnumerateChains Method</span></span>
<span data-ttu-id="3f4df-103">この ICorDebugThread オブジェクト内のすべてのスタック チェーンを含む ICorDebugChainEnum 列挙子へのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="3f4df-103">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f4df-104">構文</span><span class="sxs-lookup"><span data-stu-id="3f4df-104">Syntax</span></span>  
  
```  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f4df-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3f4df-105">Parameters</span></span>  
 `ppChains`  
 <span data-ttu-id="3f4df-106">[out]アドレスへのポインター、`ICorDebugChainEnum`このスレッドは、アクティブな (つまり、最も最近) チェーンの先頭でチェーンでつながってオブジェクトにより、すべてのスタックの列挙体です。</span><span class="sxs-lookup"><span data-stu-id="3f4df-106">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f4df-107">コメント</span><span class="sxs-lookup"><span data-stu-id="3f4df-107">Remarks</span></span>  
 <span data-ttu-id="3f4df-108">スタック チェーンでは、スレッドの物理呼び出し履歴を表します。</span><span class="sxs-lookup"><span data-stu-id="3f4df-108">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="3f4df-109">次の状況では、スタック チェーンの境界を作成します。</span><span class="sxs-lookup"><span data-stu-id="3f4df-109">The following circumstances create a stack chain boundary:</span></span>  
  
-   <span data-ttu-id="3f4df-110">アンマネージ コードへマネージまたはアンマネージからマネージへの遷移です。</span><span class="sxs-lookup"><span data-stu-id="3f4df-110">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
-   <span data-ttu-id="3f4df-111">コンテキストの切り替え。</span><span class="sxs-lookup"><span data-stu-id="3f4df-111">A context switch.</span></span>  
  
-   <span data-ttu-id="3f4df-112">A デバッガーのユーザー スレッドのハイジャックです。</span><span class="sxs-lookup"><span data-stu-id="3f4df-112">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="3f4df-113">純粋なマネージ コードを 1 つのコンテキストで実行されているスレッドの簡単な例で、一対一の対応は、スレッドとスタック チェーンの間存在します。</span><span class="sxs-lookup"><span data-stu-id="3f4df-113">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="3f4df-114">デバッガーは、論理呼び出し履歴にすべてのスレッドの物理呼び出し履歴を再配置する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3f4df-114">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="3f4df-115">これには、すべてのスレッドのチェーンの呼び出し元/呼び出し先の関係を順に並べ替えられ、それらが含まれます。</span><span class="sxs-lookup"><span data-stu-id="3f4df-115">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f4df-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="3f4df-116">Requirements</span></span>  
 <span data-ttu-id="3f4df-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3f4df-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f4df-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3f4df-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f4df-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f4df-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f4df-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f4df-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

---
title: "ICorDebugThread::GetCurrentException メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetCurrentException
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c18e2dfa68d425e5ec23d4573428018bc971f8b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgetcurrentexception-method"></a><span data-ttu-id="79617-102">ICorDebugThread::GetCurrentException メソッド</span><span class="sxs-lookup"><span data-stu-id="79617-102">ICorDebugThread::GetCurrentException Method</span></span>
<span data-ttu-id="79617-103">マネージ コードによってスローされる例外を表す ICorDebugValue オブジェクトへのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="79617-103">Gets an interface pointer to an ICorDebugValue object that represents an exception that is currently being thrown by managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79617-104">構文</span><span class="sxs-lookup"><span data-stu-id="79617-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="79617-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="79617-105">Parameters</span></span>  
 `ppExceptionObject`  
 <span data-ttu-id="79617-106">[out]アドレスへのポインター、`ICorDebugValue`マネージ コードをによってスローされる例外を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="79617-106">[out] A pointer to the address of an `ICorDebugValue` object that represents the exception that is currently being thrown by managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79617-107">コメント</span><span class="sxs-lookup"><span data-stu-id="79617-107">Remarks</span></span>  
 <span data-ttu-id="79617-108">例外オブジェクトが終了するまで、例外がスローされたときから存在、`catch`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="79617-108">The exception object will exist from the time the exception is thrown until the end of the `catch` block.</span></span> <span data-ttu-id="79617-109">ICorDebugEval メソッドによって実行される、関数の評価はセットアップの例外オブジェクトをクリアし、完了時に復元します。</span><span class="sxs-lookup"><span data-stu-id="79617-109">A function evaluation, which is performed by the ICorDebugEval methods, will clear out the exception object on setup and restore it on completion.</span></span>  
  
 <span data-ttu-id="79617-110">例外は、(たとえば、フィルターまたは関数の評価で、例外がスローされた) 場合、入れ子にでき、シングル スレッド内で複数の未処理の例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="79617-110">Exceptions can be nested (for example, if an exception is thrown in a filter or in a function evaluation), so there may be multiple outstanding exceptions on a single thread.</span></span> <span data-ttu-id="79617-111">`GetCurrentException`最新の例外を返します。</span><span class="sxs-lookup"><span data-stu-id="79617-111">`GetCurrentException` returns the most current exception.</span></span>  
  
 <span data-ttu-id="79617-112">例外オブジェクトと型については、例外の有効期間全体で変更できます。</span><span class="sxs-lookup"><span data-stu-id="79617-112">The exception object and type may change throughout the life of the exception.</span></span> <span data-ttu-id="79617-113">たとえば、x の種類の例外がスローされた後に、共通言語ランタイム (CLR) 可能性がありますメモリが不足し、メモリ不足の例外に昇格させることです。</span><span class="sxs-lookup"><span data-stu-id="79617-113">For example, after an exception of type x is thrown, the common language runtime (CLR) may run out of memory and promote it to an out-of-memory exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79617-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="79617-114">Requirements</span></span>  
 <span data-ttu-id="79617-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="79617-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79617-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79617-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79617-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79617-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79617-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79617-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

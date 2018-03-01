---
title: "ICorDebugILFrame::SetIP メソッド"
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
- ICorDebugILFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: daffbbd9e961f4fdc7ff2e3c9be57e41e8fa3f78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframesetip-method"></a><span data-ttu-id="71c5a-102">ICorDebugILFrame::SetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="71c5a-102">ICorDebugILFrame::SetIP Method</span></span>
<span data-ttu-id="71c5a-103">Microsoft intermediate language (MSIL) コード内の指定したオフセット位置に、命令ポインターを設定します。</span><span class="sxs-lookup"><span data-stu-id="71c5a-103">Sets the instruction pointer to the specified offset location in the Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71c5a-104">構文</span><span class="sxs-lookup"><span data-stu-id="71c5a-104">Syntax</span></span>  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="71c5a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="71c5a-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="71c5a-106">MSIL コード内のオフセットの位置。</span><span class="sxs-lookup"><span data-stu-id="71c5a-106">The offset location in the MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71c5a-107">コメント</span><span class="sxs-lookup"><span data-stu-id="71c5a-107">Remarks</span></span>  
 <span data-ttu-id="71c5a-108">呼び出す`SetIP`すぐにすべてのフレームと現在のスレッドのチェーンが無効にします。</span><span class="sxs-lookup"><span data-stu-id="71c5a-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="71c5a-109">デバッガーには、呼び出しの後にフレーム情報が必要がある場合`SetIP`、新しいスタック トレースを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71c5a-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="71c5a-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)に有効な状態でスタック フレームを維持しようとします。</span><span class="sxs-lookup"><span data-stu-id="71c5a-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="71c5a-111">ただし、場合でも、有効な状態では、フレームは、まだある可能性があります初期化されていないローカル変数などの問題です。</span><span class="sxs-lookup"><span data-stu-id="71c5a-111">However, even if the frame is in a valid state, there still may be problems such as uninitialized local variables.</span></span> <span data-ttu-id="71c5a-112">呼び出し元は、実行中のプログラムの一貫性を保証します。</span><span class="sxs-lookup"><span data-stu-id="71c5a-112">The caller is responsible for ensuring the coherency of the running program.</span></span>  
  
 <span data-ttu-id="71c5a-113">64 ビット プラットフォームでは、上の命令ポインターを移動できません、`catch`または`finally`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="71c5a-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="71c5a-114">場合`SetIP`が呼び出された 64 ビット プラットフォームで、このような移動をするためには、エラーを示す HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="71c5a-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71c5a-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="71c5a-115">Requirements</span></span>  
 <span data-ttu-id="71c5a-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="71c5a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71c5a-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71c5a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71c5a-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71c5a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71c5a-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71c5a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

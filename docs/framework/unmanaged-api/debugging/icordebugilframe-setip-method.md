---
title: "ICorDebugILFrame::SetIP メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.SetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b92dc50777d55ba6bfa1a0559ab198dd69114ade
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframesetip-method"></a><span data-ttu-id="f0105-102">ICorDebugILFrame::SetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="f0105-102">ICorDebugILFrame::SetIP Method</span></span>
<span data-ttu-id="f0105-103">Microsoft intermediate language (MSIL) コード内の指定したオフセット位置に、命令ポインターを設定します。</span><span class="sxs-lookup"><span data-stu-id="f0105-103">Sets the instruction pointer to the specified offset location in the Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0105-104">構文</span><span class="sxs-lookup"><span data-stu-id="f0105-104">Syntax</span></span>  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0105-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f0105-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="f0105-106">MSIL コード内のオフセットの位置。</span><span class="sxs-lookup"><span data-stu-id="f0105-106">The offset location in the MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0105-107">コメント</span><span class="sxs-lookup"><span data-stu-id="f0105-107">Remarks</span></span>  
 <span data-ttu-id="f0105-108">呼び出す`SetIP`すぐにすべてのフレームと現在のスレッドのチェーンが無効にします。</span><span class="sxs-lookup"><span data-stu-id="f0105-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="f0105-109">デバッガーには、呼び出しの後にフレーム情報が必要がある場合`SetIP`、新しいスタック トレースを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0105-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="f0105-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)に有効な状態でスタック フレームを維持しようとします。</span><span class="sxs-lookup"><span data-stu-id="f0105-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="f0105-111">ただし、場合でも、有効な状態では、フレームは、まだある可能性があります初期化されていないローカル変数などの問題です。</span><span class="sxs-lookup"><span data-stu-id="f0105-111">However, even if the frame is in a valid state, there still may be problems such as uninitialized local variables.</span></span> <span data-ttu-id="f0105-112">呼び出し元は、実行中のプログラムの一貫性を保証します。</span><span class="sxs-lookup"><span data-stu-id="f0105-112">The caller is responsible for ensuring the coherency of the running program.</span></span>  
  
 <span data-ttu-id="f0105-113">64 ビット プラットフォームでは、上の命令ポインターを移動できません、`catch`または`finally`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="f0105-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="f0105-114">場合`SetIP`が呼び出された 64 ビット プラットフォームで、このような移動をするためには、エラーを示す HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="f0105-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0105-115">要件</span><span class="sxs-lookup"><span data-stu-id="f0105-115">Requirements</span></span>  
 <span data-ttu-id="f0105-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f0105-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0105-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0105-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0105-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0105-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0105-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0105-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

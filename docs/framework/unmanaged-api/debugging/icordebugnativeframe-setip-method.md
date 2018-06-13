---
title: ICorDebugNativeFrame::SetIP メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed8b6bf60790c10b9869dcc41678be050b8979dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420226"
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="16eb0-102">ICorDebugNativeFrame::SetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="16eb0-102">ICorDebugNativeFrame::SetIP Method</span></span>
<span data-ttu-id="16eb0-103">命令ポインターをネイティブ コードで指定されたオフセット位置に設定します。</span><span class="sxs-lookup"><span data-stu-id="16eb0-103">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16eb0-104">構文</span><span class="sxs-lookup"><span data-stu-id="16eb0-104">Syntax</span></span>  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16eb0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="16eb0-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="16eb0-106">[in]ネイティブ コード内のオフセットの位置。</span><span class="sxs-lookup"><span data-stu-id="16eb0-106">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16eb0-107">コメント</span><span class="sxs-lookup"><span data-stu-id="16eb0-107">Remarks</span></span>  
 <span data-ttu-id="16eb0-108">呼び出す`SetIP`すぐにすべてのフレームと現在のスレッドのチェーンが無効にします。</span><span class="sxs-lookup"><span data-stu-id="16eb0-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="16eb0-109">デバッガーには、呼び出しの後にフレーム情報が必要がある場合`SetIP`、新しいスタック トレースを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16eb0-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="16eb0-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)に有効な状態でスタック フレームを維持しようとします。</span><span class="sxs-lookup"><span data-stu-id="16eb0-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="16eb0-111">ただし、場合でも、限り、ランタイムは、有効な状態では、フレームは、まだある可能性があります初期化されていないローカル変数などの問題です。</span><span class="sxs-lookup"><span data-stu-id="16eb0-111">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="16eb0-112">呼び出し元は、実行中のプログラムの一貫性を保証します。</span><span class="sxs-lookup"><span data-stu-id="16eb0-112">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="16eb0-113">64 ビット プラットフォームでは、上の命令ポインターを移動できません、`catch`または`finally`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="16eb0-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="16eb0-114">場合`SetIP`が呼び出された 64 ビット プラットフォームで、このような移動をするためには、エラーを示す HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="16eb0-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16eb0-115">要件</span><span class="sxs-lookup"><span data-stu-id="16eb0-115">Requirements</span></span>  
 <span data-ttu-id="16eb0-116">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="16eb0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16eb0-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16eb0-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16eb0-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16eb0-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16eb0-119">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16eb0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16eb0-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="16eb0-120">See Also</span></span>  
 

---
title: ICorDebugRegisterSet::GetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetThreadContext
helpviewer_keywords:
- GetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetThreadContext method [.NET Framework debugging]
ms.assetid: 0f63400b-dc1c-48d6-b51a-75c3f7f28e03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 632d3912bae28da22e701078bb47d2d8dbfd3644
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423404"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a><span data-ttu-id="48cce-102">ICorDebugRegisterSet::GetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="48cce-102">ICorDebugRegisterSet::GetThreadContext Method</span></span>
<span data-ttu-id="48cce-103">現在のスレッドのコンテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="48cce-103">Gets the context of the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48cce-104">構文</span><span class="sxs-lookup"><span data-stu-id="48cce-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48cce-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="48cce-105">Parameters</span></span>  
 `contextSize`  
 <span data-ttu-id="48cce-106">[in]サイズをバイト単位での`context`配列。</span><span class="sxs-lookup"><span data-stu-id="48cce-106">[in] The size, in bytes, of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="48cce-107">[入力、出力].Win32 を構成するバイトの配列`CONTEXT`現在のプラットフォームの構造体。</span><span class="sxs-lookup"><span data-stu-id="48cce-107">[in, out] An array of bytes that compose the Win32 `CONTEXT` structure for the current platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48cce-108">コメント</span><span class="sxs-lookup"><span data-stu-id="48cce-108">Remarks</span></span>  
 <span data-ttu-id="48cce-109">デバッガーは、Win32 ではなくこの関数を呼び出す必要があります`GetThreadContext`関数、スレッドのコンテキストに一時的に変更がされている「乗っ取ら」状態になるためです。</span><span class="sxs-lookup"><span data-stu-id="48cce-109">The debugger should call this function instead of the Win32 `GetThreadContext` function, because the thread may be in a "hijacked" state where its context has been temporarily changed.</span></span> <span data-ttu-id="48cce-110">返されるデータは、Win32`CONTEXT`現在のプラットフォームの構造体。</span><span class="sxs-lookup"><span data-stu-id="48cce-110">The data returned is a Win32 `CONTEXT` structure for the current platform.</span></span>  
  
 <span data-ttu-id="48cce-111">使用してレジスタが有効な非リーフ フレームのクライアントを確認する必要があります[icordebugregisterset::getregistersavailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="48cce-111">For non-leaf frames, clients should check which registers are valid by using [ICorDebugRegisterSet::GetRegistersAvailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48cce-112">要件</span><span class="sxs-lookup"><span data-stu-id="48cce-112">Requirements</span></span>  
 <span data-ttu-id="48cce-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="48cce-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48cce-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48cce-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48cce-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48cce-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48cce-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48cce-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48cce-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="48cce-117">See Also</span></span>  
 [<span data-ttu-id="48cce-118">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="48cce-118">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="48cce-119">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="48cce-119">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)

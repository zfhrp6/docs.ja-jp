---
title: _EFN_StackTrace 関数
ms.date: 03/30/2017
api_name:
- _EFN_StackTrace
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_StackTrace
helpviewer_keywords:
- _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 39a249108d10e5dc382775378e2d6b84bba87356
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408087"
---
# <a name="efnstacktrace-function"></a><span data-ttu-id="ba276-102">_EFN_StackTrace 関数</span><span class="sxs-lookup"><span data-stu-id="ba276-102">_EFN_StackTrace Function</span></span>
<span data-ttu-id="ba276-103">マネージ スタック トレースのテキスト表現および `CONTEXT` レコードの配列 (アンマネージ コードとマネージ コードの間の各移行につき 1 つ) を提供します。</span><span class="sxs-lookup"><span data-stu-id="ba276-103">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba276-104">構文</span><span class="sxs-lookup"><span data-stu-id="ba276-104">Syntax</span></span>  
  
```  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba276-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ba276-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="ba276-106">[in]デバッグ中のクライアント。</span><span class="sxs-lookup"><span data-stu-id="ba276-106">[in] The client being debugged.</span></span>  
  
 `wszTextOut`  
 <span data-ttu-id="ba276-107">[out]スタック トレースのテキスト表現。</span><span class="sxs-lookup"><span data-stu-id="ba276-107">[out] The text representation of the stack trace.</span></span>  
  
 `puiTextLength`  
 <span data-ttu-id="ba276-108">[out]文字数へのポインター`wszTextOut`です。</span><span class="sxs-lookup"><span data-stu-id="ba276-108">[out] A pointer to the number of characters in `wszTextOut`.</span></span>  
  
 `pTransitionContexts`  
 <span data-ttu-id="ba276-109">[out]遷移のコンテキストの配列です。</span><span class="sxs-lookup"><span data-stu-id="ba276-109">[out] The array of transition contexts.</span></span>  
  
 `puiTransitionContextCount`  
 <span data-ttu-id="ba276-110">[out]配列内の遷移のコンテキストの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ba276-110">[out] A pointer to the number of transition contexts in the array.</span></span>  
  
 `uiSizeOfContext`  
 <span data-ttu-id="ba276-111">[in]Context 構造体のサイズ。</span><span class="sxs-lookup"><span data-stu-id="ba276-111">[in] The size of the context structure.</span></span>  
  
 `Flags`  
 <span data-ttu-id="ba276-112">[in]0 または SOS_STACKTRACE_SHOWADDRESSES (0x01) のいずれかに設定する EBP レジスタとそれぞれの前に enter スタック ポインター (ESP) を表示`module!functionname`行です。</span><span class="sxs-lookup"><span data-stu-id="ba276-112">[in] Set to either 0 or SOS_STACKTRACE_SHOWADDRESSES (0x01) to show the EBP register and the enter stack pointer (ESP) in front of each `module!functionname` line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba276-113">コメント</span><span class="sxs-lookup"><span data-stu-id="ba276-113">Remarks</span></span>  
 <span data-ttu-id="ba276-114">`_EFN_StackTrace`構造体は、WinDbg プログラム インターフェイスから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="ba276-114">The `_EFN_StackTrace` structure can be called from a WinDbg programmatic interface.</span></span> <span data-ttu-id="ba276-115">パラメーターは、次のように使用されます。</span><span class="sxs-lookup"><span data-stu-id="ba276-115">Parameters are used as follows:</span></span>  
  
-   <span data-ttu-id="ba276-116">場合`wszTextOut`が null と`puiTextLength`が null でない関数、文字列の長さを返しますで`puiTextLength`です。</span><span class="sxs-lookup"><span data-stu-id="ba276-116">If `wszTextOut` is null and `puiTextLength` is not null, the function returns the string length in `puiTextLength`.</span></span>  
  
-   <span data-ttu-id="ba276-117">場合`wszTextOut`が null でない内のテキストは、関数には格納`wszTextOut`によって示される位置まで`puiTextLength`です。</span><span class="sxs-lookup"><span data-stu-id="ba276-117">If `wszTextOut` is not null, the function stores text in `wszTextOut` up to the location indicated by `puiTextLength`.</span></span> <span data-ttu-id="ba276-118">バッファーの長さが不足している場合、バッファー、または返します E_OUTOFMEMORY で十分な空き領域が認識されたかどうかを正常に返します。</span><span class="sxs-lookup"><span data-stu-id="ba276-118">It returns successfully if there was enough room in the buffer, or returns E_OUTOFMEMORY if the buffer was not long enough.</span></span>  
  
-   <span data-ttu-id="ba276-119">場合、関数の遷移の部分は無視されます`pTransitionContexts`と`puiTransitionContextCount`が両方とも null です。</span><span class="sxs-lookup"><span data-stu-id="ba276-119">The transition portion of the function is ignored if `pTransitionContexts` and `puiTransitionContextCount` are both null.</span></span> <span data-ttu-id="ba276-120">この場合、関数は、関数名のみのテキスト出力を持つ呼び出し元を提供します。</span><span class="sxs-lookup"><span data-stu-id="ba276-120">In this case, the function provides callers with text output of only the function names.</span></span>  
  
-   <span data-ttu-id="ba276-121">場合`pTransitionContexts`が null と`puiTransitionContextCount`が null でない関数、必要なエントリ数を返しますのコンテキストで`puiTransitionContextCount`です。</span><span class="sxs-lookup"><span data-stu-id="ba276-121">If `pTransitionContexts` is null and `puiTransitionContextCount` is not null, the function returns the necessary number of context entries in `puiTransitionContextCount`.</span></span>  
  
-   <span data-ttu-id="ba276-122">場合`pTransitionContexts`が null でない関数として扱われます長さの構造体の配列`puiTransitionContextCount`です。</span><span class="sxs-lookup"><span data-stu-id="ba276-122">If `pTransitionContexts` is not null, the function treats it as an array of structures of length `puiTransitionContextCount`.</span></span> <span data-ttu-id="ba276-123">構造体のサイズである`uiSizeOfContext`のサイズを指定する必要があります[SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)または`CONTEXT`アーキテクチャに対応します。</span><span class="sxs-lookup"><span data-stu-id="ba276-123">The structure size is given by `uiSizeOfContext`, and must be the size of [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) or `CONTEXT` for the architecture.</span></span>  
  
-   <span data-ttu-id="ba276-124">`wszTextOut` 次の形式で書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="ba276-124">`wszTextOut` is written in the following format:</span></span>  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
-   <span data-ttu-id="ba276-125">16 進数でオフセットが「0x0」の場合、オフセットは書き込まれません。</span><span class="sxs-lookup"><span data-stu-id="ba276-125">If the offset in hex is 0x0, no offset is written.</span></span>  
  
-   <span data-ttu-id="ba276-126">ない場合マネージ コードのスレッドで現在のコンテキストで、SOS_E_NOMANAGEDCODE を返します。</span><span class="sxs-lookup"><span data-stu-id="ba276-126">If there is no managed code on the thread currently in context, the function returns SOS_E_NOMANAGEDCODE.</span></span>  
  
-   <span data-ttu-id="ba276-127">`Flags`パラメーターが 0 または前にある各 EBP と ESP を表示する SOS_STACKTRACE_SHOWADDRESSES`module!functionname`行です。</span><span class="sxs-lookup"><span data-stu-id="ba276-127">The `Flags` parameter is either 0 or SOS_STACKTRACE_SHOWADDRESSES to see EBP and ESP in front of each `module!functionname` line.</span></span> <span data-ttu-id="ba276-128">既定では、これは 0 です。</span><span class="sxs-lookup"><span data-stu-id="ba276-128">By default, it is 0.</span></span>  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a><span data-ttu-id="ba276-129">要件</span><span class="sxs-lookup"><span data-stu-id="ba276-129">Requirements</span></span>  
 <span data-ttu-id="ba276-130">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ba276-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba276-131">**ヘッダー:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="ba276-131">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="ba276-132">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba276-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba276-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba276-133">See Also</span></span>  
 [<span data-ttu-id="ba276-134">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="ba276-134">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

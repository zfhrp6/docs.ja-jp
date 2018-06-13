---
title: ICorDebugModule2::SetJMCStatus メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a56b5c31c26dbe5c5371fdb7a10c13ad11847117
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419473"
---
# <a name="icordebugmodule2setjmcstatus-method"></a><span data-ttu-id="68607-102">ICorDebugModule2::SetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="68607-102">ICorDebugModule2::SetJMCStatus Method</span></span>
<span data-ttu-id="68607-103">この ICorDebugModule2 を除き、指定した値でのすべてのクラスのすべてのメソッドだけマイ コードのみ (JMC) 状態を設定、`pTokens`配列で、その逆の値に設定します。</span><span class="sxs-lookup"><span data-stu-id="68607-103">Sets the Just My Code (JMC) status of all methods of all the classes in this ICorDebugModule2 to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68607-104">構文</span><span class="sxs-lookup"><span data-stu-id="68607-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68607-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="68607-105">Parameters</span></span>  
 `bIsJustMycode`  
 <span data-ttu-id="68607-106">[in]設定`true`に、コードがデバッグ対象以外の場合は、設定`false`です。</span><span class="sxs-lookup"><span data-stu-id="68607-106">[in] Set to `true` if the code is to be debugged; otherwise, set to `false`.</span></span>  
  
 `cTokens`  
 <span data-ttu-id="68607-107">[in] `pTokens` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="68607-107">[in] The size of the `pTokens` array.</span></span>  
  
 `pTokens`  
 <span data-ttu-id="68607-108">[in]配列`mdToken`その JMC ステータスに設定するメソッドを指すそれぞれの値です。`bIsJustMycode`です。</span><span class="sxs-lookup"><span data-stu-id="68607-108">[in] An array of `mdToken` values, each of which refers to a method that will have its JMC status set to !`bIsJustMycode`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68607-109">コメント</span><span class="sxs-lookup"><span data-stu-id="68607-109">Remarks</span></span>  
 <span data-ttu-id="68607-110">指定されている各メソッドの JMC ステータス、`pTokens`と対照的に配列が設定されている、`bIsJustMycode`値。</span><span class="sxs-lookup"><span data-stu-id="68607-110">The JMC status of each method that is specified in the `pTokens` array is set to the opposite of the `bIsJustMycode` value.</span></span> <span data-ttu-id="68607-111">このモジュールで他のすべてのメソッドの状態に設定、`bIsJustMycode`値。</span><span class="sxs-lookup"><span data-stu-id="68607-111">The status of all other methods in this module is set to the `bIsJustMycode` value.</span></span>  
  
 <span data-ttu-id="68607-112">`SetJMCStatus`メソッドは、このモジュールのすべての以前 JMC 設定を消去します。</span><span class="sxs-lookup"><span data-stu-id="68607-112">The `SetJMCStatus` method erases all previous JMC settings in this module.</span></span>  
  
 <span data-ttu-id="68607-113">`SetJMCStatus`メソッドは、すべての関数が正常に設定されている場合に S_OK HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="68607-113">The `SetJMCStatus` method returns an S_OK HRESULT if all functions were set successfully.</span></span> <span data-ttu-id="68607-114">CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT される関数の一部である場合は、マークを返す`true`デバッグ可能ではありません。</span><span class="sxs-lookup"><span data-stu-id="68607-114">It returns a CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT if some functions that are marked `true` are not debuggable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68607-115">要件</span><span class="sxs-lookup"><span data-stu-id="68607-115">Requirements</span></span>  
 <span data-ttu-id="68607-116">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="68607-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68607-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68607-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68607-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68607-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68607-119">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68607-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

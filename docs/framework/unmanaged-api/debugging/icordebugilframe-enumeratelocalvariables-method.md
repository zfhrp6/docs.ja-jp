---
title: ICorDebugILFrame::EnumerateLocalVariables メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fd7694901534ad6897bbf78239081af6314e4bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415471"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="f4c4f-102">ICorDebugILFrame::EnumerateLocalVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="f4c4f-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="f4c4f-103">このフレームのローカル変数の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="f4c4f-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4c4f-104">構文</span><span class="sxs-lookup"><span data-stu-id="f4c4f-104">Syntax</span></span>  
  
```  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4c4f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f4c4f-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="f4c4f-106">[out]このフレームのローカル変数の列挙子である ICorDebugValueEnum オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f4c4f-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4c4f-107">コメント</span><span class="sxs-lookup"><span data-stu-id="f4c4f-107">Remarks</span></span>  
 <span data-ttu-id="f4c4f-108">`EnumerateLocalVariables` ICorDebugILFrame オブジェクトによって表される呼び出しフレームで使用できるローカル変数の一覧を表示する列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="f4c4f-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="f4c4f-109">一覧が含まれない場合ローカル変数の実行中の関数では、アクティブなそれらの一部はない可能性がします。</span><span class="sxs-lookup"><span data-stu-id="f4c4f-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4c4f-110">要件</span><span class="sxs-lookup"><span data-stu-id="f4c4f-110">Requirements</span></span>  
 <span data-ttu-id="f4c4f-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f4c4f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4c4f-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4c4f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4c4f-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4c4f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4c4f-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4c4f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

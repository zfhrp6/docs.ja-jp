---
title: "ICorDebugILFrame::EnumerateLocalVariables メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.EnumerateLocalVariables
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fb4e6bead1bb4933f8f9af4ffb1bfb9157a028c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="8225f-102">ICorDebugILFrame::EnumerateLocalVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="8225f-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="8225f-103">このフレームのローカル変数の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="8225f-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8225f-104">構文</span><span class="sxs-lookup"><span data-stu-id="8225f-104">Syntax</span></span>  
  
```  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8225f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8225f-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="8225f-106">[out]このフレームのローカル変数の列挙子である ICorDebugValueEnum オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8225f-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8225f-107">コメント</span><span class="sxs-lookup"><span data-stu-id="8225f-107">Remarks</span></span>  
 <span data-ttu-id="8225f-108">`EnumerateLocalVariables`ICorDebugILFrame オブジェクトによって表される呼び出しフレームで使用できるローカル変数の一覧を表示する列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="8225f-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="8225f-109">一覧が含まれない場合ローカル変数の実行中の関数では、アクティブなそれらの一部はない可能性がします。</span><span class="sxs-lookup"><span data-stu-id="8225f-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8225f-110">要件</span><span class="sxs-lookup"><span data-stu-id="8225f-110">Requirements</span></span>  
 <span data-ttu-id="8225f-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8225f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8225f-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8225f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8225f-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8225f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8225f-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8225f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

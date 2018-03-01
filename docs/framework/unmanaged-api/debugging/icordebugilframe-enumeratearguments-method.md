---
title: "ICorDebugILFrame::EnumerateArguments メソッド"
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
- ICorDebugILFrame.EnumerateArguments
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateArguments
helpviewer_keywords:
- ICorDebugILFrame::EnumerateArguments method [.NET Framework debugging]
- EnumerateArguments method [.NET Framework debugging]
ms.assetid: 00ac81e2-a774-422a-bd88-54a4b3c99f73
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 474118abc505928d16737d792a619e75f1209344
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="b7ee5-102">ICorDebugILFrame::EnumerateArguments メソッド</span><span class="sxs-lookup"><span data-stu-id="b7ee5-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="b7ee5-103">引数のこのフレームの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="b7ee5-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7ee5-104">構文</span><span class="sxs-lookup"><span data-stu-id="b7ee5-104">Syntax</span></span>  
  
```  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7ee5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b7ee5-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="b7ee5-106">[out]引数は、このフレームの列挙子である ICorDebugValueEnum オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b7ee5-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7ee5-107">コメント</span><span class="sxs-lookup"><span data-stu-id="b7ee5-107">Remarks</span></span>  
 <span data-ttu-id="b7ee5-108">`EnumerateArguments`ICorDebugILFrame オブジェクトによって表される呼び出しフレームで使用可能な引数の一覧を表示する列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="b7ee5-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="b7ee5-109">一覧には引数には表示[vararg](/cpp/windows/vararg) (つまり、可変個の引数) な引数がだけでなく`vararg`です。</span><span class="sxs-lookup"><span data-stu-id="b7ee5-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7ee5-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="b7ee5-110">Requirements</span></span>  
 <span data-ttu-id="b7ee5-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b7ee5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7ee5-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7ee5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7ee5-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7ee5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7ee5-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7ee5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

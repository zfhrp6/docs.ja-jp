---
title: "ICorDebugEval2::NewStringWithLength メソッド"
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
- ICorDebugEval2.NewStringWithLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1cd2bc201210bc9af8c13c83553b581c080f658a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="7d63d-102">ICorDebugEval2::NewStringWithLength メソッド</span><span class="sxs-lookup"><span data-stu-id="7d63d-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="7d63d-103">指定された内容を指定した長さの文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="7d63d-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d63d-104">構文</span><span class="sxs-lookup"><span data-stu-id="7d63d-104">Syntax</span></span>  
  
```  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d63d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7d63d-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="7d63d-106">[in]文字列値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="7d63d-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="7d63d-107">[in]文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="7d63d-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d63d-108">コメント</span><span class="sxs-lookup"><span data-stu-id="7d63d-108">Remarks</span></span>  
 <span data-ttu-id="7d63d-109">場合は、文字列の末尾の null 文字できると予想される管理対象の文字列での呼び出し元、`NewStringWithLength`メソッドでは、文字列の長さが、末尾の null 文字が含まれることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d63d-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="7d63d-110">文字列は常に、現在のスレッドが実行しているアプリケーション ドメインで作成されます。</span><span class="sxs-lookup"><span data-stu-id="7d63d-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d63d-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="7d63d-111">Requirements</span></span>  
 <span data-ttu-id="7d63d-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7d63d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d63d-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d63d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d63d-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d63d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d63d-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d63d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

---
title: ICorDebugEval2::NewStringWithLength メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b3b77a0ffc7af3b3640d1b255bd3be522f45a7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413551"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="6ed1b-102">ICorDebugEval2::NewStringWithLength メソッド</span><span class="sxs-lookup"><span data-stu-id="6ed1b-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="6ed1b-103">指定された内容を指定した長さの文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="6ed1b-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ed1b-104">構文</span><span class="sxs-lookup"><span data-stu-id="6ed1b-104">Syntax</span></span>  
  
```  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ed1b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6ed1b-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="6ed1b-106">[in]文字列値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6ed1b-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="6ed1b-107">[in]文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="6ed1b-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ed1b-108">コメント</span><span class="sxs-lookup"><span data-stu-id="6ed1b-108">Remarks</span></span>  
 <span data-ttu-id="6ed1b-109">場合は、文字列の末尾の null 文字できると予想される管理対象の文字列での呼び出し元、`NewStringWithLength`メソッドでは、文字列の長さが、末尾の null 文字が含まれることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ed1b-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="6ed1b-110">文字列は常に、現在のスレッドが実行しているアプリケーション ドメインで作成されます。</span><span class="sxs-lookup"><span data-stu-id="6ed1b-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ed1b-111">要件</span><span class="sxs-lookup"><span data-stu-id="6ed1b-111">Requirements</span></span>  
 <span data-ttu-id="6ed1b-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6ed1b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ed1b-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6ed1b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ed1b-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ed1b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ed1b-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ed1b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

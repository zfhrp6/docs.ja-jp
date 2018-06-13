---
title: ICorDebugFunction2::GetVersionNumber メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdd2151c4886959647de4f9e27a20a93ffc07429
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420054"
---
# <a name="icordebugfunction2getversionnumber-method"></a><span data-ttu-id="20bfd-102">ICorDebugFunction2::GetVersionNumber メソッド</span><span class="sxs-lookup"><span data-stu-id="20bfd-102">ICorDebugFunction2::GetVersionNumber Method</span></span>
<span data-ttu-id="20bfd-103">この関数のエディット コンティニュ バージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="20bfd-103">Gets the Edit and Continue version of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20bfd-104">構文</span><span class="sxs-lookup"><span data-stu-id="20bfd-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20bfd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="20bfd-105">Parameters</span></span>  
 `pnVersion`  
 <span data-ttu-id="20bfd-106">[out]ICorDebugFunction2 オブジェクトによって表される関数のバージョン番号を示す整数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="20bfd-106">[out] A pointer to an integer that is the version number of the function that is represented by this ICorDebugFunction2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20bfd-107">コメント</span><span class="sxs-lookup"><span data-stu-id="20bfd-107">Remarks</span></span>  
 <span data-ttu-id="20bfd-108">ランタイムの追跡、デバッグ セッション中に各モジュールに行われた編集の数。</span><span class="sxs-lookup"><span data-stu-id="20bfd-108">The runtime keeps track of the number of edits that have taken place to each module during a debug session.</span></span> <span data-ttu-id="20bfd-109">関数のバージョン番号は 1 つの関数を導入した編集数よりも詳細です。</span><span class="sxs-lookup"><span data-stu-id="20bfd-109">The version number of a function is one more than the number of the edit that introduced the function.</span></span> <span data-ttu-id="20bfd-110">関数の元のバージョンは 1 です。</span><span class="sxs-lookup"><span data-stu-id="20bfd-110">The function's original version is version 1.</span></span> <span data-ttu-id="20bfd-111">数は、モジュールのされるたびに増加[icordebugmodule 2::applychanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)でそのモジュールが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="20bfd-111">The number is incremented for a module every time [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) is called on that module.</span></span> <span data-ttu-id="20bfd-112">したがって、最初と 3 番目の呼び出しで、関数の本体が置き換えられた場合`ICorDebugModule2::ApplyChanges`、`GetVersionNumber`バージョン 1、2、または 4 その関数のバージョンではない 3 を返す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="20bfd-112">Thus, if a function’s body was replaced in the first and third call to `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` may return version 1, 2, or 4 for that function, but not version 3.</span></span> <span data-ttu-id="20bfd-113">(その関数がないバージョン 3 です。)</span><span class="sxs-lookup"><span data-stu-id="20bfd-113">(That function would have no version 3.)</span></span>  
  
 <span data-ttu-id="20bfd-114">バージョン番号は、モジュールごとに個別に追跡されます。</span><span class="sxs-lookup"><span data-stu-id="20bfd-114">The version number is tracked separately for each module.</span></span> <span data-ttu-id="20bfd-115">したがって、モジュール 1 および第 2 章に none で 4 つの編集を実行するとモジュール 1 で、[次へ] の編集は、その 6 のバージョン番号をモジュール 1 で編集されたすべての関数に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="20bfd-115">So, if you perform four edits on Module 1, and none on Module 2, your next edit on Module 1 will assign a version number of 6 to all the edited functions in Module 1.</span></span> <span data-ttu-id="20bfd-116">編集する場合は、同じモジュール 2、第 2 章の関数は 2 のバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="20bfd-116">If the same edit touches Module 2, the functions in Module 2 will get a version number of 2.</span></span>  
  
 <span data-ttu-id="20bfd-117">バージョン番号を取得して、`GetVersionNumber`メソッドによって取得されるよりも低い場合があります[icordebugfunction::getcurrentversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="20bfd-117">The version number obtained by the `GetVersionNumber` method may be lower than that obtained by [ICorDebugFunction::GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).</span></span>  
  
 <span data-ttu-id="20bfd-118">[Icordebugcode::getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)メソッドとして同じ操作を実行`ICorDebugFunction2::GetVersionNumber`です。</span><span class="sxs-lookup"><span data-stu-id="20bfd-118">The [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method performs the same operation as `ICorDebugFunction2::GetVersionNumber`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20bfd-119">要件</span><span class="sxs-lookup"><span data-stu-id="20bfd-119">Requirements</span></span>  
 <span data-ttu-id="20bfd-120">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="20bfd-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20bfd-121">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20bfd-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20bfd-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20bfd-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20bfd-123">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20bfd-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

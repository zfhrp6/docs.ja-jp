---
title: "ICorDebugEval::CallFunction メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.CallFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 72713d81931b53e8d61fb39cee146fd30a59bfcc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalcallfunction-method"></a><span data-ttu-id="5d804-102">ICorDebugEval::CallFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="5d804-102">ICorDebugEval::CallFunction Method</span></span>
<span data-ttu-id="5d804-103">指定した関数への呼び出しを設定します。</span><span class="sxs-lookup"><span data-stu-id="5d804-103">Sets up a call to the specified function.</span></span>  
  
 <span data-ttu-id="5d804-104">このメソッドは、.NET Framework version 2.0 廃止されています。</span><span class="sxs-lookup"><span data-stu-id="5d804-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="5d804-105">使用して[icordebugeval 2::callparameterizedfunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)代わりにします。</span><span class="sxs-lookup"><span data-stu-id="5d804-105">Use [ICorDebugEval2::CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d804-106">構文</span><span class="sxs-lookup"><span data-stu-id="5d804-106">Syntax</span></span>  
  
```  
HRESULT CallFunction (  
    [in] ICorDebugFunction  *pFunction,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d804-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5d804-107">Parameters</span></span>  
 `pFunction`  
 <span data-ttu-id="5d804-108">[in]呼び出される関数を指定する ICorDebugFunction オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5d804-108">[in] Pointer to an ICorDebugFunction object that specifies the function to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="5d804-109">[in]関数の引数の数。</span><span class="sxs-lookup"><span data-stu-id="5d804-109">[in] The number of arguments for the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="5d804-110">[in]ポインターの配列、それぞれのオブジェクトをポイントする ICorDebugValue 関数に渡される引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5d804-110">[in] An array of pointers, each of which points to an ICorDebugValue object that specifies an argument to be passed to the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d804-111">コメント</span><span class="sxs-lookup"><span data-stu-id="5d804-111">Remarks</span></span>  
 <span data-ttu-id="5d804-112">終了した場合は、仮想`CallFunction`仮想ディスパッチを実行します。</span><span class="sxs-lookup"><span data-stu-id="5d804-112">If the function is virtual, `CallFunction` will perform virtual dispatch.</span></span> <span data-ttu-id="5d804-113">関数は、別のアプリケーション ドメインでは、すべての引数がそのアプリケーション ドメイン内にも限り遷移が発生します。</span><span class="sxs-lookup"><span data-stu-id="5d804-113">If the function is in a different application domain, a transition will occur as long as all arguments are also in that application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d804-114">要件</span><span class="sxs-lookup"><span data-stu-id="5d804-114">Requirements</span></span>  
 <span data-ttu-id="5d804-115">**プラットフォーム:** WindowSee[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5d804-115">**Platforms:** WindowSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d804-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d804-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d804-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d804-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d804-118">**.NET framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="5d804-118">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d804-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d804-119">See Also</span></span>  
 [<span data-ttu-id="5d804-120">CallParameterizedFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="5d804-120">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)

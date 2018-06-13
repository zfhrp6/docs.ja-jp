---
title: ICorDebugFunction::GetNativeCode メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1cb073c1f93c6d60d86e5160dcfb0cbdaf1cd33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414572"
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="d9d23-102">ICorDebugFunction::GetNativeCode メソッド</span><span class="sxs-lookup"><span data-stu-id="d9d23-102">ICorDebugFunction::GetNativeCode Method</span></span>
<span data-ttu-id="d9d23-103">この ICorDebugFunction インスタンスで表される関数のネイティブ コードを取得します。</span><span class="sxs-lookup"><span data-stu-id="d9d23-103">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9d23-104">構文</span><span class="sxs-lookup"><span data-stu-id="d9d23-104">Syntax</span></span>  
  
```  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9d23-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d9d23-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="d9d23-106">[out]この関数は、Microsoft intermediate language (MSIL) コード ジャストでタイム (JIT) コンパイルされていない場合に、この関数の場合、または null の場合、ネイティブ コードを表す ICorDebugCode インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d9d23-106">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9d23-107">コメント</span><span class="sxs-lookup"><span data-stu-id="d9d23-107">Remarks</span></span>  
 <span data-ttu-id="d9d23-108">場合、表される関数はこの`ICorDebugFunction`インスタンス JIT でコンパイルされた 2 回以上のジェネリック型の場合、`GetNativeCode`ランダムなネイティブ コード オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="d9d23-108">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9d23-109">要件</span><span class="sxs-lookup"><span data-stu-id="d9d23-109">Requirements</span></span>  
 <span data-ttu-id="d9d23-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d9d23-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9d23-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d9d23-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9d23-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9d23-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9d23-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9d23-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

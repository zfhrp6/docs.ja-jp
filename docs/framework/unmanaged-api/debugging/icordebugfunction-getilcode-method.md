---
title: ICorDebugFunction::GetILCode メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetILCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac34fbca56c8a0f00ee3a7e0f898b8ee03287b11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="373b7-102">ICorDebugFunction::GetILCode メソッド</span><span class="sxs-lookup"><span data-stu-id="373b7-102">ICorDebugFunction::GetILCode Method</span></span>
<span data-ttu-id="373b7-103">この ICorDebugFunction オブジェクトに関連付けられている Microsoft intermediate language (MSIL) コードを表す ICorDebugCode インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="373b7-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="373b7-104">構文</span><span class="sxs-lookup"><span data-stu-id="373b7-104">Syntax</span></span>  
  
```  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="373b7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="373b7-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="373b7-106">[out]ポインター、`ICorDebugCode`インスタンス、または関数が MSIL にコンパイルされていない場合は null です。</span><span class="sxs-lookup"><span data-stu-id="373b7-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="373b7-107">コメント</span><span class="sxs-lookup"><span data-stu-id="373b7-107">Remarks</span></span>  
 <span data-ttu-id="373b7-108">この関数でエディット コンティニュが許可されている場合、`GetILCode`メソッドは、共通言語ランタイム (CLR) 内のコードのこの関数の編集済みのバージョンに対応する MSIL コードを取得します。</span><span class="sxs-lookup"><span data-stu-id="373b7-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="373b7-109">要件</span><span class="sxs-lookup"><span data-stu-id="373b7-109">Requirements</span></span>  
 <span data-ttu-id="373b7-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="373b7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="373b7-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="373b7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="373b7-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="373b7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="373b7-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="373b7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

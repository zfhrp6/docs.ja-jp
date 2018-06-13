---
title: ICorDebugFunction::CreateBreakpoint メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::CreateBreakpoint
helpviewer_keywords:
- ICorDebugFunction::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: ffd0f708-0d21-4fae-a395-63b6c45828fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2881b1f420d8e177e093969b2cdd9f2ff36883f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412521"
---
# <a name="icordebugfunctioncreatebreakpoint-method"></a><span data-ttu-id="79d3c-102">ICorDebugFunction::CreateBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="79d3c-102">ICorDebugFunction::CreateBreakpoint Method</span></span>
<span data-ttu-id="79d3c-103">この関数の先頭にブレークポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="79d3c-103">Creates a breakpoint at the beginning of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79d3c-104">構文</span><span class="sxs-lookup"><span data-stu-id="79d3c-104">Syntax</span></span>  
  
```  
HRESULT CreateBreakpoint (  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="79d3c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="79d3c-105">Parameters</span></span>  
 `ppBreakpoint`  
 <span data-ttu-id="79d3c-106">[out]関数の新しいブレークポイントを表す ICorDebugFunctionBreakpoint オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="79d3c-106">[out] A pointer to the address of an ICorDebugFunctionBreakpoint object that represents the new breakpoint for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79d3c-107">要件</span><span class="sxs-lookup"><span data-stu-id="79d3c-107">Requirements</span></span>  
 <span data-ttu-id="79d3c-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="79d3c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79d3c-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79d3c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79d3c-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79d3c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79d3c-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79d3c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

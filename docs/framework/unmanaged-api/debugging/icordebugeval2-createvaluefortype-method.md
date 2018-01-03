---
title: "ICorDebugEval2::CreateValueForType メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.CreateValueForType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 18e7eb5fc30c27fd2c4865dc61e2f75dc9e96068
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="dd384-102">ICorDebugEval2::CreateValueForType メソッド</span><span class="sxs-lookup"><span data-stu-id="dd384-102">ICorDebugEval2::CreateValueForType Method</span></span>
<span data-ttu-id="dd384-103">0 または null の初期値を持つ、指定した型の新しい ICorDebugValue へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="dd384-103">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd384-104">構文</span><span class="sxs-lookup"><span data-stu-id="dd384-104">Syntax</span></span>  
  
```  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd384-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dd384-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="dd384-106">[in]型を表す ICorDebugType オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dd384-106">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="dd384-107">[out]アドレスへのポインター、`ICorDebugValue`値を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="dd384-107">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd384-108">コメント</span><span class="sxs-lookup"><span data-stu-id="dd384-108">Remarks</span></span>  
 <span data-ttu-id="dd384-109">`CreateValueForType`一般化[icordebugeval::createvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)ことで、任意のオブジェクトの種類を指定するなど構築された型など`List<int>`です。</span><span class="sxs-lookup"><span data-stu-id="dd384-109">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="dd384-110">このメソッドの唯一の目的では、関数の評価に渡すことができる値を生成します。</span><span class="sxs-lookup"><span data-stu-id="dd384-110">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="dd384-111">種類は、クラスまたは値型にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd384-111">The type must be a class or a value type.</span></span> <span data-ttu-id="dd384-112">このメソッドを使用して、配列の値または文字列値を作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="dd384-112">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd384-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="dd384-113">Requirements</span></span>  
 <span data-ttu-id="dd384-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dd384-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd384-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dd384-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd384-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd384-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd384-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd384-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

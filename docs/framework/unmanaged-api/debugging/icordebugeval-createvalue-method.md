---
title: "ICorDebugEval::CreateValue メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.CreateValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 64d55a951795cc5efc1bfc624dbe07575be153aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalcreatevalue-method"></a><span data-ttu-id="c95b0-102">ICorDebugEval::CreateValue メソッド</span><span class="sxs-lookup"><span data-stu-id="c95b0-102">ICorDebugEval::CreateValue Method</span></span>
<span data-ttu-id="c95b0-103">0 または null の初期値を指定した型の値を作成します。</span><span class="sxs-lookup"><span data-stu-id="c95b0-103">Creates a value of the specified type, with an initial value of zero or null.</span></span>  
  
 <span data-ttu-id="c95b0-104">このメソッドは、.NET Framework version 2.0 廃止されています。</span><span class="sxs-lookup"><span data-stu-id="c95b0-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="c95b0-105">使用して[icordebugeval 2::createvaluefortype](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)代わりにします。</span><span class="sxs-lookup"><span data-stu-id="c95b0-105">Use [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c95b0-106">構文</span><span class="sxs-lookup"><span data-stu-id="c95b0-106">Syntax</span></span>  
  
```  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c95b0-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c95b0-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="c95b0-108">[in]値、 [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md)列挙値の型を指定します。</span><span class="sxs-lookup"><span data-stu-id="c95b0-108">[in] A value of the [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) enumeration that specifies the type of the value.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="c95b0-109">[in]ポインター、 [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)型がプリミティブ型ではない場合、値のクラスを指定するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c95b0-109">[in] Pointer to an [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) object that specifies the class of the value, if the type is not a primitive type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c95b0-110">[out]値を表す"ICorDebugValue"オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c95b0-110">[out] Pointer to the address of an "ICorDebugValue" object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c95b0-111">コメント</span><span class="sxs-lookup"><span data-stu-id="c95b0-111">Remarks</span></span>  
 <span data-ttu-id="c95b0-112">`CreateValue`作成、`ICorDebugValue`関数の評価に使用する際の目的で指定された型のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c95b0-112">`CreateValue` creates an `ICorDebugValue` object of the given type for the sole purpose of using it in a function evaluation.</span></span> <span data-ttu-id="c95b0-113">パラメーターとしてユーザー定数を渡すには、この値のオブジェクトを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c95b0-113">This value object can be used to pass user constants as parameters.</span></span>  
  
 <span data-ttu-id="c95b0-114">値の型がプリミティブ型の場合は、その初期値は、0 または null。</span><span class="sxs-lookup"><span data-stu-id="c95b0-114">If the type of the value is a primitive type, its initial value is zero or null.</span></span> <span data-ttu-id="c95b0-115">使用して[icordebuggenericvalue::setvalue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)プリミティブ型の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="c95b0-115">Use [ICorDebugGenericValue::SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) to set the value of a primitive type.</span></span>  
  
 <span data-ttu-id="c95b0-116">場合の値`elementType`ELEMENT_TYPE_CLASS は、"ICorDebugReferenceValue"を取得する (で返される`ppValue`) null オブジェクト参照を表すです。</span><span class="sxs-lookup"><span data-stu-id="c95b0-116">If the value of `elementType` is ELEMENT_TYPE_CLASS, you get an "ICorDebugReferenceValue" (returned in `ppValue`) representing the null object reference.</span></span> <span data-ttu-id="c95b0-117">このオブジェクトを使用して、オブジェクト参照のパラメーターを持つ関数の評価に null を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="c95b0-117">You can use this object to pass null to a function evaluation that has object reference parameters.</span></span> <span data-ttu-id="c95b0-118">設定することはできません、`ICorDebugValue`ものがデータ ソースに、常に null です。</span><span class="sxs-lookup"><span data-stu-id="c95b0-118">You cannot set the `ICorDebugValue` to anything; it always remains null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c95b0-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="c95b0-119">Requirements</span></span>  
 <span data-ttu-id="c95b0-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c95b0-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c95b0-121">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c95b0-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c95b0-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c95b0-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c95b0-123">**.NET framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="c95b0-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c95b0-124">参照</span><span class="sxs-lookup"><span data-stu-id="c95b0-124">See Also</span></span>  
    
 [<span data-ttu-id="c95b0-125">CreateValueForType メソッド</span><span class="sxs-lookup"><span data-stu-id="c95b0-125">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)  
 <span data-ttu-id="c95b0-126">ICorDebugValue</span><span class="sxs-lookup"><span data-stu-id="c95b0-126">ICorDebugValue</span></span>

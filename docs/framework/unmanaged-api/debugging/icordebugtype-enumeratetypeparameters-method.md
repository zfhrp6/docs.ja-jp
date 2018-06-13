---
title: ICorDebugType::EnumerateTypeParameters メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugType.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12b002aaad65fd5f2a1207700c8de2ca8dd60eec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421880"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a><span data-ttu-id="aebdc-102">ICorDebugType::EnumerateTypeParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="aebdc-102">ICorDebugType::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="aebdc-103">含む ICorDebugTypeEnum へのインターフェイス ポインターを取得、<xref:System.Type>この ICorDebugType によって参照されるクラスのパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="aebdc-103">Gets an interface pointer to an ICorDebugTypeEnum that contains the <xref:System.Type> parameters of the class referenced by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aebdc-104">構文</span><span class="sxs-lookup"><span data-stu-id="aebdc-104">Syntax</span></span>  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aebdc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aebdc-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="aebdc-106">[out]アドレスへのポインター、`ICorDebugTypeEnum`型のパラメーターを格納しています。</span><span class="sxs-lookup"><span data-stu-id="aebdc-106">[out] A pointer to the address of an `ICorDebugTypeEnum` that contains the parameters of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aebdc-107">コメント</span><span class="sxs-lookup"><span data-stu-id="aebdc-107">Remarks</span></span>  
 <span data-ttu-id="aebdc-108">使用することができます`EnumerateTypeParameters`CorElementType 値がによって返される場合[icordebugtype::gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) ELEMENT_TYPE_CLASS ELEMENT_TYPE_VALUETYPE、ELEMENT_TYPE_ARRAY、インポートする場合、ELEMENT_TYPE_BYREF ELEMENT_TYPE にはPTR、または ELEMENT_TYPE_FNPTR します。</span><span class="sxs-lookup"><span data-stu-id="aebdc-108">You can use `EnumerateTypeParameters` if the CorElementType value returned by [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) is ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR, or ELEMENT_TYPE_FNPTR.</span></span> <span data-ttu-id="aebdc-109">パラメーターとその順序の数は、型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="aebdc-109">The number of parameters and their order depends on the type:</span></span>  
  
-   <span data-ttu-id="aebdc-110">ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE: に含まれている型パラメーターの数、`ICorDebugTypeEnum`このメソッドが戻るし、対応するクラスを仮引数型のパラメーターの数によって異なります。</span><span class="sxs-lookup"><span data-stu-id="aebdc-110">ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE: The number of type parameters contained in the `ICorDebugTypeEnum` that this method returns, will depend on the number of formal type parameters for the corresponding class.</span></span> <span data-ttu-id="aebdc-111">たとえば、次の種類は`class Dict<String,int32>`、し`EnumerateTypeParameters`が返されます、`ICorDebugTypeEnum`を表すオブジェクトを格納している`String`と`int32`シーケンスでします。</span><span class="sxs-lookup"><span data-stu-id="aebdc-111">For example, if the type is `class Dict<String,int32>`, then `EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains objects representing `String` and `int32` in sequence.</span></span>  
  
-   <span data-ttu-id="aebdc-112">ELEMENT_TYPE_FNPTR: 含まれている型パラメーターの数の`ICorDebugTypeEnum`はいずれかに、関数が受け取る引数の数を超えています。</span><span class="sxs-lookup"><span data-stu-id="aebdc-112">ELEMENT_TYPE_FNPTR: The number of type parameters contained in the `ICorDebugTypeEnum` will be one greater than the number of arguments accepted by the function.</span></span> <span data-ttu-id="aebdc-113">含まれる最初の型パラメーター、`ICorDebugTypeEnum`関数の戻り値の型であり、その後の型パラメーターは関数のパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="aebdc-113">The first type parameter contained in the `ICorDebugTypeEnum` is the return type for the function, and the subsequent type parameters are the function's parameters.</span></span>  
  
-   <span data-ttu-id="aebdc-114">ELEMENT_TYPE_ARRAY、インポートする場合、ELEMENT_TYPE_BYREF、または ELEMENT_TYPE_PTR: 1 つの型パラメーターが返されます。</span><span class="sxs-lookup"><span data-stu-id="aebdc-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR: One type parameter will be returned.</span></span> <span data-ttu-id="aebdc-115">たとえば、次の型は、配列型など`int32[]`、`EnumerateTypeParameters`が返されます、`ICorDebugTypeEnum`を表すオブジェクトを格納している`int32`です。</span><span class="sxs-lookup"><span data-stu-id="aebdc-115">For example, if the type is an array type such as `int32[]`,`EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains an object representing `int32`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aebdc-116">要件</span><span class="sxs-lookup"><span data-stu-id="aebdc-116">Requirements</span></span>  
 <span data-ttu-id="aebdc-117">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="aebdc-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aebdc-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aebdc-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aebdc-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aebdc-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aebdc-120">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aebdc-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

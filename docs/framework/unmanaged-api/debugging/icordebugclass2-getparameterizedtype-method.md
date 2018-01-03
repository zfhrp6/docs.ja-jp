---
title: "ICorDebugClass2::GetParameterizedType メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass2.GetParameterizedType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass2::GetParameterizedType
helpviewer_keywords:
- GetParameterizedType method [.NET Framework debugging]
- ICorDebugClass2::GetParameterizedType method [.NET Framework debugging]
ms.assetid: 94b591c4-9302-4af2-a510-089496afb036
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9cbb755bd8f52482f7eece6e9d236f29cadc419
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugclass2getparameterizedtype-method"></a><span data-ttu-id="5b150-102">ICorDebugClass2::GetParameterizedType メソッド</span><span class="sxs-lookup"><span data-stu-id="5b150-102">ICorDebugClass2::GetParameterizedType Method</span></span>
<span data-ttu-id="5b150-103">このクラスの型宣言を取得します。</span><span class="sxs-lookup"><span data-stu-id="5b150-103">Gets the type declaration for this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b150-104">構文</span><span class="sxs-lookup"><span data-stu-id="5b150-104">Syntax</span></span>  
  
```  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5b150-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5b150-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="5b150-106">[in]このクラスの要素の型を指定する CorElementType 列挙型の値: この ICorDebugClass2 が値型を表している場合、ELEMENT_TYPE_VALUETYPE にこの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="5b150-106">[in] A value of the CorElementType enumeration that specifies the element type for this class: Set this value to ELEMENT_TYPE_VALUETYPE if this ICorDebugClass2 represents a value type.</span></span> <span data-ttu-id="5b150-107">この場合は、この値を ELEMENT_TYPE_CLASS に設定します。`ICorDebugClass2`複合型を表します。</span><span class="sxs-lookup"><span data-stu-id="5b150-107">Set this value to ELEMENT_TYPE_CLASS if this `ICorDebugClass2` represents a complex type.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="5b150-108">[in]型がジェネリックの場合、型パラメーターの数。</span><span class="sxs-lookup"><span data-stu-id="5b150-108">[in] The number of type parameters, if the type is generic.</span></span> <span data-ttu-id="5b150-109">型パラメーター (ある場合) の数は、クラスに必要な数と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b150-109">The number of type parameters (if any) must match the number required by the class.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="5b150-110">[in]型パラメーターを表す ICorDebugType オブジェクトを指し示すそれぞれが、ポインターの配列。</span><span class="sxs-lookup"><span data-stu-id="5b150-110">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type parameter.</span></span> <span data-ttu-id="5b150-111">クラスが非ジェネリックの場合は、この値が null です。</span><span class="sxs-lookup"><span data-stu-id="5b150-111">If the class is non-generic, this value is null.</span></span>  
  
 `ppType`  
 <span data-ttu-id="5b150-112">[out]アドレスへのポインター、`ICorDebugType`型宣言を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5b150-112">[out] A pointer to the address of an `ICorDebugType` object that represents the type declaration.</span></span> <span data-ttu-id="5b150-113">このオブジェクトは、<xref:System.Type>マネージ コード内のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5b150-113">This object is equivalent to a <xref:System.Type> object in managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b150-114">コメント</span><span class="sxs-lookup"><span data-stu-id="5b150-114">Remarks</span></span>  
 <span data-ttu-id="5b150-115">場合は、クラスは、非ジェネリックでは、型パラメーターが存在しない場合`GetParameterizedType`クラスに対応するランタイム型のオブジェクトを取得するだけです。</span><span class="sxs-lookup"><span data-stu-id="5b150-115">If the class is non-generic, that is, if it has no type parameters, `GetParameterizedType` simply gets the runtime type object corresponding to the class.</span></span> <span data-ttu-id="5b150-116">`elementType`クラスの正しい要素の型にパラメーターを設定する必要があります: ELEMENT_TYPE_VALUETYPE クラスが値型である場合はそれ以外の場合、ELEMENT_TYPE_CLASS です。</span><span class="sxs-lookup"><span data-stu-id="5b150-116">The `elementType` parameter should be set to the correct element type for the class: ELEMENT_TYPE_VALUETYPE if the class is a value type; otherwise, ELEMENT_TYPE_CLASS.</span></span>  
  
 <span data-ttu-id="5b150-117">クラスが型パラメーターを受け入れる場合 (たとえば、 `ArrayList<T>`)、使用することができます`GetParameterizedType`など型のインスタンスの型のオブジェクトを構築するために`ArrayList<int>`です。</span><span class="sxs-lookup"><span data-stu-id="5b150-117">If the class accepts type parameters (for example, `ArrayList<T>`), you can use `GetParameterizedType` to construct a type object for an instantiated type such as `ArrayList<int>`.</span></span>  
  
## <a name="background-information"></a><span data-ttu-id="5b150-118">背景情報</span><span class="sxs-lookup"><span data-stu-id="5b150-118">Background Information</span></span>  
 <span data-ttu-id="5b150-119">.NET Framework バージョン 1.0 および 1.1 では、メタデータ内のすべての型を直接実行中のプロセス内の型にマップすることもできます。</span><span class="sxs-lookup"><span data-stu-id="5b150-119">In the .NET Framework versions 1.0 and 1.1, every type in the metadata could be directly mapped to a type in the running process.</span></span> <span data-ttu-id="5b150-120">したがって、メタデータの種類と、ランタイム型は、実行中のプロセスで 1 つの表現必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b150-120">Thus, a metadata type and a runtime type had a single representation in the running process.</span></span> <span data-ttu-id="5b150-121">ただし、メタデータ内の 1 つのジェネリック型は、実行中のプロセスでの型の複数の異なるインスタンスにマップできます。</span><span class="sxs-lookup"><span data-stu-id="5b150-121">However, one generic type in metadata can be mapped to many different instantiations of the type in the running process.</span></span> <span data-ttu-id="5b150-122">たとえば、メタデータ型`SortedList<K,V>`にマップできます`SortedList<String, EmployeeRecord>`、 `SortedList<Int32, String>`、`SortedList<String,Array<Int32>>`のようにします。</span><span class="sxs-lookup"><span data-stu-id="5b150-122">For example, the metadata type `SortedList<K,V>` can map to `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`, and so on.</span></span> <span data-ttu-id="5b150-123">したがって、型のインスタンス化を処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b150-123">Thus, you need a way to handle type instantiation.</span></span>  
  
 <span data-ttu-id="5b150-124">.NET Framework version 2.0 では、`ICorDebugType`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="5b150-124">The .NET Framework version 2.0 introduces the `ICorDebugType` interface.</span></span> <span data-ttu-id="5b150-125">ジェネリック型の場合、`ICorDebugClass`または`ICorDebugClass2`オブジェクトがインスタンス化されていない型を表します (`SortedList<K,V>`)、および`ICorDebugType`オブジェクトは、さまざまなインスタンス化された型を表します。</span><span class="sxs-lookup"><span data-stu-id="5b150-125">For a generic type, an `ICorDebugClass` or `ICorDebugClass2` object represents the uninstantiated type (`SortedList<K,V>`), and an `ICorDebugType` object represents the various instantiated types.</span></span> <span data-ttu-id="5b150-126">指定された、`ICorDebugClass`または`ICorDebugClass2`オブジェクトを作成することができます、`ICorDebugType`オブジェクトを呼び出すことによって、インスタンス化、`ICorDebugClass2::GetParameterizedType`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="5b150-126">Given an `ICorDebugClass` or `ICorDebugClass2` object, you can create an `ICorDebugType` object for any instantiation by calling the `ICorDebugClass2::GetParameterizedType` method.</span></span> <span data-ttu-id="5b150-127">作成することも、 `ICorDebugType` Int32 などの単純型または非ジェネリック型のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5b150-127">You can also create an `ICorDebugType` object for a simple type, such as Int32, or for a non-generic type.</span></span>  
  
 <span data-ttu-id="5b150-128">導入、`ICorDebugType`型の実行時の概念を表現するオブジェクトが、API 全体に影響します。</span><span class="sxs-lookup"><span data-stu-id="5b150-128">The introduction of the `ICorDebugType` object to represent the run-time notion of a type has a ripple effect throughout the API.</span></span> <span data-ttu-id="5b150-129">かかっていた関数、`ICorDebugClass`または`ICorDebugClass2`オブジェクトまたはであっても、`CorElementType`値を汎用化されて、`ICorDebugType`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5b150-129">Functions that previously took an `ICorDebugClass` or `ICorDebugClass2` object or even a `CorElementType` value are generalized to take an `ICorDebugType` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b150-130">必要条件</span><span class="sxs-lookup"><span data-stu-id="5b150-130">Requirements</span></span>  
 <span data-ttu-id="5b150-131">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5b150-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b150-132">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b150-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b150-133">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b150-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b150-134">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b150-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

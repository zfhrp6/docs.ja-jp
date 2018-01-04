---
title: "Put 関数 (アンマネージ API リファレンス)"
description: "Put 関数では、名前付きプロパティに新しい値を割り当てます。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Put
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Put
helpviewer_keywords: Put function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09d3edc74b34688d5cc36e688f634850cfb60910
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="put-function"></a><span data-ttu-id="ba25a-103">Put 関数</span><span class="sxs-lookup"><span data-stu-id="ba25a-103">Put function</span></span>
<span data-ttu-id="ba25a-104">新しい値を名前付きプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="ba25a-104">Sets a named property to a new value.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="ba25a-105">構文</span><span class="sxs-lookup"><span data-stu-id="ba25a-105">Syntax</span></span>  
  
```  
HRESULT Put (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
); 
```  

## <a name="parameters"></a><span data-ttu-id="ba25a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ba25a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="ba25a-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="ba25a-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="ba25a-108">[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="ba25a-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="ba25a-109">[in]プロパティの名前です。</span><span class="sxs-lookup"><span data-stu-id="ba25a-109">[in] The name of the property.</span></span> <span data-ttu-id="ba25a-110">このパラメーターを指定できません`null`です。</span><span class="sxs-lookup"><span data-stu-id="ba25a-110">This parameter cannot be `null`.</span></span>

`lFlags`  
<span data-ttu-id="ba25a-111">[in]予約されています。</span><span class="sxs-lookup"><span data-stu-id="ba25a-111">[in] Reserved.</span></span> <span data-ttu-id="ba25a-112">このパラメーターは、0 を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba25a-112">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="ba25a-113">[in]有効なポインター`VARIANT`新しいプロパティ値になります。</span><span class="sxs-lookup"><span data-stu-id="ba25a-113">[in] A pointer to a valid `VARIANT` that becomes the new property value.</span></span> <span data-ttu-id="ba25a-114">場合`pVal`は`null`を指すか、`VARIANT`型の`VT_NULL`、プロパティに設定`null`です。</span><span class="sxs-lookup"><span data-stu-id="ba25a-114">If `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`, the property is set to `null`.</span></span> 

`vtType`  
<span data-ttu-id="ba25a-115">[in]型`VARIANT`によって示される`pVal`です。</span><span class="sxs-lookup"><span data-stu-id="ba25a-115">[in] The type of `VARIANT` pointed to by `pVal`.</span></span> <span data-ttu-id="ba25a-116">参照してください、[解説](#remarks)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="ba25a-116">See the [Remarks](#remarks) section for more information.</span></span>
 

## <a name="return-value"></a><span data-ttu-id="ba25a-117">戻り値</span><span class="sxs-lookup"><span data-stu-id="ba25a-117">Return value</span></span>

<span data-ttu-id="ba25a-118">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="ba25a-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ba25a-119">定数</span><span class="sxs-lookup"><span data-stu-id="ba25a-119">Constant</span></span>  |<span data-ttu-id="ba25a-120">[値]</span><span class="sxs-lookup"><span data-stu-id="ba25a-120">Value</span></span>  |<span data-ttu-id="ba25a-121">説明</span><span class="sxs-lookup"><span data-stu-id="ba25a-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="ba25a-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="ba25a-122">0x80041001</span></span> | <span data-ttu-id="ba25a-123">一般的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ba25a-123">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ba25a-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ba25a-124">0x80041008</span></span> | <span data-ttu-id="ba25a-125">1 つまたは複数のパラメーターが有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="ba25a-125">One or more parameters are not valid.</span></span> |
|`WBEM_E_INVALID_PROPERTY_TYPE` | <span data-ttu-id="ba25a-126">0x8004102a</span><span class="sxs-lookup"><span data-stu-id="ba25a-126">0x8004102a</span></span> | <span data-ttu-id="ba25a-127">プロパティの型は認識されません。</span><span class="sxs-lookup"><span data-stu-id="ba25a-127">The property type is not recognized.</span></span> <span data-ttu-id="ba25a-128">クラスが既に存在する場合は、クラスのインスタンスを作成するときに、この値が返されます。</span><span class="sxs-lookup"><span data-stu-id="ba25a-128">This value is returned when creating class instances if the class already exists.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="ba25a-129">0x80041006</span><span class="sxs-lookup"><span data-stu-id="ba25a-129">0x80041006</span></span> | <span data-ttu-id="ba25a-130">操作を完了するのに十分なメモリがあります。</span><span class="sxs-lookup"><span data-stu-id="ba25a-130">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="ba25a-131">0x80041005</span><span class="sxs-lookup"><span data-stu-id="ba25a-131">0x80041005</span></span> | <span data-ttu-id="ba25a-132">インスタンス: ことを示します`pVal`を指す、`VARIANT`プロパティの型が正しくないのです。</span><span class="sxs-lookup"><span data-stu-id="ba25a-132">For instances: Indicates that `pVal` points to a `VARIANT` of an incorrect type for the property.</span></span> <br/> <span data-ttu-id="ba25a-133">クラス定義: プロパティは、親クラスに既に存在し、新しい COM 型が古い COM 型を異なる。</span><span class="sxs-lookup"><span data-stu-id="ba25a-133">For class definitions: The property already exists in the parent class, and the new COM type is different from the old COM type.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="ba25a-134">0</span><span class="sxs-lookup"><span data-stu-id="ba25a-134">0</span></span> | <span data-ttu-id="ba25a-135">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="ba25a-135">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="ba25a-136">コメント</span><span class="sxs-lookup"><span data-stu-id="ba25a-136">Remarks</span></span>

<span data-ttu-id="ba25a-137">この関数への呼び出しをラップする、 [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="ba25a-137">This function wraps a call to the [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="ba25a-138">この関数は常に、新しい現在のプロパティ値を上書きします。</span><span class="sxs-lookup"><span data-stu-id="ba25a-138">This function always overwrites the current property value with a new one.</span></span> <span data-ttu-id="ba25a-139">場合、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)はクラス定義、指す`Put`作成するか、プロパティ値を更新します。</span><span class="sxs-lookup"><span data-stu-id="ba25a-139">If the [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) points to a class definition, `Put` creates or updates the property value.</span></span> <span data-ttu-id="ba25a-140">ときに[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) CIM のインスタンスを指す`Put`更新プログラムのプロパティの値だけです。`Put`プロパティ値を作成できません。</span><span class="sxs-lookup"><span data-stu-id="ba25a-140">When [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) points to a CIM instance, `Put` updates the property value only; `Put` cannot create a property value.</span></span>

<span data-ttu-id="ba25a-141">`__CLASS`システム プロパティは書き込み可能なクラスの作成時に場合にのみは空白にできません。</span><span class="sxs-lookup"><span data-stu-id="ba25a-141">The `__CLASS` system property is only writable during class creation, when it may not be left blank.</span></span> <span data-ttu-id="ba25a-142">その他のすべてのシステム プロパティとは、読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="ba25a-142">All other system properties are read-only.</span></span>

<span data-ttu-id="ba25a-143">ユーザーは、アンダー スコア (「_ _」) で開始または終了する名前を持つプロパティを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="ba25a-143">A user cannot create properties with names that begin or end with an underscore ("_").</span></span> <span data-ttu-id="ba25a-144">これはシステム クラスとプロパティの予約されています。</span><span class="sxs-lookup"><span data-stu-id="ba25a-144">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="ba25a-145">プロパティ設定されている場合、`Put`親クラスで関数が存在する場合、プロパティの型が、親クラスの型と一致しませんしない限り、プロパティの既定値を変更します。</span><span class="sxs-lookup"><span data-stu-id="ba25a-145">If the property set by the `Put` function exists in the parent class, the default value of the property is changed unless the property type does not match the parent class type.</span></span> <span data-ttu-id="ba25a-146">プロパティが存在しないため、型の不一致は、プロパティが ceated を使用します。</span><span class="sxs-lookup"><span data-stu-id="ba25a-146">If the property does not exist and it is not a type mismatch, the property is ceated.</span></span>

<span data-ttu-id="ba25a-147">使用して、`vtType`パラメーター CIM クラス定義に新しいプロパティを作成する場合にのみと`pVal`は`null`を指すか、`VARIANT`型の`VT_NULL`します。</span><span class="sxs-lookup"><span data-stu-id="ba25a-147">Use the `vtType` parameter only when creating new properties in a CIM class definition and `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`.</span></span> <span data-ttu-id="ba25a-148">ここで、`vType`パラメーター プロパティの CIM 型を指定します。</span><span class="sxs-lookup"><span data-stu-id="ba25a-148">In this case, the `vType` parameter specifies the CIM type of the property.</span></span> <span data-ttu-id="ba25a-149">その他のすべてのケースで`vtType`0 にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba25a-149">In every other case, `vtType` must be 0.</span></span> <span data-ttu-id="ba25a-150">`vtType`基になるオブジェクトがインスタンスの場合も、0 をする必要があります (場合でも`Val`は`null`) ため、プロパティの型は固定され変更できません。</span><span class="sxs-lookup"><span data-stu-id="ba25a-150">`vtType` must also be 0 if the underlying object is an instance (even if `Val` is `null`) because the type of the property is fixed and cannot be changed.</span></span>   

## <a name="example"></a><span data-ttu-id="ba25a-151">例</span><span class="sxs-lookup"><span data-stu-id="ba25a-151">Example</span></span>

<span data-ttu-id="ba25a-152">例については、次を参照してください。、 [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="ba25a-152">For an example, see the [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ba25a-153">必要条件</span><span class="sxs-lookup"><span data-stu-id="ba25a-153">Requirements</span></span>  
 <span data-ttu-id="ba25a-154">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ba25a-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba25a-155">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ba25a-155">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ba25a-156">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ba25a-156">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba25a-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba25a-157">See also</span></span>  
[<span data-ttu-id="ba25a-158">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="ba25a-158">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

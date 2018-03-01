---
title: "PutMethod 関数 (アンマネージ API リファレンス)"
description: "PutMethod 関数では、メソッドを作成します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7e97ffcf44a738234f67d9736382c46c42e5b61e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="putmethod-function"></a><span data-ttu-id="a4ff7-103">PutMethod 関数</span><span class="sxs-lookup"><span data-stu-id="a4ff7-103">PutMethod function</span></span>
<span data-ttu-id="a4ff7-104">メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="a4ff7-105">構文</span><span class="sxs-lookup"><span data-stu-id="a4ff7-105">Syntax</span></span>  
  
```  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a><span data-ttu-id="a4ff7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a4ff7-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="a4ff7-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="a4ff7-108">[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="a4ff7-109">[in]作成する方法の名前。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-109">[in] The name of the method to create.</span></span> 

`lFlags`  
<span data-ttu-id="a4ff7-110">[in]予約されています。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-110">[in] Reserved.</span></span> <span data-ttu-id="a4ff7-111">このパラメーターは、0 を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="a4ff7-112">[in]コピーへのポインター、 [_parameters システム クラス](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx)を格納している、`in`メソッドのパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-112">[in] A pointer to a copy of the [__Parameters system class](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="a4ff7-113">場合、このパラメーターは無視されます 'éý'`null`です。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="a4ff7-114">[in] コピーへのポインター、 [_parameters システム クラス](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx)を格納している、`out`メソッドのパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-114">[in]  A pointer to a copy of the [__Parameters system class](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="a4ff7-115">場合、このパラメーターは無視されます 'éý'`null`です。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-115">This parameter is ignored if set to `null`.</span></span>
 

## <a name="return-value"></a><span data-ttu-id="a4ff7-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="a4ff7-116">Return value</span></span>

<span data-ttu-id="a4ff7-117">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a4ff7-118">定数</span><span class="sxs-lookup"><span data-stu-id="a4ff7-118">Constant</span></span>  |<span data-ttu-id="a4ff7-119">[値]</span><span class="sxs-lookup"><span data-stu-id="a4ff7-119">Value</span></span>  |<span data-ttu-id="a4ff7-120">説明</span><span class="sxs-lookup"><span data-stu-id="a4ff7-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a4ff7-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a4ff7-121">0x80041008</span></span> | <span data-ttu-id="a4ff7-122">1 つまたは複数のパラメーターが有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="a4ff7-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="a4ff7-123">0x80041043</span></span> | <span data-ttu-id="a4ff7-124">`[in, out]`メソッド パラメーターの両方で指定された、 *pInSignature*と*pOutSignature*オブジェクトが別の修飾子を持ちます。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="a4ff7-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="a4ff7-125">0x80041036</span></span> | <span data-ttu-id="a4ff7-126">メソッド パラメーターには、指定が不足して、 **ID**修飾子です。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="a4ff7-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="a4ff7-127">0x80041038</span></span> | <span data-ttu-id="a4ff7-128">メソッドのパラメーターに割り当てられている ID の系列が連続するか、0 から始まっていません。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="a4ff7-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="a4ff7-129">0x80041039</span></span> | <span data-ttu-id="a4ff7-130">メソッドの戻り値は、 **ID**修飾子です。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="a4ff7-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="a4ff7-131">0x80041034</span></span> | <span data-ttu-id="a4ff7-132">親クラスからの既存のメソッド名を再利用しようとしましたが、シグネチャが一致しませんでした。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="a4ff7-133">0</span><span class="sxs-lookup"><span data-stu-id="a4ff7-133">0</span></span> | <span data-ttu-id="a4ff7-134">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="a4ff7-135">コメント</span><span class="sxs-lookup"><span data-stu-id="a4ff7-135">Remarks</span></span>

<span data-ttu-id="a4ff7-136">この関数への呼び出しをラップする、 [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-136">This function wraps a call to the [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="a4ff7-137">場合にのみ、このメソッドの呼び出しがサポート`ptr`CIM クラス定義です。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="a4ff7-138">メソッドの操作からは使用できない[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) CIM インスタンスを指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-138">Method manipulation is not available from [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) pointers that point to CIM instances.</span></span>

<span data-ttu-id="a4ff7-139">ユーザーは、名前にアンダー スコアで開始または終了をメソッドを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="a4ff7-140">これはシステム クラスとプロパティの予約されています。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="a4ff7-141">メソッドで、`in`と`out`パラメーターがプロパティとして記載されている[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) objects.</span></span>

<span data-ttu-id="a4ff7-142">`[in/out]`によって示される両方のオブジェクトに同じプロパティを追加することでパラメーターを定義することができます、`pInSignature`と`pOutSignature`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="a4ff7-143">この場合、プロパティが同じ**ID**修飾子の値。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="a4ff7-144">内の各プロパティ、 [_parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx)以外のオブジェクトをクラス`ReturnValue`必要があります、 **ID**修飾子、パラメーターの順序を識別する 0 から始まる数値です。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-144">Each property in a [__Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="a4ff7-145">ない 2 つのパラメーターと同じであることができます**ID**値、およびなし**ID**値をスキップすることができます。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="a4ff7-146">いずれかの条件が発生した場合、`PutMethod`関数が返される`WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`です。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="a4ff7-147">例</span><span class="sxs-lookup"><span data-stu-id="a4ff7-147">Example</span></span>

<span data-ttu-id="a4ff7-148">例については、次を参照してください。、 [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-148">For an example, see the [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a4ff7-149">必要条件</span><span class="sxs-lookup"><span data-stu-id="a4ff7-149">Requirements</span></span>  
 <span data-ttu-id="a4ff7-150">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a4ff7-150">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4ff7-151">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a4ff7-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a4ff7-152">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a4ff7-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4ff7-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4ff7-153">See also</span></span>  
[<span data-ttu-id="a4ff7-154">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="a4ff7-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

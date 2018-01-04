---
title: "Get 関数 (アンマネージ API リファレンス)"
description: "Get 関数は、指定されたプロパティ値を取得します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Get
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Get
helpviewer_keywords: Get function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 69312030689ab1b87e3aadd040395f06e1c94ac8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="get-function"></a><span data-ttu-id="477f7-103">Get 関数</span><span class="sxs-lookup"><span data-stu-id="477f7-103">Get function</span></span>
<span data-ttu-id="477f7-104">存在する場合は、指定されたプロパティ値を取得します。</span><span class="sxs-lookup"><span data-stu-id="477f7-104">Retrieves the specified property value if it exists.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="477f7-105">構文</span><span class="sxs-lookup"><span data-stu-id="477f7-105">Syntax</span></span>  
  
```  
HRESULT Get (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
); 
```  

## <a name="parameters"></a><span data-ttu-id="477f7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="477f7-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="477f7-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="477f7-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="477f7-108">[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="477f7-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="477f7-109">[in]プロパティの名前です。</span><span class="sxs-lookup"><span data-stu-id="477f7-109">[in] The name of the property.</span></span>

<span data-ttu-id="477f7-110">`lFlags`[in]予約されています。</span><span class="sxs-lookup"><span data-stu-id="477f7-110">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="477f7-111">このパラメーターは、0 を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="477f7-111">This parameter must be 0.</span></span>

<span data-ttu-id="477f7-112">`pVal`[out]関数が正常に返された場合の値が含まれています、`wszName`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="477f7-112">`pVal` [out] If the function returns successfully, contains the value of the `wszName` property.</span></span> <span data-ttu-id="477f7-113">`pval`引数には、正しい型および修飾子の値が割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="477f7-113">The `pval` argument is assigned the correct type and value for the qualifier.</span></span>

<span data-ttu-id="477f7-114">`pvtType`[out]関数が正常に返された場合は、 [CIM 型の定数](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx)プロパティの型を示すです。</span><span class="sxs-lookup"><span data-stu-id="477f7-114">`pvtType` [out] If the function returns successfully, contains a [CIM-type constant](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) that indicates the property type.</span></span> <span data-ttu-id="477f7-115">その値にはあります`null`です。</span><span class="sxs-lookup"><span data-stu-id="477f7-115">Its value can also be `null`.</span></span> 

<span data-ttu-id="477f7-116">`plFlavor`[out]関数が正常に返された場合は、プロパティの原点に関する情報を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="477f7-116">`plFlavor` [out] If the function returns successfully, receives information about the origin of the property.</span></span> <span data-ttu-id="477f7-117">その値を指定できます`null`、またはいずれかで定義されている次の WBEM_FLAVOR_TYPE 定数の*WbemCli.h*ヘッダー ファイル。</span><span class="sxs-lookup"><span data-stu-id="477f7-117">Its value can be `null`, or one of the following WBEM_FLAVOR_TYPE constants defined in the *WbemCli.h* header file:</span></span> 

|<span data-ttu-id="477f7-118">定数</span><span class="sxs-lookup"><span data-stu-id="477f7-118">Constant</span></span>  |<span data-ttu-id="477f7-119">[値]</span><span class="sxs-lookup"><span data-stu-id="477f7-119">Value</span></span>  |<span data-ttu-id="477f7-120">説明</span><span class="sxs-lookup"><span data-stu-id="477f7-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="477f7-121">0x40</span><span class="sxs-lookup"><span data-stu-id="477f7-121">0x40</span></span> | <span data-ttu-id="477f7-122">プロパティは、標準のシステム プロパティです。</span><span class="sxs-lookup"><span data-stu-id="477f7-122">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="477f7-123">0x20</span><span class="sxs-lookup"><span data-stu-id="477f7-123">0x20</span></span> | <span data-ttu-id="477f7-124">クラスの: このプロパティは、親クラスから継承します。</span><span class="sxs-lookup"><span data-stu-id="477f7-124">For a class: The property is inherited from the parent class.</span></span> </br> <span data-ttu-id="477f7-125">インスタンス: プロパティは、親クラスから継承されたときに変更されていないインスタンスがします。</span><span class="sxs-lookup"><span data-stu-id="477f7-125">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="477f7-126">0</span><span class="sxs-lookup"><span data-stu-id="477f7-126">0</span></span> | <span data-ttu-id="477f7-127">クラスの: プロパティが、派生クラスに所属します。</span><span class="sxs-lookup"><span data-stu-id="477f7-127">For a class: The property belongs to the derived class.</span></span> </br> <span data-ttu-id="477f7-128">インスタンス:; のインスタンスによって、プロパティが変更されました。値が指定された、または修飾子が追加または変更します。</span><span class="sxs-lookup"><span data-stu-id="477f7-128">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="return-value"></a><span data-ttu-id="477f7-129">戻り値</span><span class="sxs-lookup"><span data-stu-id="477f7-129">Return value</span></span>

<span data-ttu-id="477f7-130">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="477f7-130">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="477f7-131">定数</span><span class="sxs-lookup"><span data-stu-id="477f7-131">Constant</span></span>  |<span data-ttu-id="477f7-132">[値]</span><span class="sxs-lookup"><span data-stu-id="477f7-132">Value</span></span>  |<span data-ttu-id="477f7-133">説明</span><span class="sxs-lookup"><span data-stu-id="477f7-133">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="477f7-134">0x80041001</span><span class="sxs-lookup"><span data-stu-id="477f7-134">0x80041001</span></span> | <span data-ttu-id="477f7-135">一般的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="477f7-135">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="477f7-136">0x80041008</span><span class="sxs-lookup"><span data-stu-id="477f7-136">0x80041008</span></span> | <span data-ttu-id="477f7-137">1 つまたは複数のパラメーターが有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="477f7-137">One or more parameters are not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="477f7-138">0x80041002</span><span class="sxs-lookup"><span data-stu-id="477f7-138">0x80041002</span></span> | <span data-ttu-id="477f7-139">指定したプロパティは見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="477f7-139">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="477f7-140">0x80041006</span><span class="sxs-lookup"><span data-stu-id="477f7-140">0x80041006</span></span> | <span data-ttu-id="477f7-141">操作を完了するのに十分なメモリがあります。</span><span class="sxs-lookup"><span data-stu-id="477f7-141">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="477f7-142">0</span><span class="sxs-lookup"><span data-stu-id="477f7-142">0</span></span> | <span data-ttu-id="477f7-143">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="477f7-143">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="477f7-144">コメント</span><span class="sxs-lookup"><span data-stu-id="477f7-144">Remarks</span></span>

<span data-ttu-id="477f7-145">この関数への呼び出しをラップする、 [IWbemClassObject::Get](https://msdn.microsoft.com/library/aa391442(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="477f7-145">This function wraps a call to the [IWbemClassObject::Get](https://msdn.microsoft.com/library/aa391442(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="477f7-146">`Get`関数では、システムのプロパティを返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="477f7-146">The `Get` function can also return system properties.</span></span>

<span data-ttu-id="477f7-147">`pVal`引数には、正しい型および修飾子と COM の値が割り当てられている[VariantInit](https://msdn.microsoft.com/library/ms221402(v=vs.85).aspx)関数</span><span class="sxs-lookup"><span data-stu-id="477f7-147">The `pVal` argument is assigned the correct type and value for the qualifier and the COM [VariantInit](https://msdn.microsoft.com/library/ms221402(v=vs.85).aspx) function</span></span>

## <a name="requirements"></a><span data-ttu-id="477f7-148">必要条件</span><span class="sxs-lookup"><span data-stu-id="477f7-148">Requirements</span></span>  
 <span data-ttu-id="477f7-149">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="477f7-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="477f7-150">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="477f7-150">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="477f7-151">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="477f7-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="477f7-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="477f7-152">See also</span></span>  
[<span data-ttu-id="477f7-153">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="477f7-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

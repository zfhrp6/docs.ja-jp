---
title: "GetPropertyQualifierSet 関数 (アンマネージ API リファレンス)"
description: "GetPropertyQualifierSet 関数では、プロパティの設定、修飾子を取得します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetPropertyQualifierSet
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetPropertyQualifierSet
helpviewer_keywords: GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bd8abdb34f37273e469bdf5fc659b261bb2b9304
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="getpropertyqualifierset-function"></a><span data-ttu-id="f64dd-103">GetPropertyQualifierSet 関数</span><span class="sxs-lookup"><span data-stu-id="f64dd-103">GetPropertyQualifierSet function</span></span>
<span data-ttu-id="f64dd-104">特定のプロパティの設定、修飾子を取得します。</span><span class="sxs-lookup"><span data-stu-id="f64dd-104">Retrieves the qualifier set for a particular property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="f64dd-105">構文</span><span class="sxs-lookup"><span data-stu-id="f64dd-105">Syntax</span></span>  
  
```  
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="f64dd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f64dd-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f64dd-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="f64dd-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f64dd-108">[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="f64dd-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethod`  
<span data-ttu-id="f64dd-109">[in]プロパティ名。</span><span class="sxs-lookup"><span data-stu-id="f64dd-109">[in] The property  name.</span></span> <span data-ttu-id="f64dd-110">`wszProperty`有効なをポイントする必要があります`LPCWSTR`です。</span><span class="sxs-lookup"><span data-stu-id="f64dd-110">`wszProperty` must point to a valid `LPCWSTR`.</span></span> 

`ppQualSet`  
<span data-ttu-id="f64dd-111">[out]プロパティの修飾子にアクセスできるようにするインターフェイス ポインターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="f64dd-111">[out] Receives the interface pointer that allows access to the qualifiers of the property.</span></span> <span data-ttu-id="f64dd-112">`ppQualSet` として `null` を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="f64dd-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="f64dd-113">かどうかは、エラーが発生し、新しいオブジェクトが返されない、ポインターが指すように設定`null`です。</span><span class="sxs-lookup"><span data-stu-id="f64dd-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="f64dd-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="f64dd-114">Return value</span></span>

<span data-ttu-id="f64dd-115">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="f64dd-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f64dd-116">定数</span><span class="sxs-lookup"><span data-stu-id="f64dd-116">Constant</span></span>  |<span data-ttu-id="f64dd-117">値</span><span class="sxs-lookup"><span data-stu-id="f64dd-117">Value</span></span>  |<span data-ttu-id="f64dd-118">説明</span><span class="sxs-lookup"><span data-stu-id="f64dd-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="f64dd-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="f64dd-119">0x80041001</span></span> | <span data-ttu-id="f64dd-120">一般的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f64dd-120">There has been a general failure.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="f64dd-121">0x80041002</span><span class="sxs-lookup"><span data-stu-id="f64dd-121">0x80041002</span></span> | <span data-ttu-id="f64dd-122">指定されたメソッドが存在しません。</span><span class="sxs-lookup"><span data-stu-id="f64dd-122">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f64dd-123">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f64dd-123">0x80041006</span></span> | <span data-ttu-id="f64dd-124">操作を完了するのに十分なメモリがあります。</span><span class="sxs-lookup"><span data-stu-id="f64dd-124">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f64dd-125">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f64dd-125">0x80041008</span></span> | <span data-ttu-id="f64dd-126">パラメーターが`null`です。</span><span class="sxs-lookup"><span data-stu-id="f64dd-126">A parameter is `null`.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | <span data-ttu-id="f64dd-127">0x80041030</span><span class="sxs-lookup"><span data-stu-id="f64dd-127">0x80041030</span></span> | <span data-ttu-id="f64dd-128">関数は、システム プロパティの修飾子を取得しようとします。</span><span class="sxs-lookup"><span data-stu-id="f64dd-128">The function attempts to get qualifiers of a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f64dd-129">0</span><span class="sxs-lookup"><span data-stu-id="f64dd-129">0</span></span> | <span data-ttu-id="f64dd-130">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="f64dd-130">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f64dd-131">コメント</span><span class="sxs-lookup"><span data-stu-id="f64dd-131">Remarks</span></span>

<span data-ttu-id="f64dd-132">この関数への呼び出しをラップする、 [IWbemClassObject::GetPropertyQualifierSet](https://msdn.microsoft.com/library/aa391450(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f64dd-132">This function wraps a call to the [IWbemClassObject::GetPropertyQualifierSet](https://msdn.microsoft.com/library/aa391450(v=vs.85).aspx) method.</span></span> 

<span data-ttu-id="f64dd-133">この関数に対する呼び出しがサポートされるは、現在のオブジェクトが、CIM クラスの定義である場合にのみです。</span><span class="sxs-lookup"><span data-stu-id="f64dd-133">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="f64dd-134">メソッドの操作では使用できません[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) CIM インスタンスを指す ponters です。</span><span class="sxs-lookup"><span data-stu-id="f64dd-134">Method manipulation is not available for [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters that point to CIM instances.</span></span>

<span data-ttu-id="f64dd-135">各メソッドには、独自の修飾子があるため、 [IWbemQualifierSet ポインター](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)により、呼び出し元を追加、編集、またはこれらの修飾子を削除します。</span><span class="sxs-lookup"><span data-stu-id="f64dd-135">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) lets the caller add, edit, or delete these qualifiers.</span></span>

<span data-ttu-id="f64dd-136">システムのプロパティに修飾子があるないため、関数を返します`WBEM_E_SYSTEM_PROPERTY`を取得しようとすると、 [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)システム プロパティへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f64dd-136">Because system properties have no qualifiers, the function returns `WBEM_E_SYSTEM_PROPERTY` if you attempt to obtain a [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) pointer for a system property.</span></span>

## <a name="requirements"></a><span data-ttu-id="f64dd-137">要件</span><span class="sxs-lookup"><span data-stu-id="f64dd-137">Requirements</span></span>  
<span data-ttu-id="f64dd-138">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f64dd-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f64dd-139">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f64dd-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f64dd-140">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f64dd-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f64dd-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="f64dd-141">See also</span></span>  
[<span data-ttu-id="f64dd-142">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f64dd-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

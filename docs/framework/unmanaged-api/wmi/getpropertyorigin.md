---
title: "GetPropertyOrigin 関数 (Unmnaged API リファレンス)"
description: "GetPropertyOrigin 関数では、プロパティが宣言されるクラスを決定します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetPropertyOrigin
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetPropertyOrigin
helpviewer_keywords: GetPropertyOrigin function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 68df29e88b41cb12d002913d5bbd42050395d871
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="getpropertyorigin-function"></a><span data-ttu-id="6dedc-103">GetPropertyOrigin 関数</span><span class="sxs-lookup"><span data-stu-id="6dedc-103">GetPropertyOrigin function</span></span>
<span data-ttu-id="6dedc-104">プロパティが宣言されるクラスを決定します。</span><span class="sxs-lookup"><span data-stu-id="6dedc-104">Determines the class in which a property is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="6dedc-105">構文</span><span class="sxs-lookup"><span data-stu-id="6dedc-105">Syntax</span></span>  
  
```  
HRESULT GetPropertyOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a><span data-ttu-id="6dedc-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dedc-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="6dedc-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="6dedc-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="6dedc-108">[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="6dedc-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="6dedc-109">[in]所有するクラスが要求されているオブジェクトのプロパティの名前。</span><span class="sxs-lookup"><span data-stu-id="6dedc-109">[in] The name of the property for the object whose owning class is being requested.</span></span> 

`pstrClassName`  
<span data-ttu-id="6dedc-110">[out]プロパティを所有するクラスの名前を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="6dedc-110">[out] Receives the name of the class that owns the property.</span></span>

## <a name="return-value"></a><span data-ttu-id="6dedc-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dedc-111">Return value</span></span>

<span data-ttu-id="6dedc-112">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="6dedc-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6dedc-113">定数</span><span class="sxs-lookup"><span data-stu-id="6dedc-113">Constant</span></span>  |<span data-ttu-id="6dedc-114">値</span><span class="sxs-lookup"><span data-stu-id="6dedc-114">Value</span></span>  |<span data-ttu-id="6dedc-115">説明</span><span class="sxs-lookup"><span data-stu-id="6dedc-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="6dedc-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="6dedc-116">0x80041001</span></span> | <span data-ttu-id="6dedc-117">一般的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="6dedc-117">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="6dedc-118">0x80041002</span><span class="sxs-lookup"><span data-stu-id="6dedc-118">0x80041002</span></span> | <span data-ttu-id="6dedc-119">指定したプロパティは見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="6dedc-119">The specified property was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="6dedc-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="6dedc-120">0x80041008</span></span> | <span data-ttu-id="6dedc-121">パラメーターが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="6dedc-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="6dedc-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="6dedc-122">0x80041006</span></span> | <span data-ttu-id="6dedc-123">操作を完了するのに十分なメモリがあります。</span><span class="sxs-lookup"><span data-stu-id="6dedc-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="6dedc-124">0</span><span class="sxs-lookup"><span data-stu-id="6dedc-124">0</span></span> | <span data-ttu-id="6dedc-125">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="6dedc-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="6dedc-126">コメント</span><span class="sxs-lookup"><span data-stu-id="6dedc-126">Remarks</span></span>

<span data-ttu-id="6dedc-127">この関数への呼び出しをラップする、 [IWbemClassObject::GetPropertyOrigin](https://msdn.microsoft.com/library/aa391449(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="6dedc-127">This function wraps a call to the [IWbemClassObject::GetPropertyOrigin](https://msdn.microsoft.com/library/aa391449(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="6dedc-128">クラスは、1 つまたは複数の基底クラスからプロパティを継承することができます、ために、開発者は多くの場合に特定のメソッドが定義されているプロパティを確認します。</span><span class="sxs-lookup"><span data-stu-id="6dedc-128">Because a class can inherit properties from one or more base classes, developers often want to determine the property in which a given method is defined.</span></span>

<span data-ttu-id="6dedc-129">`pstrClassName`パラメーターは、有効なを指していない必要があります`BSTR`ため、これは、関数が呼び出される前に、`out`パラメーターです。 この関数が返された後に、ポインターが割り当て解除されません。</span><span class="sxs-lookup"><span data-stu-id="6dedc-129">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="6dedc-130">要件</span><span class="sxs-lookup"><span data-stu-id="6dedc-130">Requirements</span></span>  
<span data-ttu-id="6dedc-131">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6dedc-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dedc-132">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6dedc-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="6dedc-133">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6dedc-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dedc-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="6dedc-134">See also</span></span>  
[<span data-ttu-id="6dedc-135">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="6dedc-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

---
title: "NextMethod 関数 (アンマネージ API リファレンス)"
description: "NextMethod 関数では、列挙体の次のメソッドを取得します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: NextMethod
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: NextMethod
helpviewer_keywords: NextMethod function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b886b3ecbd1d5b5b8d212846b2bd8291fa43909
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="nextmethod-function"></a><span data-ttu-id="7f737-103">NextMethod 関数</span><span class="sxs-lookup"><span data-stu-id="7f737-103">NextMethod function</span></span>
<span data-ttu-id="7f737-104">呼び出しで始まる列挙体の次のメソッドを取得[BeginMethodEnumeration](beginmethodenumeration.md)です。</span><span class="sxs-lookup"><span data-stu-id="7f737-104">Retrieves the next method in an enumeration that begins with a call to [BeginMethodEnumeration](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="7f737-105">構文</span><span class="sxs-lookup"><span data-stu-id="7f737-105">Syntax</span></span>  
  
```  
HRESULT NextMethod (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature   
); 
```  

## <a name="parameters"></a><span data-ttu-id="7f737-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7f737-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="7f737-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="7f737-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="7f737-108">[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="7f737-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lFlags`  
<span data-ttu-id="7f737-109">[in]予約されています。</span><span class="sxs-lookup"><span data-stu-id="7f737-109">[in] Reserved.</span></span> <span data-ttu-id="7f737-110">このパラメーターは、0 を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f737-110">This parameter must be 0.</span></span>

`pName`  
<span data-ttu-id="7f737-111">[out]指すポインター`null`呼び出しの前にします。</span><span class="sxs-lookup"><span data-stu-id="7f737-111">[out] A pointer that points to `null` prior to the call.</span></span> <span data-ttu-id="7f737-112">ときに、関数からの新しいアドレス`BSTR`メソッド名を格納しています。</span><span class="sxs-lookup"><span data-stu-id="7f737-112">When the function returns, the address of a new `BSTR` that contains the method name.</span></span> 

`ppSignatureIn`  
<span data-ttu-id="7f737-113">[out]ポインターを受け取るポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)を格納している、`in`メソッドのパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="7f737-113">[out] A pointer that receives a pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) that contains the `in` parameters for the method.</span></span> 

`ppSignatureOut`  
<span data-ttu-id="7f737-114">[out]ポインターを受け取るポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)を格納している、`out`メソッドのパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="7f737-114">[out] A pointer that receives a pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) that contains the `out` parameters for the method.</span></span> 

## <a name="return-value"></a><span data-ttu-id="7f737-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="7f737-115">Return value</span></span>

<span data-ttu-id="7f737-116">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="7f737-116">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7f737-117">定数</span><span class="sxs-lookup"><span data-stu-id="7f737-117">Constant</span></span>  |<span data-ttu-id="7f737-118">[値]</span><span class="sxs-lookup"><span data-stu-id="7f737-118">Value</span></span>  |<span data-ttu-id="7f737-119">説明</span><span class="sxs-lookup"><span data-stu-id="7f737-119">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="7f737-120">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="7f737-120">0x8004101d</span></span> | <span data-ttu-id="7f737-121">呼び出しが入っていなかった、 [ `BeginEnumeration` ](beginenumeration.md)関数。</span><span class="sxs-lookup"><span data-stu-id="7f737-121">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="7f737-122">0</span><span class="sxs-lookup"><span data-stu-id="7f737-122">0</span></span> | <span data-ttu-id="7f737-123">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="7f737-123">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="7f737-124">0x40005</span><span class="sxs-lookup"><span data-stu-id="7f737-124">0x40005</span></span> | <span data-ttu-id="7f737-125">列挙には、プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="7f737-125">There are no more properties in the enumeration.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="7f737-126">コメント</span><span class="sxs-lookup"><span data-stu-id="7f737-126">Remarks</span></span>

<span data-ttu-id="7f737-127">この関数への呼び出しをラップする、 [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="7f737-127">This function wraps a call to the [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="7f737-128">呼び出し元が呼び出しによって列挙のシーケンスを開始、 [BeginMethodEnumeration](beginmethodenumeration.md)関数、および関数が戻るまで [NextMethod] 関数を呼び出す`WBEM_S_NO_MORE_DATA`です。</span><span class="sxs-lookup"><span data-stu-id="7f737-128">The caller begins the enumeration sequence by calling the [BeginMethodEnumeration](beginmethodenumeration.md) function, and then calls the [NextMethod] function until the function returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="7f737-129">必要に応じて、呼び出し元が完了すると、シーケンスを呼び出して[EndMethodEnumeration](endmethodenumeration.md)です。</span><span class="sxs-lookup"><span data-stu-id="7f737-129">Optionally, the caller finishes the sequence by calling [EndMethodEnumeration](endmethodenumeration.md).</span></span> <span data-ttu-id="7f737-130">呼び出し元が呼び出すことで列挙体を早期終了可能性があります[EndMethodEnumeration](endmethodenumeration.md)いつでもできます。</span><span class="sxs-lookup"><span data-stu-id="7f737-130">The caller may terminate the enumeration early by calling [EndMethodEnumeration](endmethodenumeration.md) at any time.</span></span>

## <a name="example"></a><span data-ttu-id="7f737-131">例</span><span class="sxs-lookup"><span data-stu-id="7f737-131">Example</span></span>

<span data-ttu-id="7f737-132">C++ の例では、次を参照してください。、 [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="7f737-132">For a C++ example, see the [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7f737-133">必要条件</span><span class="sxs-lookup"><span data-stu-id="7f737-133">Requirements</span></span>  
 <span data-ttu-id="7f737-134">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7f737-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f737-135">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="7f737-135">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="7f737-136">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7f737-136">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f737-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f737-137">See also</span></span>  
[<span data-ttu-id="7f737-138">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="7f737-138">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

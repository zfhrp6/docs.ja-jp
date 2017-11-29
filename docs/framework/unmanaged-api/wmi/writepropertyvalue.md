---
title: "WritePropertyValue 関数 (アンマネージ API リファレンス)"
description: "WritePropertyValue 関数は、プロパティにバイトを書き込みます。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: WritePropertyValue
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: WritePropertyValue
helpviewer_keywords: WritePropertyValue function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 26337a13ab9840b79c253d4af2d84a10e70877c5
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="e8f2a-103">WritePropertyValue 関数</span><span class="sxs-lookup"><span data-stu-id="e8f2a-103">WritePropertyValue function</span></span>
<span data-ttu-id="e8f2a-104">プロパティのハンドルによって識別されたプロパティに指定したバイト数を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="e8f2a-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="e8f2a-105">構文</span><span class="sxs-lookup"><span data-stu-id="e8f2a-105">Syntax</span></span>  
  
```  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a><span data-ttu-id="e8f2a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e8f2a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e8f2a-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="e8f2a-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="e8f2a-108">[in]ポインター、 [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="e8f2a-108">[in] A pointer to an [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) instance.</span></span>

`lHandle`  
<span data-ttu-id="e8f2a-109">[in]このプロパティを識別するハンドルを格納する整数。</span><span class="sxs-lookup"><span data-stu-id="e8f2a-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="e8f2a-110">呼び出すことによって、ハンドルを取得できる、 [GetPropertyHandle](getpropertyhandle.md)関数。</span><span class="sxs-lookup"><span data-stu-id="e8f2a-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>   

`lNumBytes`  
<span data-ttu-id="e8f2a-111">[in]プロパティに書き込まれるバイト数。</span><span class="sxs-lookup"><span data-stu-id="e8f2a-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="e8f2a-112">参照してください、[解説](#remarks)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="e8f2a-112">See the [Remarks](#remarks) section for more information.</span></span>

`pHandle`   
<span data-ttu-id="e8f2a-113">[out]データを格納するバイト配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e8f2a-113">[out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="e8f2a-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="e8f2a-114">Return value</span></span>

<span data-ttu-id="e8f2a-115">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="e8f2a-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e8f2a-116">定数</span><span class="sxs-lookup"><span data-stu-id="e8f2a-116">Constant</span></span>  |<span data-ttu-id="e8f2a-117">値</span><span class="sxs-lookup"><span data-stu-id="e8f2a-117">Value</span></span>  |<span data-ttu-id="e8f2a-118">説明</span><span class="sxs-lookup"><span data-stu-id="e8f2a-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e8f2a-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e8f2a-119">0x80041008</span></span> | <span data-ttu-id="e8f2a-120">パラメーターが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="e8f2a-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="e8f2a-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="e8f2a-121">0x80041005</span></span> | <span data-ttu-id="e8f2a-122">型の不一致が発生しました。</span><span class="sxs-lookup"><span data-stu-id="e8f2a-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e8f2a-123">0</span><span class="sxs-lookup"><span data-stu-id="e8f2a-123">0</span></span> | <span data-ttu-id="e8f2a-124">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="e8f2a-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e8f2a-125">コメント</span><span class="sxs-lookup"><span data-stu-id="e8f2a-125">Remarks</span></span>

<span data-ttu-id="e8f2a-126">この関数への呼び出しをラップする、 [IWbemClassObject::WritePropertyValue](https://msdn.microsoft.com/library/aa391783(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e8f2a-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](https://msdn.microsoft.com/library/aa391783(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="e8f2a-127">使用してこの関数の文字列とすべて他の非`DWORD`または非-`QWORD`データ。</span><span class="sxs-lookup"><span data-stu-id="e8f2a-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="e8f2a-128">プロパティ値は文字列ではない、`lNumBytes`指定されたプロパティの型の適切なデータ サイズにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8f2a-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="e8f2a-129">文字列プロパティの値の`lNumBytes`長さにする必要があります (バイト単位) で指定した文字列および文字列の偶数の長さ (バイト単位) の必要があり、null 終端文字の後にします。</span><span class="sxs-lookup"><span data-stu-id="e8f2a-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="e8f2a-130">要件</span><span class="sxs-lookup"><span data-stu-id="e8f2a-130">Requirements</span></span>  
<span data-ttu-id="e8f2a-131">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e8f2a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8f2a-132">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e8f2a-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e8f2a-133">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e8f2a-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8f2a-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="e8f2a-134">See also</span></span>  
[<span data-ttu-id="e8f2a-135">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="e8f2a-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

---
title: "GetMethodOrigin 関数 (アンマネージ API リファレンス)"
description: "GetMethodOrigin 関数では、メソッドが宣言されるクラスを決定します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetMethodOrigin
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetMethodOrigin
helpviewer_keywords: GetMethodOrigin function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7982ef2f272173e89434b64a4c296a2ce963594e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="0b964-103">GetMethodOrigin 関数</span><span class="sxs-lookup"><span data-stu-id="0b964-103">GetMethodOrigin function</span></span>
<span data-ttu-id="0b964-104">メソッドが宣言されるクラスを決定します。</span><span class="sxs-lookup"><span data-stu-id="0b964-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="0b964-105">構文</span><span class="sxs-lookup"><span data-stu-id="0b964-105">Syntax</span></span>  
  
```  
HRESULT GetMethodOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a><span data-ttu-id="0b964-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0b964-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="0b964-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="0b964-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="0b964-108">[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="0b964-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="0b964-109">[in]所有するクラスが要求されているオブジェクトのメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="0b964-109">[in] The name of the method for the object whose owning class is being requested.</span></span> 

`pstrClassName`  
<span data-ttu-id="0b964-110">[out]メソッドを所有するクラスの名前を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="0b964-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="0b964-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="0b964-111">Return value</span></span>

<span data-ttu-id="0b964-112">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="0b964-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0b964-113">定数</span><span class="sxs-lookup"><span data-stu-id="0b964-113">Constant</span></span>  |<span data-ttu-id="0b964-114">値</span><span class="sxs-lookup"><span data-stu-id="0b964-114">Value</span></span>  |<span data-ttu-id="0b964-115">説明</span><span class="sxs-lookup"><span data-stu-id="0b964-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="0b964-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="0b964-116">0x80041002</span></span> | <span data-ttu-id="0b964-117">指定されたメソッドが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="0b964-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="0b964-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="0b964-118">0x80041008</span></span> | <span data-ttu-id="0b964-119">1 つまたは複数のパラメーターが有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="0b964-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="0b964-120">0</span><span class="sxs-lookup"><span data-stu-id="0b964-120">0</span></span> | <span data-ttu-id="0b964-121">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="0b964-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="0b964-122">コメント</span><span class="sxs-lookup"><span data-stu-id="0b964-122">Remarks</span></span>

<span data-ttu-id="0b964-123">この関数への呼び出しをラップする、 [IWbemClassObject::GetMethodOrigin](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="0b964-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="0b964-124">クラスは、1 つまたは複数の基底クラスからメソッドを継承することができます、ために、開発者は多くの場合に特定のメソッドが定義されているクラスを確認します。</span><span class="sxs-lookup"><span data-stu-id="0b964-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="0b964-125">`pstrClassName`パラメーターは、有効なを指していない必要があります`BSTR`ため、これは、関数が呼び出される前に、`out`パラメーターです。 この関数が返された後に、ポインターが割り当て解除されません。</span><span class="sxs-lookup"><span data-stu-id="0b964-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="0b964-126">要件</span><span class="sxs-lookup"><span data-stu-id="0b964-126">Requirements</span></span>  
<span data-ttu-id="0b964-127">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0b964-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b964-128">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="0b964-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="0b964-129">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0b964-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b964-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b964-130">See also</span></span>  
[<span data-ttu-id="0b964-131">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="0b964-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

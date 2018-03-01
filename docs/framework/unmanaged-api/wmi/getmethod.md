---
title: "GetMethod 関数 (アンマネージ API リファレンス)"
description: "GetMethod 関数では、メソッドに関する情報を取得します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f22a2dfa7aae411cac960cbad2017718df8057e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getmethod-function"></a><span data-ttu-id="aca76-103">GetMethod 関数</span><span class="sxs-lookup"><span data-stu-id="aca76-103">GetMethod function</span></span>
<span data-ttu-id="aca76-104">指定したメソッドに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="aca76-104">Retrieves information about the specified method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="aca76-105">構文</span><span class="sxs-lookup"><span data-stu-id="aca76-105">Syntax</span></span>  
  
```  
HRESULT GetMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
); 
```  

## <a name="parameters"></a><span data-ttu-id="aca76-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aca76-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="aca76-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="aca76-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="aca76-108">[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="aca76-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="aca76-109">[in]メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="aca76-109">[in] The method name.</span></span> <span data-ttu-id="aca76-110">このパラメーターを指定できません`null`し、有効なをポイントする必要があります`LPCWSTR`です。</span><span class="sxs-lookup"><span data-stu-id="aca76-110">This parameter cannot be `null` and must point to a valid `LPCWSTR`.</span></span>

`lFlags`  
<span data-ttu-id="aca76-111">[in]予約されています。</span><span class="sxs-lookup"><span data-stu-id="aca76-111">[in] Reserved.</span></span> <span data-ttu-id="aca76-112">このパラメーターは、0 を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aca76-112">This parameter must be 0.</span></span>

`ppInSignature`   
<span data-ttu-id="aca76-113">[out]アドレスへのポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)メソッドへの paramteers を説明するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="aca76-113">[out] A pointer to the address of an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance that describes the in paramteers to the method.</span></span> <span data-ttu-id="aca76-114">設定されている場合、このパラメーターは無視されます`null`です。</span><span class="sxs-lookup"><span data-stu-id="aca76-114">This parameter is ignored if it is set to `null`.</span></span> 

`ppOutSignature`  
<span data-ttu-id="aca76-115">[out]アドレスへのポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)メソッドに out パラメーターを説明するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="aca76-115">[out] A pointer to the address of an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance that describes the out parameters to the method.</span></span> <span data-ttu-id="aca76-116">設定されている場合、このパラメーターは無視されます`null`です。</span><span class="sxs-lookup"><span data-stu-id="aca76-116">This parameter is ignored if it is set to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="aca76-117">戻り値</span><span class="sxs-lookup"><span data-stu-id="aca76-117">Return value</span></span>

<span data-ttu-id="aca76-118">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="aca76-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="aca76-119">定数</span><span class="sxs-lookup"><span data-stu-id="aca76-119">Constant</span></span>  |<span data-ttu-id="aca76-120">[値]</span><span class="sxs-lookup"><span data-stu-id="aca76-120">Value</span></span>  |<span data-ttu-id="aca76-121">説明</span><span class="sxs-lookup"><span data-stu-id="aca76-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="aca76-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="aca76-122">0x80041002</span></span> | <span data-ttu-id="aca76-123">指定したプロパティは見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="aca76-123">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="aca76-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="aca76-124">0x80041006</span></span> | <span data-ttu-id="aca76-125">操作を完了するのに十分なメモリがあります。</span><span class="sxs-lookup"><span data-stu-id="aca76-125">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="aca76-126">0</span><span class="sxs-lookup"><span data-stu-id="aca76-126">0</span></span> | <span data-ttu-id="aca76-127">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aca76-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="aca76-128">コメント</span><span class="sxs-lookup"><span data-stu-id="aca76-128">Remarks</span></span>

<span data-ttu-id="aca76-129">この関数への呼び出しをラップする、 [IWbemClassObject::GetMethod](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="aca76-129">This function wraps a call to the [IWbemClassObject::GetMethod](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="aca76-130">Windows の管理を設定できる、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)へのポインター`null`メソッドに in パラメーターがあるない場合。</span><span class="sxs-lookup"><span data-stu-id="aca76-130">Windows Management can set the [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) pointer to `null` if the method has no in parameters.</span></span>

<span data-ttu-id="aca76-131">`ppInSignature`と`ppOutSignature`in および out パラメーターをそれぞれのプロパティとして、説明、`IWbemClassObject`システム クラスのインスタンス[_Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx)です。</span><span class="sxs-lookup"><span data-stu-id="aca76-131">In `ppInSignature` and `ppOutSignature` describe in and out parameters, respectively, as properties in a `IWbemClassObject` instance of the system class [_Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx).</span></span> <span data-ttu-id="aca76-132">指定したプロパティ`ppInsignature`は名前付き**Param***n*ここで、  *n*  (このようなメソッド シグネチャのパラメーターの位置は、として`Param1`、 `Param2`, などです。)。</span><span class="sxs-lookup"><span data-stu-id="aca76-132">The properties in `ppInsignature` are named **Param***n*, where *n* is the position of the parameter in the method signature (such as `Param1`, `Param2`, etc.).</span></span> <span data-ttu-id="aca76-133">指定したプロパティ`ppOutSignature`とも呼ば**Param***n*、および戻り値が名前付き**ReturnValue**です。</span><span class="sxs-lookup"><span data-stu-id="aca76-133">The properties in `ppOutSignature` are also named **Param***n*, and the return value is named **ReturnValue**.</span></span> <span data-ttu-id="aca76-134">例および詳細については、次を参照してください。 [IWbemClassObject::GetMethod メソッド](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx)です。</span><span class="sxs-lookup"><span data-stu-id="aca76-134">For more information and an example, see [IWbemClassObject::GetMethod method](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx).</span></span>

## <a name="requirements"></a><span data-ttu-id="aca76-135">必要条件</span><span class="sxs-lookup"><span data-stu-id="aca76-135">Requirements</span></span>  
<span data-ttu-id="aca76-136">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="aca76-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aca76-137">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="aca76-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="aca76-138">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="aca76-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aca76-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="aca76-139">See also</span></span>  
[<span data-ttu-id="aca76-140">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="aca76-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

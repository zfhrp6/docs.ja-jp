---
title: "QualifierSet_Put 関数 (アンマネージ API リファレンス)"
description: "QualifierSet_Put 関数は、名前付きの修飾子とその値を書き込みます。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_Put
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_Put
helpviewer_keywords: QualifierSet_Put function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7fdb6759d4e39ad9ab6bd6da2c2a0e2abfbe5d56
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetput-function"></a><span data-ttu-id="2b324-103">QualifierSet_Put 関数</span><span class="sxs-lookup"><span data-stu-id="2b324-103">QualifierSet_Put function</span></span>
<span data-ttu-id="2b324-104">名前付きの修飾子と値を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="2b324-104">Writes the named qualifier and value.</span></span> <span data-ttu-id="2b324-105">新しい修飾子には、同じ名前の前の値が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="2b324-105">The new qualifier overwrites the previous value of the same name.</span></span> <span data-ttu-id="2b324-106">修飾子が存在しない場合は作成されます。</span><span class="sxs-lookup"><span data-stu-id="2b324-106">If the qualifier does not exist, it is created.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="2b324-107">構文</span><span class="sxs-lookup"><span data-stu-id="2b324-107">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Put (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
); 
```  

## <a name="parameters"></a><span data-ttu-id="2b324-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2b324-108">Parameters</span></span>

`vFunc`   
<span data-ttu-id="2b324-109">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="2b324-109">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="2b324-110">[in]ポインター、 [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="2b324-110">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`wszName`   
<span data-ttu-id="2b324-111">[in]書き込む修飾子の名前。</span><span class="sxs-lookup"><span data-stu-id="2b324-111">[in] The name of the qualifier to write.</span></span>

<span data-ttu-id="2b324-112">`pVal`[in]有効なポインター`VARIANT`書き込む修飾子を格納しています。</span><span class="sxs-lookup"><span data-stu-id="2b324-112">`pVal` [in] A pointer to a valid `VARIANT` that contains the qualifier to write.</span></span> <span data-ttu-id="2b324-113">このパラメーターを指定できません`null`です。</span><span class="sxs-lookup"><span data-stu-id="2b324-113">This parameter cannot be `null`.</span></span>

<span data-ttu-id="2b324-114">`lFlavor`[in]この修飾子に必要な修飾子のフレーバーを定義する次の定数の 1 つ。</span><span class="sxs-lookup"><span data-stu-id="2b324-114">`lFlavor` [in] One of the following constants that defines the desired qualifier flavors for this qualifier.</span></span> <span data-ttu-id="2b324-115">既定値は`WBEM_FLAVOR_OVERRIDABLE`(0) です。</span><span class="sxs-lookup"><span data-stu-id="2b324-115">The default value is `WBEM_FLAVOR_OVERRIDABLE` (0).</span></span>

|<span data-ttu-id="2b324-116">定数</span><span class="sxs-lookup"><span data-stu-id="2b324-116">Constant</span></span>  |<span data-ttu-id="2b324-117">値</span><span class="sxs-lookup"><span data-stu-id="2b324-117">Value</span></span>  |<span data-ttu-id="2b324-118">説明</span><span class="sxs-lookup"><span data-stu-id="2b324-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | <span data-ttu-id="2b324-119">0</span><span class="sxs-lookup"><span data-stu-id="2b324-119">0</span></span> | <span data-ttu-id="2b324-120">修飾子は、派生クラスまたはインスタンスでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="2b324-120">The qualifier can be overridden in a derived class or instance.</span></span> <span data-ttu-id="2b324-121">**これは、既定値です。**</span><span class="sxs-lookup"><span data-stu-id="2b324-121">**This is the default value.**</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | <span data-ttu-id="2b324-122">1</span><span class="sxs-lookup"><span data-stu-id="2b324-122">1</span></span> | <span data-ttu-id="2b324-123">この修飾子は、インスタンスに反映されます。</span><span class="sxs-lookup"><span data-stu-id="2b324-123">The qualifier is propagated to instances.</span></span> |
| `WBEM_FLAVOR_GLAG_PROPAGATE_TO_DERIVED_CLASS` | <span data-ttu-id="2b324-124">2</span><span class="sxs-lookup"><span data-stu-id="2b324-124">2</span></span> | <span data-ttu-id="2b324-125">修飾子は、派生クラスに伝達されます。</span><span class="sxs-lookup"><span data-stu-id="2b324-125">The qualifier is propagated to derived classes.</span></span> |
| <span data-ttu-id="2b324-126">' WBEM_FLAVOR_NOT_OVERRIDABLE</span><span class="sxs-lookup"><span data-stu-id="2b324-126">\`WBEM_FLAVOR_NOT_OVERRIDABLE</span></span> | <span data-ttu-id="2b324-127">0x10</span><span class="sxs-lookup"><span data-stu-id="2b324-127">0x10</span></span> | <span data-ttu-id="2b324-128">この修飾子は、派生クラスまたはインスタンスではオーバーライドできません。</span><span class="sxs-lookup"><span data-stu-id="2b324-128">The qualifier cannot be overridden in a derived class or instance.</span></span> |
| <span data-ttu-id="2b324-129">' WBEM_FLAVOR_AMENDED</span><span class="sxs-lookup"><span data-stu-id="2b324-129">\`WBEM_FLAVOR_AMENDED</span></span> | <span data-ttu-id="2b324-130">0x80</span><span class="sxs-lookup"><span data-stu-id="2b324-130">0x80</span></span> | <span data-ttu-id="2b324-131">修飾子はローカライズされます。</span><span class="sxs-lookup"><span data-stu-id="2b324-131">The qualifier is localized.</span></span> |

## <a name="return-value"></a><span data-ttu-id="2b324-132">戻り値</span><span class="sxs-lookup"><span data-stu-id="2b324-132">Return value</span></span>

<span data-ttu-id="2b324-133">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="2b324-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2b324-134">定数</span><span class="sxs-lookup"><span data-stu-id="2b324-134">Constant</span></span>  |<span data-ttu-id="2b324-135">値</span><span class="sxs-lookup"><span data-stu-id="2b324-135">Value</span></span>  |<span data-ttu-id="2b324-136">説明</span><span class="sxs-lookup"><span data-stu-id="2b324-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | <span data-ttu-id="2b324-137">0x8004101f</span><span class="sxs-lookup"><span data-stu-id="2b324-137">0x8004101f</span></span> | <span data-ttu-id="2b324-138">指定する無効なが試行されました、**キー**することはできません、キー プロパティでの修飾子です。</span><span class="sxs-lookup"><span data-stu-id="2b324-138">There was an illegal attempt to specify the **Key** qualifier on a property that cannot be a key.</span></span> <span data-ttu-id="2b324-139">キーが指定されて om c; オブジェクトの定義はアセンブリと、インスタンスごとに変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="2b324-139">The keys are specified om tje c;ass definition for an object and cannot be altered on a per-instance basis.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2b324-140">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2b324-140">0x80041008</span></span> | <span data-ttu-id="2b324-141">パラメーターが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="2b324-141">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | <span data-ttu-id="2b324-142">0x80041029</span><span class="sxs-lookup"><span data-stu-id="2b324-142">0x80041029</span></span> | <span data-ttu-id="2b324-143">`pVal`パラメーターが正しい型ではありません。</span><span class="sxs-lookup"><span data-stu-id="2b324-143">The `pVal` parameter is not of a legal qualifier type.</span></span> |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | <span data-ttu-id="2b324-144">0x8004101a</span><span class="sxs-lookup"><span data-stu-id="2b324-144">0x8004101a</span></span> | <span data-ttu-id="2b324-145">呼び出すことはできません、`QualifierSet_Put`修飾子のメソッド オーバーライドの所有するオブジェクトが許可されていません。</span><span class="sxs-lookup"><span data-stu-id="2b324-145">It is not possible to call the `QualifierSet_Put` method on the qualifier because the owning object does not permit overrides.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="2b324-146">0</span><span class="sxs-lookup"><span data-stu-id="2b324-146">0</span></span> | <span data-ttu-id="2b324-147">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="2b324-147">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="2b324-148">コメント</span><span class="sxs-lookup"><span data-stu-id="2b324-148">Remarks</span></span>

<span data-ttu-id="2b324-149">この関数への呼び出しをラップする、 [IWbemQualifierSet::Put](https://msdn.microsoft.com/library/aa391871(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="2b324-149">This function wraps a call to the [IWbemQualifierSet::Put](https://msdn.microsoft.com/library/aa391871(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2b324-150">要件</span><span class="sxs-lookup"><span data-stu-id="2b324-150">Requirements</span></span>  
 <span data-ttu-id="2b324-151">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2b324-151">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b324-152">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="2b324-152">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2b324-153">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2b324-153">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b324-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b324-154">See also</span></span>  
[<span data-ttu-id="2b324-155">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="2b324-155">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

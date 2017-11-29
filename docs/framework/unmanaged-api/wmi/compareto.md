---
title: "CompareTo 関数 (アンマネージ API リファレンス)"
description: "CompareTo 関数では、別の WMI オブジェクトにオブジェクトを比較します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: CompareTo
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: CompareTo
helpviewer_keywords: CompareTo function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dacb1516bebfc73ae9e16b03f3755ab49382e571
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="compareto-function"></a><span data-ttu-id="5dca1-103">CompareTo 関数</span><span class="sxs-lookup"><span data-stu-id="5dca1-103">CompareTo function</span></span>
<span data-ttu-id="5dca1-104">別の Windows 管理オブジェクトにオブジェクトを比較します。</span><span class="sxs-lookup"><span data-stu-id="5dca1-104">Compares an object to another Windows management object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="5dca1-105">構文</span><span class="sxs-lookup"><span data-stu-id="5dca1-105">Syntax</span></span>  
  
```
HRESULT CompareTo (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo 
); 
```  

## <a name="parameters"></a><span data-ttu-id="5dca1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5dca1-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="5dca1-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="5dca1-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="5dca1-108">[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="5dca1-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`flags`  
<span data-ttu-id="5dca1-109">[in]比較検討するオブジェクトの特性を指定するフラグのビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="5dca1-109">[in] A bitwise combination of the flags that specify the object characteristics to consider for the comparison.</span></span> <span data-ttu-id="5dca1-110">参照してください、[解説](#remarks)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="5dca1-110">See the [Remarks](#remarks) section for more information.</span></span>

`pCompareTo`  

<span data-ttu-id="5dca1-111">[in]比較のオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="5dca1-111">[in] The object for comparison.</span></span> <span data-ttu-id="5dca1-112">`pcompareTo`有効な[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス; ことはできません`null`です。</span><span class="sxs-lookup"><span data-stu-id="5dca1-112">`pcompareTo` must be a valid [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance; it cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="5dca1-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="5dca1-113">Return value</span></span>

<span data-ttu-id="5dca1-114">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="5dca1-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5dca1-115">定数</span><span class="sxs-lookup"><span data-stu-id="5dca1-115">Constant</span></span>  |<span data-ttu-id="5dca1-116">値</span><span class="sxs-lookup"><span data-stu-id="5dca1-116">Value</span></span>  |<span data-ttu-id="5dca1-117">説明</span><span class="sxs-lookup"><span data-stu-id="5dca1-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="5dca1-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="5dca1-118">0x80041001</span></span> | <span data-ttu-id="5dca1-119">不明なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="5dca1-119">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5dca1-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5dca1-120">0x80041008</span></span> | <span data-ttu-id="5dca1-121">パラメーターが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="5dca1-121">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="5dca1-122">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="5dca1-122">0x8004101d</span></span> | <span data-ttu-id="5dca1-123">2 番目の呼び出しに`BeginEnumeration`せずに中間の呼び出しが行われた[ `EndEnumeration`](endenumeration.md)です。</span><span class="sxs-lookup"><span data-stu-id="5dca1-123">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="5dca1-124">0</span><span class="sxs-lookup"><span data-stu-id="5dca1-124">0</span></span> | <span data-ttu-id="5dca1-125">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="5dca1-125">The function call was successful.</span></span>  |
| `WBEM_S_DIFFERENT` | <span data-ttu-id="5dca1-126">0x40003</span><span class="sxs-lookup"><span data-stu-id="5dca1-126">0x40003</span></span> | <span data-ttu-id="5dca1-127">オブジェクトが異なるです。</span><span class="sxs-lookup"><span data-stu-id="5dca1-127">The objects are different.</span></span> |
| `WBEM_S_SAME` | <span data-ttu-id="5dca1-128">0</span><span class="sxs-lookup"><span data-stu-id="5dca1-128">0</span></span> | <span data-ttu-id="5dca1-129">オブジェクトは、比較フラグに基づいたものと同じです。</span><span class="sxs-lookup"><span data-stu-id="5dca1-129">The objects are the same based on the comparison flags.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="5dca1-130">コメント</span><span class="sxs-lookup"><span data-stu-id="5dca1-130">Remarks</span></span>

<span data-ttu-id="5dca1-131">この関数への呼び出しをラップする、 [IWbemClassObject::CompareTo](https://msdn.microsoft.com/library/aa391437(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="5dca1-131">This function wraps a call to the [IWbemClassObject::CompareTo](https://msdn.microsoft.com/library/aa391437(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="5dca1-132">フラグとして渡すことができる、`lEnumFlags`で引数が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。</span><span class="sxs-lookup"><span data-stu-id="5dca1-132">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> <span data-ttu-id="5dca1-133">次のフラグのビットごとの組み合わせを指定することによって、比較に関係する個々 の特性を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5dca1-133">You can specify the individual characteristics involved in the comparison by specifying a bitwise combination of the following flags:</span></span>

|<span data-ttu-id="5dca1-134">定数</span><span class="sxs-lookup"><span data-stu-id="5dca1-134">Constant</span></span>  |<span data-ttu-id="5dca1-135">値</span><span class="sxs-lookup"><span data-stu-id="5dca1-135">Value</span></span>  |<span data-ttu-id="5dca1-136">説明</span><span class="sxs-lookup"><span data-stu-id="5dca1-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | <span data-ttu-id="5dca1-137">2</span><span class="sxs-lookup"><span data-stu-id="5dca1-137">2</span></span> | <span data-ttu-id="5dca1-138">ソース (サーバーと、元の名前空間) を無視します。</span><span class="sxs-lookup"><span data-stu-id="5dca1-138">Ignore the source (the server and the namespace they came from).</span></span> |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | <span data-ttu-id="5dca1-139">1</span><span class="sxs-lookup"><span data-stu-id="5dca1-139">1</span></span> | <span data-ttu-id="5dca1-140">すべての修飾子を無視する (含む**キー**と**動的**)</span><span class="sxs-lookup"><span data-stu-id="5dca1-140">Ignore all qualifiers (including **Key** and **Dynamic**)</span></span> |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | <span data-ttu-id="5dca1-141">4</span><span class="sxs-lookup"><span data-stu-id="5dca1-141">4</span></span> | <span data-ttu-id="5dca1-142">プロパティの既定値を無視します。</span><span class="sxs-lookup"><span data-stu-id="5dca1-142">Ignore default values of properties.</span></span> <span data-ttu-id="5dca1-143">このフラグは、クラスの比較にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="5dca1-143">This flag only applies to comparison of classes.</span></span> |
| `WBEM_FLAG_IGNORE_FLAVOR` | <span data-ttu-id="5dca1-144">0x20</span><span class="sxs-lookup"><span data-stu-id="5dca1-144">0x20</span></span> | <span data-ttu-id="5dca1-145">修飾子のフレーバーを無視します。</span><span class="sxs-lookup"><span data-stu-id="5dca1-145">Ignore qualifier flavors.</span></span> <span data-ttu-id="5dca1-146">このフラグはまだ修飾子を考慮に入れたが伝達規則などのフレーバーの区別を無視、制限を上書きします。</span><span class="sxs-lookup"><span data-stu-id="5dca1-146">This flag still takes qualifiers into account, but ignores flavor distinctions such as propagation rules and override restrictions.</span></span> |
| `WBEM_FLAG_IGNORE_CASE` | <span data-ttu-id="5dca1-147">0x10</span><span class="sxs-lookup"><span data-stu-id="5dca1-147">0x10</span></span> | <span data-ttu-id="5dca1-148">文字列値の比較で大文字小文字を区別します。</span><span class="sxs-lookup"><span data-stu-id="5dca1-148">Ignore case in comparing string values.</span></span> <span data-ttu-id="5dca1-149">これには、文字列と修飾子の値の両方が適用されます。</span><span class="sxs-lookup"><span data-stu-id="5dca1-149">This applies both to strings and qualifier values.</span></span> <span data-ttu-id="5dca1-150">プロパティと修飾子の名前の比較は、このフラグが設定されているかに関係なく大文字小文字を区別は常にします。</span><span class="sxs-lookup"><span data-stu-id="5dca1-150">The comparison of property and qualifier names is always case-sensitive regardless of whether this flag is set.</span></span> |
| `WBEM_FLAG_IGNORE_CLASS` | <span data-ttu-id="5dca1-151">0x8</span><span class="sxs-lookup"><span data-stu-id="5dca1-151">0x8</span></span> | <span data-ttu-id="5dca1-152">比較対象となるオブジェクトが同じクラスのインスタンスであると仮定します。</span><span class="sxs-lookup"><span data-stu-id="5dca1-152">Assume that the objects being compared are instanes of the same class.</span></span> <span data-ttu-id="5dca1-153">そのため、このフラグは、インスタンスに関連する情報のみを比較します。</span><span class="sxs-lookup"><span data-stu-id="5dca1-153">Consequently, this flag compares instance-related information only.</span></span> <span data-ttu-id="5dca1-154">このフラグを使用して、パフォーマンスを最適化します。</span><span class="sxs-lookup"><span data-stu-id="5dca1-154">Use this flags to optimize performance.</span></span> <span data-ttu-id="5dca1-155">同じクラスのオブジェクトは場合、結果は定義されていません。</span><span class="sxs-lookup"><span data-stu-id="5dca1-155">If the objects are not of the same class, the results are undefined.</span></span> |

<span data-ttu-id="5dca1-156">または、次のように 1 つの複合フラグを指定できます。</span><span class="sxs-lookup"><span data-stu-id="5dca1-156">Or you can specify a single composite flag as follows:</span></span>

|<span data-ttu-id="5dca1-157">定数</span><span class="sxs-lookup"><span data-stu-id="5dca1-157">Constant</span></span>  |<span data-ttu-id="5dca1-158">値</span><span class="sxs-lookup"><span data-stu-id="5dca1-158">Value</span></span>  |<span data-ttu-id="5dca1-159">説明</span><span class="sxs-lookup"><span data-stu-id="5dca1-159">Description</span></span>  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | <span data-ttu-id="5dca1-160">0</span><span class="sxs-lookup"><span data-stu-id="5dca1-160">0</span></span> | <span data-ttu-id="5dca1-161">比較のすべての機能を検討してください。</span><span class="sxs-lookup"><span data-stu-id="5dca1-161">Consider all features in the comparison.</span></span> |

## <a name="requirements"></a><span data-ttu-id="5dca1-162">要件</span><span class="sxs-lookup"><span data-stu-id="5dca1-162">Requirements</span></span>  
 <span data-ttu-id="5dca1-163">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5dca1-163">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dca1-164">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5dca1-164">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5dca1-165">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5dca1-165">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dca1-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="5dca1-166">See also</span></span>  
[<span data-ttu-id="5dca1-167">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="5dca1-167">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

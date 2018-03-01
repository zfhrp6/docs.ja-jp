---
title: "GetNames 関数 (アンマネージ API リファレンス)"
description: "GetNames 関数では、オブジェクトのプロパティの名前を取得します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetNames
helpviewer_keywords:
- GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 80284900c318a3776168b781ce2e0e5e4a68f96d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getnames-function"></a><span data-ttu-id="5146a-103">GetNames 関数</span><span class="sxs-lookup"><span data-stu-id="5146a-103">GetNames function</span></span>
<span data-ttu-id="5146a-104">一部またはすべてのオブジェクトのプロパティの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="5146a-104">Retrieves either a subset or all of the names of the properties of an object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="5146a-105">構文</span><span class="sxs-lookup"><span data-stu-id="5146a-105">Syntax</span></span>  
  
```  
HRESULT GetNames (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
); 
```  

## <a name="parameters"></a><span data-ttu-id="5146a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5146a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="5146a-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="5146a-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="5146a-108">[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="5146a-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="5146a-109">[in]有効なポインター`LPCWSTR`フィルターの一部として動作する修飾子の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="5146a-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="5146a-110">詳細については、次を参照してください。、[解説](#remarks)セクションです。</span><span class="sxs-lookup"><span data-stu-id="5146a-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="5146a-111">このパラメーターは、`null` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="5146a-111">This parameter can be `null`.</span></span> 

`lFlags`  
<span data-ttu-id="5146a-112">[in]ビット フィールドの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="5146a-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="5146a-113">詳細については、次を参照してください。、[解説](#remarks)セクションです。</span><span class="sxs-lookup"><span data-stu-id="5146a-113">For more information, see the [Remarks](#remarks) section.</span></span>

`pQualifierValue`   
<span data-ttu-id="5146a-114">[in]有効なポインター`VARIANT`フィルター値に初期化された構造体。</span><span class="sxs-lookup"><span data-stu-id="5146a-114">[in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="5146a-115">このパラメーターは、`null` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="5146a-115">This parameter can be `null`.</span></span> 

`pstrNames`  
<span data-ttu-id="5146a-116">[out]A`SAFEARRAY`プロパティ名を格納する構造体。</span><span class="sxs-lookup"><span data-stu-id="5146a-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="5146a-117">項目で、このパラメーターは常にへのポインター`null`です。</span><span class="sxs-lookup"><span data-stu-id="5146a-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="5146a-118">参照してください、[解説](#remarks)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="5146a-118">See the [Remarks](#remarks) section for more information.</span></span> 

## <a name="return-value"></a><span data-ttu-id="5146a-119">戻り値</span><span class="sxs-lookup"><span data-stu-id="5146a-119">Return value</span></span>

<span data-ttu-id="5146a-120">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="5146a-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5146a-121">定数</span><span class="sxs-lookup"><span data-stu-id="5146a-121">Constant</span></span>  |<span data-ttu-id="5146a-122">[値]</span><span class="sxs-lookup"><span data-stu-id="5146a-122">Value</span></span>  |<span data-ttu-id="5146a-123">説明</span><span class="sxs-lookup"><span data-stu-id="5146a-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="5146a-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="5146a-124">0x80041001</span></span> | <span data-ttu-id="5146a-125">一般的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="5146a-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5146a-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5146a-126">0x80041008</span></span> | <span data-ttu-id="5146a-127">1 つまたは複数のパラメーターが有効でないか、フラグとパラメーターの組み合わせが正しくないが指定されました。</span><span class="sxs-lookup"><span data-stu-id="5146a-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5146a-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5146a-128">0x80041006</span></span> | <span data-ttu-id="5146a-129">操作を完了するのに十分なメモリがあります。</span><span class="sxs-lookup"><span data-stu-id="5146a-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="5146a-130">0</span><span class="sxs-lookup"><span data-stu-id="5146a-130">0</span></span> | <span data-ttu-id="5146a-131">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="5146a-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5146a-132">コメント</span><span class="sxs-lookup"><span data-stu-id="5146a-132">Remarks</span></span>

<span data-ttu-id="5146a-133">この関数への呼び出しをラップする、 [IWbemClassObject::GetNames](https://msdn.microsoft.com/library/aa391447(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="5146a-133">This function wraps a call to the [IWbemClassObject::GetNames](https://msdn.microsoft.com/library/aa391447(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="5146a-134">返される名前付きのフラグとパラメーターの組み合わせによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="5146a-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="5146a-135">たとえば、関数では、すべてのプロパティの名前またはキーのプロパティの名前のみを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="5146a-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="5146a-136">プライマリ フィルターがで指定された、`lFlags`パラメーター、およびその他のパラメーターは、これによって異なります。</span><span class="sxs-lookup"><span data-stu-id="5146a-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="5146a-137">フラグの値が`lFlags`ビット フィールドは、</span><span class="sxs-lookup"><span data-stu-id="5146a-137">The flag values in `lFlags` are bit fields</span></span>


<span data-ttu-id="5146a-138">フラグとして渡すことができる、`lEnumFlags`引数は、ビット フィールドで定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。</span><span class="sxs-lookup"><span data-stu-id="5146a-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="5146a-139">その他のグループから任意のフラグを使って各グループから 1 つのフラグを組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="5146a-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="5146a-140">ただし、同じグループにフラグは相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="5146a-140">However, flags from the same group are mutually exclusive.</span></span> 

| <span data-ttu-id="5146a-141">グループ 1 フラグ</span><span class="sxs-lookup"><span data-stu-id="5146a-141">Group 1 flags</span></span> |<span data-ttu-id="5146a-142">[値]</span><span class="sxs-lookup"><span data-stu-id="5146a-142">Value</span></span>  |<span data-ttu-id="5146a-143">説明</span><span class="sxs-lookup"><span data-stu-id="5146a-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="5146a-144">0</span><span class="sxs-lookup"><span data-stu-id="5146a-144">0</span></span> | <span data-ttu-id="5146a-145">すべてのプロパティ名を返します。</span><span class="sxs-lookup"><span data-stu-id="5146a-145">Return all property names.</span></span> <span data-ttu-id="5146a-146">`strQualifierName``pQualifierVal`使用されていません。</span><span class="sxs-lookup"><span data-stu-id="5146a-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="5146a-147">1</span><span class="sxs-lookup"><span data-stu-id="5146a-147">1</span></span> | <span data-ttu-id="5146a-148">指定した名前の修飾子を持つプロパティのみを返す、`strQualifierName`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="5146a-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="5146a-149">このフラグを使用する必要がありますを指定する`strQualifierName`です。</span><span class="sxs-lookup"><span data-stu-id="5146a-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="5146a-150">2</span><span class="sxs-lookup"><span data-stu-id="5146a-150">2</span></span> |  <span data-ttu-id="5146a-151">によって指定された名前の修飾子を持たない唯一のプロパティを返す、`strQualifierName`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="5146a-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="5146a-152">このフラグを使用する必要がありますを指定する`strQualifierName`です。</span><span class="sxs-lookup"><span data-stu-id="5146a-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="5146a-153">3</span><span class="sxs-lookup"><span data-stu-id="5146a-153">3</span></span> | <span data-ttu-id="5146a-154">によって指定された名前の修飾子を持つプロパティのみを返す、`wszQualifierName`パラメーターで指定されているのと同じ値が設定されても、`pQualifierVal`構造体。</span><span class="sxs-lookup"><span data-stu-id="5146a-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="5146a-155">このフラグを使用する場合、両方を指定する必要があります、`wszQualifierName`と`pQualifierValue`です。</span><span class="sxs-lookup"><span data-stu-id="5146a-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="5146a-156">グループ 2 フラグ</span><span class="sxs-lookup"><span data-stu-id="5146a-156">Group 2 flags</span></span> |<span data-ttu-id="5146a-157">[値]</span><span class="sxs-lookup"><span data-stu-id="5146a-157">Value</span></span>  |<span data-ttu-id="5146a-158">説明</span><span class="sxs-lookup"><span data-stu-id="5146a-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="5146a-159">0x4</span><span class="sxs-lookup"><span data-stu-id="5146a-159">0x4</span></span> | <span data-ttu-id="5146a-160">キーを定義するプロパティの名前のみを返します。</span><span class="sxs-lookup"><span data-stu-id="5146a-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="5146a-161">0x8</span><span class="sxs-lookup"><span data-stu-id="5146a-161">0x8</span></span> | <span data-ttu-id="5146a-162">戻り値のみプロパティ名オブジェクト参照であります。</span><span class="sxs-lookup"><span data-stu-id="5146a-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="5146a-163">フラグのグループ 3</span><span class="sxs-lookup"><span data-stu-id="5146a-163">Group 3 flags</span></span> |<span data-ttu-id="5146a-164">[値]</span><span class="sxs-lookup"><span data-stu-id="5146a-164">Value</span></span>  |<span data-ttu-id="5146a-165">説明</span><span class="sxs-lookup"><span data-stu-id="5146a-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="5146a-166">0x10</span><span class="sxs-lookup"><span data-stu-id="5146a-166">0x10</span></span> | <span data-ttu-id="5146a-167">最派生クラスに属しているプロパティ名のみが返されます。</span><span class="sxs-lookup"><span data-stu-id="5146a-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="5146a-168">親クラスからプロパティを除外します。</span><span class="sxs-lookup"><span data-stu-id="5146a-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="5146a-169">0x20</span><span class="sxs-lookup"><span data-stu-id="5146a-169">0x20</span></span> | <span data-ttu-id="5146a-170">親クラスに属しているプロパティ名のみが返されます。</span><span class="sxs-lookup"><span data-stu-id="5146a-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="5146a-171">0x30</span><span class="sxs-lookup"><span data-stu-id="5146a-171">0x30</span></span> | <span data-ttu-id="5146a-172">システムのプロパティの名前のみを返します。</span><span class="sxs-lookup"><span data-stu-id="5146a-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="5146a-173">0x40</span><span class="sxs-lookup"><span data-stu-id="5146a-173">0x40</span></span> | <span data-ttu-id="5146a-174">非システムのプロパティの名前のみを返します。</span><span class="sxs-lookup"><span data-stu-id="5146a-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="5146a-175">関数を常に割り当てる新しい`SAFEARRAY`を返す場合`WBEM_S_NO_ERROR`、および`pstrNames`は常に設定します。</span><span class="sxs-lookup"><span data-stu-id="5146a-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="5146a-176">指定したフィルターに一致するプロパティがない場合、返される配列要素がゼロことができます。</span><span class="sxs-lookup"><span data-stu-id="5146a-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="5146a-177">以外の場合、値が返されます場合`WBM_S_NO_ERROR`、新しい`SAFEARRAY`構造は返されません。</span><span class="sxs-lookup"><span data-stu-id="5146a-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>
 
## <a name="requirements"></a><span data-ttu-id="5146a-178">必要条件</span><span class="sxs-lookup"><span data-stu-id="5146a-178">Requirements</span></span>  
 <span data-ttu-id="5146a-179">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5146a-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5146a-180">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5146a-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5146a-181">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5146a-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5146a-182">関連項目</span><span class="sxs-lookup"><span data-stu-id="5146a-182">See also</span></span>  
[<span data-ttu-id="5146a-183">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="5146a-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

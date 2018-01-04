---
title: "QualifierSet_GetNames 関数 (アンマネージ API リファレンス)"
description: "QualifierSet_GetNames 関数は、オブジェクトまたはプロパティから修飾子の名前を取得します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_GetNames
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_GetNames
helpviewer_keywords: QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6077b448c2644f68d12679cf208ee921c2af119a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetgetnames-function"></a><span data-ttu-id="3cc88-103">QualifierSet_GetNames 関数</span><span class="sxs-lookup"><span data-stu-id="3cc88-103">QualifierSet_GetNames function</span></span>
<span data-ttu-id="3cc88-104">すべての修飾子のまたは現在のオブジェクトまたはプロパティから使用できる特定の修飾子の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="3cc88-104">Retrieves the names of all the qualifiers or of certain qualifiers that are available from the current object or property.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="3cc88-105">構文</span><span class="sxs-lookup"><span data-stu-id="3cc88-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
); 
```  

## <a name="parameters"></a><span data-ttu-id="3cc88-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3cc88-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="3cc88-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="3cc88-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="3cc88-108">[in]ポインター、 [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="3cc88-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`lFlags`   
<span data-ttu-id="3cc88-109">[in]次のフラグまたは列挙体に追加するには、どの名前を指定する値のいずれか。</span><span class="sxs-lookup"><span data-stu-id="3cc88-109">[in] One of the following flags or values that specifies which names to include in the enumeration.</span></span>

|<span data-ttu-id="3cc88-110">定数</span><span class="sxs-lookup"><span data-stu-id="3cc88-110">Constant</span></span>  |<span data-ttu-id="3cc88-111">[値]</span><span class="sxs-lookup"><span data-stu-id="3cc88-111">Value</span></span>  |<span data-ttu-id="3cc88-112">説明</span><span class="sxs-lookup"><span data-stu-id="3cc88-112">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="3cc88-113">0</span><span class="sxs-lookup"><span data-stu-id="3cc88-113">0</span></span> | <span data-ttu-id="3cc88-114">すべての修飾子の名前を返します。</span><span class="sxs-lookup"><span data-stu-id="3cc88-114">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="3cc88-115">0x10</span><span class="sxs-lookup"><span data-stu-id="3cc88-115">0x10</span></span> | <span data-ttu-id="3cc88-116">現在のプロパティまたはオブジェクトに特定の修飾子の名前のみを返します。</span><span class="sxs-lookup"><span data-stu-id="3cc88-116">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="3cc88-117">プロパティの: (オーバーライドを含む)、プロパティに特定の修飾子のみを返すし、クラス定義から伝達されたこれらの修飾子されません。</span><span class="sxs-lookup"><span data-stu-id="3cc88-117">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="3cc88-118">インスタンス: インスタンス固有の修飾子名のみが返されます。</span><span class="sxs-lookup"><span data-stu-id="3cc88-118">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="3cc88-119">クラスの: 派生クラス beiong に特定の修飾子のみを返します。</span><span class="sxs-lookup"><span data-stu-id="3cc88-119">For a class: Return only qualifiers specific to the class beiong derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="3cc88-120">0x20</span><span class="sxs-lookup"><span data-stu-id="3cc88-120">0x20</span></span> | <span data-ttu-id="3cc88-121">別のオブジェクトから修飾子の名前のみが反映される戻り値。</span><span class="sxs-lookup"><span data-stu-id="3cc88-121">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="3cc88-122">プロパティ: から返される修飾子のみが反映されるこのプロパティに、クラス定義と、プロパティ自体からです。</span><span class="sxs-lookup"><span data-stu-id="3cc88-122">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="3cc88-123">インスタンス: クラス定義からこれらの修飾子のみが反映される戻り値。</span><span class="sxs-lookup"><span data-stu-id="3cc88-123">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="3cc88-124">クラスの: 戻り値の修飾子名前だけが、親クラスから継承します。</span><span class="sxs-lookup"><span data-stu-id="3cc88-124">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

<span data-ttu-id="3cc88-125">`pstrNames`[out]新しい`SAFEARRAY`要求された名前を格納しています。</span><span class="sxs-lookup"><span data-stu-id="3cc88-125">`pstrNames` [out] A new `SAFEARRAY` that contains the requested names.</span></span> <span data-ttu-id="3cc88-126">配列には、0 の要素を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="3cc88-126">The array can have 0 elements.</span></span> <span data-ttu-id="3cc88-127">エラーが発生した場合、新しい`SAFEARRAY`は返されません。</span><span class="sxs-lookup"><span data-stu-id="3cc88-127">If an error occurs, a new `SAFEARRAY` is not returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="3cc88-128">戻り値</span><span class="sxs-lookup"><span data-stu-id="3cc88-128">Return value</span></span>

<span data-ttu-id="3cc88-129">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="3cc88-129">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="3cc88-130">定数</span><span class="sxs-lookup"><span data-stu-id="3cc88-130">Constant</span></span>  |<span data-ttu-id="3cc88-131">[値]</span><span class="sxs-lookup"><span data-stu-id="3cc88-131">Value</span></span>  |<span data-ttu-id="3cc88-132">説明</span><span class="sxs-lookup"><span data-stu-id="3cc88-132">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="3cc88-133">0x80041008</span><span class="sxs-lookup"><span data-stu-id="3cc88-133">0x80041008</span></span> | <span data-ttu-id="3cc88-134">パラメーターが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="3cc88-134">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="3cc88-135">0x80041006</span><span class="sxs-lookup"><span data-stu-id="3cc88-135">0x80041006</span></span> | <span data-ttu-id="3cc88-136">十分なメモリが新しい列挙体を開始します。</span><span class="sxs-lookup"><span data-stu-id="3cc88-136">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="3cc88-137">0</span><span class="sxs-lookup"><span data-stu-id="3cc88-137">0</span></span> | <span data-ttu-id="3cc88-138">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="3cc88-138">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="3cc88-139">コメント</span><span class="sxs-lookup"><span data-stu-id="3cc88-139">Remarks</span></span>

<span data-ttu-id="3cc88-140">この関数への呼び出しをラップする、 [IWbemQualifierSet::GetNames](https://msdn.microsoft.com/library/aa391868(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="3cc88-140">This function wraps a call to the [IWbemQualifierSet::GetNames](https://msdn.microsoft.com/library/aa391868(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="3cc88-141">修飾子の名前を取得すると、各修飾子名前でアクセスできますを呼び出して、 [QualifierSet_Get](qualifierset-get.md)関数。</span><span class="sxs-lookup"><span data-stu-id="3cc88-141">Once you've retrieved the qualifier names, you can access each qualifier by name by calling the [QualifierSet_Get](qualifierset-get.md) function.</span></span> 

<span data-ttu-id="3cc88-142">ゼロ修飾子があるためには、指定したオブジェクトのエラーではありませんで文字列の数`pstrNames`返された場合は 0 を指定する場合でも、この関数を返します`WBEM_S_NO_ERROR`です。</span><span class="sxs-lookup"><span data-stu-id="3cc88-142">It is not an error for a given object to have zero qualifiers, so the number of strings in `pstrNames` on return can be 0, even though the function returns `WBEM_S_NO_ERROR`.</span></span>

## <a name="requirements"></a><span data-ttu-id="3cc88-143">必要条件</span><span class="sxs-lookup"><span data-stu-id="3cc88-143">Requirements</span></span>  
 <span data-ttu-id="3cc88-144">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3cc88-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cc88-145">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="3cc88-145">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="3cc88-146">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3cc88-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cc88-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="3cc88-147">See also</span></span>  
[<span data-ttu-id="3cc88-148">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="3cc88-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

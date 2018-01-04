---
title: "QualifierSet_BeginEnumeration 関数 (アンマネージ API リファレンス)"
description: "QualifierSet_BeginEnumeration 関数では、オブジェクトの修飾子の列挙子をリセットします。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_BeginEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_BeginEnumeration
helpviewer_keywords: QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 440dde03f4ed138a33eb6f817723d7c5c74f6d46
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetbeginenumeration-function"></a><span data-ttu-id="c7328-103">QualifierSet_BeginEnumeration 関数</span><span class="sxs-lookup"><span data-stu-id="c7328-103">QualifierSet_BeginEnumeration function</span></span>
<span data-ttu-id="c7328-104">列挙体の先頭にオブジェクトの修飾子の列挙子をリセットします。</span><span class="sxs-lookup"><span data-stu-id="c7328-104">Resets an enumerator of the qualifiers of an object to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="c7328-105">構文</span><span class="sxs-lookup"><span data-stu-id="c7328-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="c7328-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c7328-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="c7328-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="c7328-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="c7328-108">[in]ポインター、 [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="c7328-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`lFlags`   
<span data-ttu-id="c7328-109">[in]フラグまたはで説明されている値のビットごとの組み合わせ、[解説](#remarks)セクションに含める列挙体の修飾子を指定します。</span><span class="sxs-lookup"><span data-stu-id="c7328-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that specifies the qualifiers to include in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="c7328-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="c7328-110">Return value</span></span>

<span data-ttu-id="c7328-111">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="c7328-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c7328-112">定数</span><span class="sxs-lookup"><span data-stu-id="c7328-112">Constant</span></span>  |<span data-ttu-id="c7328-113">[値]</span><span class="sxs-lookup"><span data-stu-id="c7328-113">Value</span></span>  |<span data-ttu-id="c7328-114">説明</span><span class="sxs-lookup"><span data-stu-id="c7328-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="c7328-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="c7328-115">0x80041008</span></span> | <span data-ttu-id="c7328-116">`lFlags`パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="c7328-116">The `lFlags` parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="c7328-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="c7328-117">0x8004101d</span></span> | <span data-ttu-id="c7328-118">2 番目の呼び出しに`QualifierSet_BeginEnumeration`せずに中間の呼び出しが行われた[ `QualifierSet_EndEnumeration`](qualifierset-endenumeration.md)です。</span><span class="sxs-lookup"><span data-stu-id="c7328-118">A second call to `QualifierSet_BeginEnumeration` was made without an intervening call to [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="c7328-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="c7328-119">0x80041006</span></span> | <span data-ttu-id="c7328-120">十分なメモリが新しい列挙体を開始します。</span><span class="sxs-lookup"><span data-stu-id="c7328-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="c7328-121">0</span><span class="sxs-lookup"><span data-stu-id="c7328-121">0</span></span> | <span data-ttu-id="c7328-122">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="c7328-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="c7328-123">コメント</span><span class="sxs-lookup"><span data-stu-id="c7328-123">Remarks</span></span>

<span data-ttu-id="c7328-124">この関数への呼び出しをラップする、 [IWbemQualifierSet::BeginEnumeration](https://msdn.microsoft.com/library/aa391861(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="c7328-124">This function wraps a call to the [IWbemQualifierSet::BeginEnumeration](https://msdn.microsoft.com/library/aa391861(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="c7328-125">すべてのオブジェクトに対する修飾子を列挙するには、最初の呼び出しの前にこのメソッドを呼び出す[QualifierSet_Next](qualifierset-next.md)です。</span><span class="sxs-lookup"><span data-stu-id="c7328-125">To enumerate all of the qualifiers on an object, this method must be called before the first call to [QualifierSet_Next](qualifierset-next.md).</span></span> <span data-ttu-id="c7328-126">修飾子が列挙される順序が指定した列挙体のバリアントを解除します。</span><span class="sxs-lookup"><span data-stu-id="c7328-126">The order in which qualifiers are enumerated is guaranteed to be invariant for a given enumeration.</span></span>

<span data-ttu-id="c7328-127">フラグとして渡すことができる、`lEnumFlags`で引数が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。</span><span class="sxs-lookup"><span data-stu-id="c7328-127">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>   

|<span data-ttu-id="c7328-128">定数</span><span class="sxs-lookup"><span data-stu-id="c7328-128">Constant</span></span>  |<span data-ttu-id="c7328-129">[値]</span><span class="sxs-lookup"><span data-stu-id="c7328-129">Value</span></span>  |<span data-ttu-id="c7328-130">説明</span><span class="sxs-lookup"><span data-stu-id="c7328-130">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="c7328-131">0</span><span class="sxs-lookup"><span data-stu-id="c7328-131">0</span></span> | <span data-ttu-id="c7328-132">すべての修飾子の名前を返します。</span><span class="sxs-lookup"><span data-stu-id="c7328-132">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="c7328-133">0x10</span><span class="sxs-lookup"><span data-stu-id="c7328-133">0x10</span></span> | <span data-ttu-id="c7328-134">現在のプロパティまたはオブジェクトに特定の修飾子の名前のみを返します。</span><span class="sxs-lookup"><span data-stu-id="c7328-134">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="c7328-135">プロパティの: (オーバーライドを含む)、プロパティに特定の修飾子のみを返すし、クラス定義から伝達されたこれらの修飾子されません。</span><span class="sxs-lookup"><span data-stu-id="c7328-135">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="c7328-136">インスタンス: インスタンス固有の修飾子名のみが返されます。</span><span class="sxs-lookup"><span data-stu-id="c7328-136">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="c7328-137">クラスの: 派生クラス beiong に特定の修飾子のみを返します。</span><span class="sxs-lookup"><span data-stu-id="c7328-137">For a class: Return only qualifiers specific to the class beiong derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="c7328-138">0x20</span><span class="sxs-lookup"><span data-stu-id="c7328-138">0x20</span></span> | <span data-ttu-id="c7328-139">別のオブジェクトから修飾子の名前のみが反映される戻り値。</span><span class="sxs-lookup"><span data-stu-id="c7328-139">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="c7328-140">プロパティ: から返される修飾子のみが反映されるこのプロパティに、クラス定義と、プロパティ自体からです。</span><span class="sxs-lookup"><span data-stu-id="c7328-140">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="c7328-141">インスタンス: クラス定義からこれらの修飾子のみが反映される戻り値。</span><span class="sxs-lookup"><span data-stu-id="c7328-141">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="c7328-142">クラスの: 戻り値の修飾子名前だけが、親クラスから継承します。</span><span class="sxs-lookup"><span data-stu-id="c7328-142">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="c7328-143">必要条件</span><span class="sxs-lookup"><span data-stu-id="c7328-143">Requirements</span></span>  
 <span data-ttu-id="c7328-144">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c7328-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7328-145">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c7328-145">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="c7328-146">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c7328-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7328-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7328-147">See also</span></span>  
[<span data-ttu-id="c7328-148">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="c7328-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

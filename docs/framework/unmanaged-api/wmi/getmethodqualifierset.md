---
title: "GetMethodQualifierSet 関数 (アンマネージ API リファレンス)"
description: "GetMethodQualifierSet 関数は、メソッドの修飾子のセットを取得します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetMethodQualifierSet
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetMethodQualifierSet
helpviewer_keywords: GetMethodQualifierSet function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2999bef31576cf2bc025868260c2b1782a9b69f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getmethodqualifierset-function"></a><span data-ttu-id="3d4a0-103">GetMethodQualifierSet 関数</span><span class="sxs-lookup"><span data-stu-id="3d4a0-103">GetMethodQualifierSet function</span></span>
<span data-ttu-id="3d4a0-104">特定のメソッドの設定、修飾子を取得します。</span><span class="sxs-lookup"><span data-stu-id="3d4a0-104">Retrieves the qualifier set for a particular method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="3d4a0-105">構文</span><span class="sxs-lookup"><span data-stu-id="3d4a0-105">Syntax</span></span>  
  
```  
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="3d4a0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3d4a0-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="3d4a0-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="3d4a0-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="3d4a0-108">[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="3d4a0-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethod`  
<span data-ttu-id="3d4a0-109">[in]メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="3d4a0-109">[in] The method  name.</span></span> <span data-ttu-id="3d4a0-110">`wszMethod`有効なをポイントする必要があります`LPCWSTR`です。</span><span class="sxs-lookup"><span data-stu-id="3d4a0-110">`wszMethod` must point to a valid `LPCWSTR`.</span></span> 

`ppQualSet`  
<span data-ttu-id="3d4a0-111">[out]メソッドの修飾子にアクセスできるようにするインターフェイス ポインターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="3d4a0-111">[out] Receives the interface pointer that allows access to the qualifiers of the method.</span></span> <span data-ttu-id="3d4a0-112">`ppQualSet` として `null` を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="3d4a0-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="3d4a0-113">かどうかは、エラーが発生し、新しいオブジェクトが返されない、ポインターが指すように設定`null`です。</span><span class="sxs-lookup"><span data-stu-id="3d4a0-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="3d4a0-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="3d4a0-114">Return value</span></span>

<span data-ttu-id="3d4a0-115">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="3d4a0-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="3d4a0-116">定数</span><span class="sxs-lookup"><span data-stu-id="3d4a0-116">Constant</span></span>  |<span data-ttu-id="3d4a0-117">[値]</span><span class="sxs-lookup"><span data-stu-id="3d4a0-117">Value</span></span>  |<span data-ttu-id="3d4a0-118">説明</span><span class="sxs-lookup"><span data-stu-id="3d4a0-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="3d4a0-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="3d4a0-119">0x80041002</span></span> | <span data-ttu-id="3d4a0-120">指定されたメソッドが存在しません。</span><span class="sxs-lookup"><span data-stu-id="3d4a0-120">The specified method does not exist.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="3d4a0-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="3d4a0-121">0x80041008</span></span> | <span data-ttu-id="3d4a0-122">パラメーターが`null`です。</span><span class="sxs-lookup"><span data-stu-id="3d4a0-122">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="3d4a0-123">0</span><span class="sxs-lookup"><span data-stu-id="3d4a0-123">0</span></span> | <span data-ttu-id="3d4a0-124">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="3d4a0-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="3d4a0-125">コメント</span><span class="sxs-lookup"><span data-stu-id="3d4a0-125">Remarks</span></span>

<span data-ttu-id="3d4a0-126">この関数への呼び出しをラップする、 [IWbemClassObject::GetMethodQualifierSet](https://msdn.microsoft.com/library/aa391446(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="3d4a0-126">This function wraps a call to the [IWbemClassObject::GetMethodQualifierSet](https://msdn.microsoft.com/library/aa391446(v=vs.85).aspx) method.</span></span> 

<span data-ttu-id="3d4a0-127">この関数に対する呼び出しがサポートされるは、現在のオブジェクトが、CIM クラスの定義である場合にのみです。</span><span class="sxs-lookup"><span data-stu-id="3d4a0-127">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="3d4a0-128">メソッドの操作では使用できません[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) CIM インスタンスを指す ponters です。</span><span class="sxs-lookup"><span data-stu-id="3d4a0-128">Method manipulation is not available for [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters that point to CIM instances.</span></span>

<span data-ttu-id="3d4a0-129">各メソッドには、独自の修飾子があるため、 [IWbemQualifierSet ポインター](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)により、呼び出し元を追加、編集、またはこれらの修飾子を削除します。</span><span class="sxs-lookup"><span data-stu-id="3d4a0-129">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) lets the caller add, edit, or delete these qualifiers.</span></span>

## <a name="requirements"></a><span data-ttu-id="3d4a0-130">必要条件</span><span class="sxs-lookup"><span data-stu-id="3d4a0-130">Requirements</span></span>  
<span data-ttu-id="3d4a0-131">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3d4a0-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d4a0-132">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="3d4a0-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="3d4a0-133">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3d4a0-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d4a0-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d4a0-134">See also</span></span>  
[<span data-ttu-id="3d4a0-135">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="3d4a0-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

---
title: "InheritsFrom 関数 (アンマネージ API リファレンス)"
description: "InheritsFrom 関数は、クラスまたはインスタンスが特定の親クラスから派生しているかどうかを決定します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: InheritsFrom
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: InheritsFrom
helpviewer_keywords: InheritsFrom function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0dce964829399e6761152a8ff424671b47cc6eb3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="d4ef5-103">InheritsFrom 関数</span><span class="sxs-lookup"><span data-stu-id="d4ef5-103">InheritsFrom function</span></span>
<span data-ttu-id="d4ef5-104">現在のクラスまたはインスタンスが指定された親クラスから派生するかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="d4ef5-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="d4ef5-105">構文</span><span class="sxs-lookup"><span data-stu-id="d4ef5-105">Syntax</span></span>  
  
```
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a><span data-ttu-id="d4ef5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d4ef5-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d4ef5-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="d4ef5-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="d4ef5-108">[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="d4ef5-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="d4ef5-109">[in]クラスの名前です。</span><span class="sxs-lookup"><span data-stu-id="d4ef5-109">[in] The name of the class.</span></span> <span data-ttu-id="d4ef5-110">`wszAncestor`有効なをポイントする必要があります`LPCWSTR`です。</span><span class="sxs-lookup"><span data-stu-id="d4ef5-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="d4ef5-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="d4ef5-111">Return value</span></span>

<span data-ttu-id="d4ef5-112">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="d4ef5-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d4ef5-113">定数</span><span class="sxs-lookup"><span data-stu-id="d4ef5-113">Constant</span></span>  |<span data-ttu-id="d4ef5-114">[値]</span><span class="sxs-lookup"><span data-stu-id="d4ef5-114">Value</span></span>  |<span data-ttu-id="d4ef5-115">説明</span><span class="sxs-lookup"><span data-stu-id="d4ef5-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="d4ef5-116">0</span><span class="sxs-lookup"><span data-stu-id="d4ef5-116">0</span></span> | <span data-ttu-id="d4ef5-117">現在のオブジェクトから継承`wszAncestor`です。</span><span class="sxs-lookup"><span data-stu-id="d4ef5-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="d4ef5-118">1</span><span class="sxs-lookup"><span data-stu-id="d4ef5-118">1</span></span> | <span data-ttu-id="d4ef5-119">現在のオブジェクトを継承しない`wszAncestor`です。</span><span class="sxs-lookup"><span data-stu-id="d4ef5-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d4ef5-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d4ef5-120">0x80041008</span></span> | <span data-ttu-id="d4ef5-121">`wszAncestor` は `null` です。</span><span class="sxs-lookup"><span data-stu-id="d4ef5-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="d4ef5-122">コメント</span><span class="sxs-lookup"><span data-stu-id="d4ef5-122">Remarks</span></span>

<span data-ttu-id="d4ef5-123">この関数への呼び出しをラップする、 [IWbemClassObject::InheritsFrom](https://msdn.microsoft.com/library/aa391452(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d4ef5-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](https://msdn.microsoft.com/library/aa391452(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d4ef5-124">必要条件</span><span class="sxs-lookup"><span data-stu-id="d4ef5-124">Requirements</span></span>  
 <span data-ttu-id="d4ef5-125">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d4ef5-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4ef5-126">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d4ef5-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d4ef5-127">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d4ef5-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4ef5-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4ef5-128">See also</span></span>  
[<span data-ttu-id="d4ef5-129">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d4ef5-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

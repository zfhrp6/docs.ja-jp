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
ms.openlocfilehash: aedeec76f4fabb2f6bd32d7d06eb5a1a5734534e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="df698-103">InheritsFrom 関数</span><span class="sxs-lookup"><span data-stu-id="df698-103">InheritsFrom function</span></span>
<span data-ttu-id="df698-104">現在のクラスまたはインスタンスが指定された親クラスから派生するかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="df698-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="df698-105">構文</span><span class="sxs-lookup"><span data-stu-id="df698-105">Syntax</span></span>  
  
```
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a><span data-ttu-id="df698-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="df698-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="df698-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="df698-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="df698-108">[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="df698-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="df698-109">[in]クラスの名前です。</span><span class="sxs-lookup"><span data-stu-id="df698-109">[in] The name of the class.</span></span> <span data-ttu-id="df698-110">`wszAncestor`有効なをポイントする必要があります`LPCWSTR`です。</span><span class="sxs-lookup"><span data-stu-id="df698-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="df698-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="df698-111">Return value</span></span>

<span data-ttu-id="df698-112">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="df698-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="df698-113">定数</span><span class="sxs-lookup"><span data-stu-id="df698-113">Constant</span></span>  |<span data-ttu-id="df698-114">値</span><span class="sxs-lookup"><span data-stu-id="df698-114">Value</span></span>  |<span data-ttu-id="df698-115">説明</span><span class="sxs-lookup"><span data-stu-id="df698-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="df698-116">0</span><span class="sxs-lookup"><span data-stu-id="df698-116">0</span></span> | <span data-ttu-id="df698-117">現在のオブジェクトから継承`wszAncestor`です。</span><span class="sxs-lookup"><span data-stu-id="df698-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="df698-118">1</span><span class="sxs-lookup"><span data-stu-id="df698-118">1</span></span> | <span data-ttu-id="df698-119">現在のオブジェクトを継承しない`wszAncestor`です。</span><span class="sxs-lookup"><span data-stu-id="df698-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="df698-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="df698-120">0x80041008</span></span> | <span data-ttu-id="df698-121">`wszAncestor` は `null` です。</span><span class="sxs-lookup"><span data-stu-id="df698-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="df698-122">コメント</span><span class="sxs-lookup"><span data-stu-id="df698-122">Remarks</span></span>

<span data-ttu-id="df698-123">この関数への呼び出しをラップする、 [IWbemClassObject::InheritsFrom](https://msdn.microsoft.com/library/aa391452(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="df698-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](https://msdn.microsoft.com/library/aa391452(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="df698-124">要件</span><span class="sxs-lookup"><span data-stu-id="df698-124">Requirements</span></span>  
 <span data-ttu-id="df698-125">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="df698-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df698-126">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="df698-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="df698-127">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="df698-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df698-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="df698-128">See also</span></span>  
[<span data-ttu-id="df698-129">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="df698-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

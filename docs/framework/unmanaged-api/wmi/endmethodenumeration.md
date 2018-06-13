---
title: EndMethodEnumeration 関数 (アンマネージ API リファレンス)
description: EndMethodEnumeration 関数は、メソッドの列挙のシーケンスを終了します。
ms.date: 11/06/2017
api_name:
- EndMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndMethodEnumeration
helpviewer_keywords:
- EndMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d09a2ee278dba7e711891bc6d72043bb3a499dd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458491"
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="ff060-103">EndMethodEnumeration 関数</span><span class="sxs-lookup"><span data-stu-id="ff060-103">EndMethodEnumeration function</span></span>
<span data-ttu-id="ff060-104">呼び出し時に起動列挙のシーケンスの終了、 [BeginMethodEnumeration 関数](beginmethodenumeration.md)です。</span><span class="sxs-lookup"><span data-stu-id="ff060-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="ff060-105">構文</span><span class="sxs-lookup"><span data-stu-id="ff060-105">Syntax</span></span>  
  
```  
HRESULT EndMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="ff060-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff060-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="ff060-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="ff060-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="ff060-108">[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="ff060-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="ff060-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff060-109">Return value</span></span>

<span data-ttu-id="ff060-110">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="ff060-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ff060-111">定数</span><span class="sxs-lookup"><span data-stu-id="ff060-111">Constant</span></span>  |<span data-ttu-id="ff060-112">[値]</span><span class="sxs-lookup"><span data-stu-id="ff060-112">Value</span></span>  |<span data-ttu-id="ff060-113">説明</span><span class="sxs-lookup"><span data-stu-id="ff060-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="ff060-114">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="ff060-114">0x8004101d</span></span> | <span data-ttu-id="ff060-115">内部エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ff060-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="ff060-116">0</span><span class="sxs-lookup"><span data-stu-id="ff060-116">0</span></span> | <span data-ttu-id="ff060-117">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff060-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="ff060-118">コメント</span><span class="sxs-lookup"><span data-stu-id="ff060-118">Remarks</span></span>

<span data-ttu-id="ff060-119">この関数への呼び出しをラップする、 [IWbemClassObject::EndMethodEnumeration](https://msdn.microsoft.com/library/aa391441(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="ff060-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](https://msdn.microsoft.com/library/aa391441(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="ff060-120">列挙のシーケンスを使用して、呼び出し元の開始[BeginMethodEnumeration 関数](beginmethodenumeration.md)、しを呼び出して、 [NextMethod 関数](nextmethod.md )メソッドが戻るまで`WBEM_S_NO_MORE_DATA`です。</span><span class="sxs-lookup"><span data-stu-id="ff060-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="ff060-121">呼び出し元は、必要に応じてが完了すると、シーケンスを呼び出して`EndMethodEnumeration`です。</span><span class="sxs-lookup"><span data-stu-id="ff060-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="ff060-122">呼び出し元が呼び出すことで列挙体を早期終了可能性があります`EndMethodEnumeration`いつでもできます。</span><span class="sxs-lookup"><span data-stu-id="ff060-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="ff060-123">要件</span><span class="sxs-lookup"><span data-stu-id="ff060-123">Requirements</span></span>  
 <span data-ttu-id="ff060-124">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ff060-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff060-125">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ff060-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ff060-126">**.NET framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ff060-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff060-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff060-127">See also</span></span>  
[<span data-ttu-id="ff060-128">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="ff060-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

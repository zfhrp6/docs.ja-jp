---
title: GetObjectText 関数 (アンマネージ API リファレンス)
description: GetObjectText 関数は、MOF 構文では、オブジェクトのテキストのレンダリングを返します。
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d2f0e766a3a310bdb58f7cbffd8d49404eb5e0b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459640"
---
# <a name="getobjecttext-function"></a><span data-ttu-id="6bb25-103">GetObjectText 関数</span><span class="sxs-lookup"><span data-stu-id="6bb25-103">GetObjectText function</span></span>
<span data-ttu-id="6bb25-104">管理オブジェクト フォーマット (MOF) の構文では、オブジェクトのテキストのレンダリングを返します。</span><span class="sxs-lookup"><span data-stu-id="6bb25-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="6bb25-105">構文</span><span class="sxs-lookup"><span data-stu-id="6bb25-105">Syntax</span></span>  
  
```  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a><span data-ttu-id="6bb25-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6bb25-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="6bb25-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="6bb25-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="6bb25-108">[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="6bb25-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lFlags`  
<span data-ttu-id="6bb25-109">[in]通常は 0 です。</span><span class="sxs-lookup"><span data-stu-id="6bb25-109">[in] Normally 0.</span></span> <span data-ttu-id="6bb25-110">場合`WBEM_FLAG_NO_FLAVORS`(0x1) を指定すると、修飾子は伝達またはフレーバーの情報がない場合に含まれています。</span><span class="sxs-lookup"><span data-stu-id="6bb25-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

`pstrObjectText`   
<span data-ttu-id="6bb25-111">[out]ポインター、`null`エントリです。</span><span class="sxs-lookup"><span data-stu-id="6bb25-111">[out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="6bb25-112">戻り時に、新しく割り当てられた`BSTR`を含むオブジェクトの MOF 構文レンダリングします。</span><span class="sxs-lookup"><span data-stu-id="6bb25-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="6bb25-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="6bb25-113">Return value</span></span>

<span data-ttu-id="6bb25-114">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="6bb25-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6bb25-115">定数</span><span class="sxs-lookup"><span data-stu-id="6bb25-115">Constant</span></span>  |<span data-ttu-id="6bb25-116">[値]</span><span class="sxs-lookup"><span data-stu-id="6bb25-116">Value</span></span>  |<span data-ttu-id="6bb25-117">説明</span><span class="sxs-lookup"><span data-stu-id="6bb25-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="6bb25-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="6bb25-118">0x80041001</span></span> | <span data-ttu-id="6bb25-119">一般的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="6bb25-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="6bb25-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="6bb25-120">0x80041008</span></span> | <span data-ttu-id="6bb25-121">パラメーターが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="6bb25-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="6bb25-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="6bb25-122">0x80041006</span></span> | <span data-ttu-id="6bb25-123">操作を完了するのに十分なメモリがあります。</span><span class="sxs-lookup"><span data-stu-id="6bb25-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="6bb25-124">0</span><span class="sxs-lookup"><span data-stu-id="6bb25-124">0</span></span> | <span data-ttu-id="6bb25-125">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="6bb25-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="6bb25-126">コメント</span><span class="sxs-lookup"><span data-stu-id="6bb25-126">Remarks</span></span>

<span data-ttu-id="6bb25-127">この関数への呼び出しをラップする、 [IWbemClassObject::GetObjectText](https://msdn.microsoft.com/library/aa391448(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="6bb25-127">This function wraps a call to the [IWbemClassObject::GetObjectText](https://msdn.microsoft.com/library/aa391448(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="6bb25-128">MOF テキストを返すには、オブジェクトに関するすべての情報が、元のオブジェクトを作成し直すことができる MOF コンパイラのための十分な情報のみがありません。</span><span class="sxs-lookup"><span data-stu-id="6bb25-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="6bb25-129">たとえば、伝達された修飾子または親クラスのプロパティは含まれません。</span><span class="sxs-lookup"><span data-stu-id="6bb25-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="6bb25-130">次のアルゴリズムは、メソッドのパラメーターのテキストを再構築に使用されます。</span><span class="sxs-lookup"><span data-stu-id="6bb25-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="6bb25-131">パラメーターは、その識別子の値の順序で resequenced されます。</span><span class="sxs-lookup"><span data-stu-id="6bb25-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="6bb25-132">パラメーターとして指定されている`[in]`と`[out]`パラメーターを 1 つに結合されます。</span><span class="sxs-lookup"><span data-stu-id="6bb25-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>
 
<span data-ttu-id="6bb25-133">`pstrObjectText` ポインターにする必要があります、`null`有効では、メソッドを呼び出す前に、ポインターの割り当てを解除できませんが、文字列をポイントする必要がありますいない関数が呼び出されるとします。 します。</span><span class="sxs-lookup"><span data-stu-id="6bb25-133">`pstrObjectText` must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="6bb25-134">要件</span><span class="sxs-lookup"><span data-stu-id="6bb25-134">Requirements</span></span>  
<span data-ttu-id="6bb25-135">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6bb25-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bb25-136">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6bb25-136">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="6bb25-137">**.NET framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6bb25-137">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb25-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="6bb25-138">See also</span></span>  
[<span data-ttu-id="6bb25-139">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="6bb25-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

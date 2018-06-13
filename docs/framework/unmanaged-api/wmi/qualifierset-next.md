---
title: QualifierSet_Next 関数 (アンマネージ API リファレンス)
description: QualifierSet_Next 関数では、列挙体の次の修飾子を取得します。
ms.date: 11/06/2017
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8232691c697c51b5a480a68c6d952f294a63460
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460228"
---
# <a name="qualifiersetnext-function"></a><span data-ttu-id="411f6-103">QualifierSet_Next 関数</span><span class="sxs-lookup"><span data-stu-id="411f6-103">QualifierSet_Next function</span></span>
<span data-ttu-id="411f6-104">呼び出しの使用を開始する列挙体の次の修飾子を取得、 [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)関数。</span><span class="sxs-lookup"><span data-stu-id="411f6-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="411f6-105">構文</span><span class="sxs-lookup"><span data-stu-id="411f6-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Next (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,        
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a><span data-ttu-id="411f6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="411f6-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="411f6-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="411f6-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="411f6-108">[in]ポインター、 [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="411f6-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`lFlags`   
<span data-ttu-id="411f6-109">[in]予約されています。</span><span class="sxs-lookup"><span data-stu-id="411f6-109">[in] Reserved.</span></span> <span data-ttu-id="411f6-110">このパラメーターは、0 を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="411f6-110">This parameter must be 0.</span></span>

`pstrName`   
<span data-ttu-id="411f6-111">[out]修飾子の名前。</span><span class="sxs-lookup"><span data-stu-id="411f6-111">[out] The name of the qualifier.</span></span> <span data-ttu-id="411f6-112">場合`null`、このパラメーターは無視されます。 それ以外の場合、`pstrName`指す必要がありますいない有効な`BSTR`またはメモリ リークが発生します。</span><span class="sxs-lookup"><span data-stu-id="411f6-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="411f6-113">かどうかは null でない関数を常に割り当てる新しい`BSTR`を返す場合`WBEM_S_NO_ERROR`です。</span><span class="sxs-lookup"><span data-stu-id="411f6-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

`pVal`   
<span data-ttu-id="411f6-114">[out]成功した場合、修飾子の値。</span><span class="sxs-lookup"><span data-stu-id="411f6-114">[out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="411f6-115">関数が失敗した場合、`VARIANT`によって示される`pVal`は変更されません。</span><span class="sxs-lookup"><span data-stu-id="411f6-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="411f6-116">このパラメーターが場合`null`パラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="411f6-116">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="411f6-117">[out]修飾子の種類を受け取る long 整数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="411f6-117">[out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="411f6-118">このパラメーターを指定できますフレーバー情報が必要ない場合`null`です。</span><span class="sxs-lookup"><span data-stu-id="411f6-118">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="411f6-119">戻り値</span><span class="sxs-lookup"><span data-stu-id="411f6-119">Return value</span></span>

<span data-ttu-id="411f6-120">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="411f6-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="411f6-121">定数</span><span class="sxs-lookup"><span data-stu-id="411f6-121">Constant</span></span>  |<span data-ttu-id="411f6-122">[値]</span><span class="sxs-lookup"><span data-stu-id="411f6-122">Value</span></span>  |<span data-ttu-id="411f6-123">説明</span><span class="sxs-lookup"><span data-stu-id="411f6-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="411f6-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="411f6-124">0x80041008</span></span> | <span data-ttu-id="411f6-125">パラメーターが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="411f6-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="411f6-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="411f6-126">0x8004101d</span></span> | <span data-ttu-id="411f6-127">呼び出し元を呼び出さなかった[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)です。</span><span class="sxs-lookup"><span data-stu-id="411f6-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="411f6-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="411f6-128">0x80041006</span></span> | <span data-ttu-id="411f6-129">十分なメモリが新しい列挙体を開始します。</span><span class="sxs-lookup"><span data-stu-id="411f6-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="411f6-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="411f6-130">0x40005</span></span> | <span data-ttu-id="411f6-131">複数修飾子は、列挙体に残されます。</span><span class="sxs-lookup"><span data-stu-id="411f6-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="411f6-132">0</span><span class="sxs-lookup"><span data-stu-id="411f6-132">0</span></span> | <span data-ttu-id="411f6-133">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="411f6-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="411f6-134">コメント</span><span class="sxs-lookup"><span data-stu-id="411f6-134">Remarks</span></span>

<span data-ttu-id="411f6-135">この関数への呼び出しをラップする、 [IWbemQualifierSet::Next](https://msdn.microsoft.com/library/aa391870(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="411f6-135">This function wraps a call to the [IWbemQualifierSet::Next](https://msdn.microsoft.com/library/aa391870(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="411f6-136">呼び出す、`QualifierSet_Next`関数の戻り値まで、すべての修飾子を列挙するには、繰り返し関数`WBEM_S_NO_MORE_DATA`です。</span><span class="sxs-lookup"><span data-stu-id="411f6-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="411f6-137">列挙体を早い段階を終了するには、呼び出し、 [QualifierSet_EndEnumeration](qualifierset-endenumeration.md)関数。</span><span class="sxs-lookup"><span data-stu-id="411f6-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="411f6-138">列挙体の中に返された修飾子の順序は定義されません。</span><span class="sxs-lookup"><span data-stu-id="411f6-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="411f6-139">要件</span><span class="sxs-lookup"><span data-stu-id="411f6-139">Requirements</span></span>  
 <span data-ttu-id="411f6-140">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="411f6-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="411f6-141">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="411f6-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="411f6-142">**.NET framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="411f6-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="411f6-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="411f6-143">See also</span></span>  
[<span data-ttu-id="411f6-144">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="411f6-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

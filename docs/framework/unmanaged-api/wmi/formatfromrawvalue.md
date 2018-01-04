---
title: "FormatFromRawValue 関数 (アンマネージ API リファレンス)"
description: "FormatFromRawValue 関数では、生のパフォーマンス データを指定した形式に変換します。"
ms.date: 11/21/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: FormatFromRawValue
api_location: PerfCounter.dll
api_type: DLLExport
f1_keywords: FormatFromRawValue
helpviewer_keywords: FormatFromRawValue function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3daa89ec0b40bb9c08898ecd682f05f0f0ce09a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="6841b-103">FormatFromRawValue 関数</span><span class="sxs-lookup"><span data-stu-id="6841b-103">FormatFromRawValue function</span></span>
<span data-ttu-id="6841b-104">形式の変換が時間ベースの場合は、指定された形式に 1 つの生のパフォーマンス データの値または生のパフォーマンス データの 2 つの値に変換します。</span><span class="sxs-lookup"><span data-stu-id="6841b-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="6841b-105">構文</span><span class="sxs-lookup"><span data-stu-id="6841b-105">Syntax</span></span>  
  
```  
int FormatFromRawValue (
   [in] uint                    dwCounterType, 
   [in] uint                    dwFormat, 
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
); 
```  

## <a name="parameters"></a><span data-ttu-id="6841b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6841b-106">Parameters</span></span>

`dwCounterType`  
<span data-ttu-id="6841b-107">[in]カウンターの型。</span><span class="sxs-lookup"><span data-stu-id="6841b-107">[in] The counter type.</span></span> <span data-ttu-id="6841b-108">カウンターの種類の一覧は、次を参照してください。 [WMI パフォーマンス カウンターの種類](https://msdn.microsoft.com/library/aa394569(v=vs.85).aspx)です。</span><span class="sxs-lookup"><span data-stu-id="6841b-108">For a list of counter types, see [WMI Performance Counter Types](https://msdn.microsoft.com/library/aa394569(v=vs.85).aspx).</span></span> <span data-ttu-id="6841b-109">`dwCounterType`以外の場合は、どのカウンター型でもかまいません`PERF_LARGE_RAW_FRACTION`と`PERF_LARGE_RAW_BASE`です。</span><span class="sxs-lookup"><span data-stu-id="6841b-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span> 

`dwFormat`  
<span data-ttu-id="6841b-110">[in]生のパフォーマンス データを変換先形式です。</span><span class="sxs-lookup"><span data-stu-id="6841b-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="6841b-111">次の値のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="6841b-111">It can be one of the following values:</span></span>

|<span data-ttu-id="6841b-112">定数</span><span class="sxs-lookup"><span data-stu-id="6841b-112">Constant</span></span>  |<span data-ttu-id="6841b-113">[値]</span><span class="sxs-lookup"><span data-stu-id="6841b-113">Value</span></span>  |<span data-ttu-id="6841b-114">説明</span><span class="sxs-lookup"><span data-stu-id="6841b-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="6841b-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="6841b-115">0x00000200</span></span> | <span data-ttu-id="6841b-116">倍精度浮動小数点値として計算された値を返します。</span><span class="sxs-lookup"><span data-stu-id="6841b-116">Return the calculated value as a double-precision floating point value.</span></span> | 
| `PDH_FMT_LARGE` | <span data-ttu-id="6841b-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="6841b-117">0x00000400</span></span> | <span data-ttu-id="6841b-118">計算される値を 64 ビット整数として返します。</span><span class="sxs-lookup"><span data-stu-id="6841b-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="6841b-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="6841b-119">0x00000100</span></span> | <span data-ttu-id="6841b-120">計算される値を 32 ビット整数として返します。</span><span class="sxs-lookup"><span data-stu-id="6841b-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="6841b-121">次のスケーリングのフラグのいずれかの論理和は以前の値のいずれかのことができます。</span><span class="sxs-lookup"><span data-stu-id="6841b-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="6841b-122">定数</span><span class="sxs-lookup"><span data-stu-id="6841b-122">Constant</span></span>  |<span data-ttu-id="6841b-123">[値]</span><span class="sxs-lookup"><span data-stu-id="6841b-123">Value</span></span>  |<span data-ttu-id="6841b-124">説明</span><span class="sxs-lookup"><span data-stu-id="6841b-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="6841b-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="6841b-125">0x00001000</span></span> | <span data-ttu-id="6841b-126">カウンターのスケール ファクターは適用されません。</span><span class="sxs-lookup"><span data-stu-id="6841b-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="6841b-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="6841b-127">0x00002000</span></span> | <span data-ttu-id="6841b-128">1,000 最終的な値を乗算します。</span><span class="sxs-lookup"><span data-stu-id="6841b-128">Multiply the final value by 1,000.</span></span> | 

`pTimeBase`  
<span data-ttu-id="6841b-129">[in]形式の変換が必要な場合、時間ベースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6841b-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="6841b-130">時間ベースの情報は、形式変換の必要はありません、このパラメーターの値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="6841b-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

<span data-ttu-id="6841b-131">`pRawValue1`[in]ポインター、 [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx)生のパフォーマンスの値を表す構造です。</span><span class="sxs-lookup"><span data-stu-id="6841b-131">`pRawValue1` [in] A pointer to a [`PDH_RAW_COUNTER`](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) structure that represents a raw performance value.</span></span>

<span data-ttu-id="6841b-132">`pRawValue2`[in]ポインター、 [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx)を 2 番目の生のパフォーマンス値を表す構造です。</span><span class="sxs-lookup"><span data-stu-id="6841b-132">`pRawValue2` [in] A pointer to a [`PDH_RAW_COUNTER`](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) structure that represents a second raw performance value.</span></span> <span data-ttu-id="6841b-133">このパラメーターを指定する場合は、2 番目の生のパフォーマンス値が必要ではありません、`null`です。</span><span class="sxs-lookup"><span data-stu-id="6841b-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

<span data-ttu-id="6841b-134">`pFmtValue`[out]ポインター、 [ `PDH_FMT_COUNTERVALUE` ](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx)書式設定されたパフォーマンスの値を受け取る。</span><span class="sxs-lookup"><span data-stu-id="6841b-134">`pFmtValue` [out] A pointer to a [`PDH_FMT_COUNTERVALUE`](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="6841b-135">戻り値</span><span class="sxs-lookup"><span data-stu-id="6841b-135">Return value</span></span>

<span data-ttu-id="6841b-136">この関数では、次の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="6841b-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="6841b-137">定数</span><span class="sxs-lookup"><span data-stu-id="6841b-137">Constant</span></span>  |<span data-ttu-id="6841b-138">[値]</span><span class="sxs-lookup"><span data-stu-id="6841b-138">Value</span></span>  |<span data-ttu-id="6841b-139">説明</span><span class="sxs-lookup"><span data-stu-id="6841b-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="6841b-140">0</span><span class="sxs-lookup"><span data-stu-id="6841b-140">0</span></span> | <span data-ttu-id="6841b-141">関数呼び出しが成功します。</span><span class="sxs-lookup"><span data-stu-id="6841b-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="6841b-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="6841b-142">0xC0000BBD</span></span> | <span data-ttu-id="6841b-143">必須の引数は、見つからないか正しくないです。</span><span class="sxs-lookup"><span data-stu-id="6841b-143">A required argument is missing or incorrect.</span></span> | 
| `PDH_INVALID_HANDLE` | <span data-ttu-id="6841b-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="6841b-144">0xC0000BBC</span></span> | <span data-ttu-id="6841b-145">ハンドルが有効な PDH オブジェクトではありません。</span><span class="sxs-lookup"><span data-stu-id="6841b-145">The handle is not a valid PDH object.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="6841b-146">コメント</span><span class="sxs-lookup"><span data-stu-id="6841b-146">Remarks</span></span>

<span data-ttu-id="6841b-147">この関数への呼び出しをラップする、 [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx)関数。</span><span class="sxs-lookup"><span data-stu-id="6841b-147">This function wraps a call to the [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="6841b-148">必要条件</span><span class="sxs-lookup"><span data-stu-id="6841b-148">Requirements</span></span>  
 <span data-ttu-id="6841b-149">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6841b-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6841b-150">**ライブラリ:** PerfCounter.dll</span><span class="sxs-lookup"><span data-stu-id="6841b-150">**Library:** PerfCounter.dll</span></span>  
  
 <span data-ttu-id="6841b-151">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6841b-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6841b-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="6841b-152">See also</span></span>  
[<span data-ttu-id="6841b-153">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="6841b-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

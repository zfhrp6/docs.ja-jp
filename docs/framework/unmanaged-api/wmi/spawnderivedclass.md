---
title: SpawnDerivedClass 関数 (アンマネージ API リファレンス)
description: SpawnDerivedClass 関数は、オブジェクトから派生する新しいオブジェクトを作成します。
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe93b7ee28db8151345871b0dd716d41227ed565
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="9d83d-103">SpawnDerivedClass 関数</span><span class="sxs-lookup"><span data-stu-id="9d83d-103">SpawnDerivedClass function</span></span>
<span data-ttu-id="9d83d-104">指定したオブジェクトから新しく派生クラス オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9d83d-104">Creates a newly derived class object from a specified object.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="9d83d-105">構文</span><span class="sxs-lookup"><span data-stu-id="9d83d-105">Syntax</span></span>  
  
```  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a><span data-ttu-id="9d83d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9d83d-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="9d83d-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="9d83d-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="9d83d-108">[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="9d83d-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lFlags`  
<span data-ttu-id="9d83d-109">[in]予約されています。</span><span class="sxs-lookup"><span data-stu-id="9d83d-109">[in] Reserved.</span></span> <span data-ttu-id="9d83d-110">このパラメーターは、0 を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d83d-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="9d83d-111">[out]新しいクラス定義のオブジェクトへのポインターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="9d83d-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="9d83d-112">エラーが発生する場合、新しいオブジェクトが返される、および`ppNewClass`左は変更されていません。</span><span class="sxs-lookup"><span data-stu-id="9d83d-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="9d83d-113">その値にすることはできません`null`です。</span><span class="sxs-lookup"><span data-stu-id="9d83d-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="9d83d-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="9d83d-114">Return value</span></span>

<span data-ttu-id="9d83d-115">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="9d83d-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9d83d-116">定数</span><span class="sxs-lookup"><span data-stu-id="9d83d-116">Constant</span></span>  |<span data-ttu-id="9d83d-117">[値]</span><span class="sxs-lookup"><span data-stu-id="9d83d-117">Value</span></span>  |<span data-ttu-id="9d83d-118">説明</span><span class="sxs-lookup"><span data-stu-id="9d83d-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="9d83d-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="9d83d-119">0x80041001</span></span> | <span data-ttu-id="9d83d-120">一般的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9d83d-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="9d83d-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="9d83d-121">0x80041016</span></span> | <span data-ttu-id="9d83d-122">インスタンスからのクラスの生成などの無効な操作が要求されました。</span><span class="sxs-lookup"><span data-stu-id="9d83d-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="9d83d-123">ソース クラスが完全に定義されているか、新しい派生クラスは許可されていないために、Windows の管理に登録されています。</span><span class="sxs-lookup"><span data-stu-id="9d83d-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="9d83d-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="9d83d-124">0x80041006</span></span> | <span data-ttu-id="9d83d-125">操作を完了するのに十分なメモリがあります。</span><span class="sxs-lookup"><span data-stu-id="9d83d-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="9d83d-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="9d83d-126">0x80041008</span></span> | <span data-ttu-id="9d83d-127">`ppNewClass` は `null` です。</span><span class="sxs-lookup"><span data-stu-id="9d83d-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="9d83d-128">0</span><span class="sxs-lookup"><span data-stu-id="9d83d-128">0</span></span> | <span data-ttu-id="9d83d-129">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="9d83d-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="9d83d-130">コメント</span><span class="sxs-lookup"><span data-stu-id="9d83d-130">Remarks</span></span>

<span data-ttu-id="9d83d-131">この関数への呼び出しをラップする、 [IWbemClassObject::SpawnDerivedClass](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="9d83d-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="9d83d-132">`ptr` 子オブジェクトの親クラスとなるクラス定義でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="9d83d-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="9d83d-133">返されたオブジェクトでは、現在のオブジェクトのサブクラスになります。</span><span class="sxs-lookup"><span data-stu-id="9d83d-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="9d83d-134">返される新しいオブジェクト`ppNewClass`現在のオブジェクトのサブクラスに自動的になります。</span><span class="sxs-lookup"><span data-stu-id="9d83d-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="9d83d-135">この動作はオーバーライドできません。</span><span class="sxs-lookup"><span data-stu-id="9d83d-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="9d83d-136">サブクラス (派生クラス) を作成できる他の方法はありません。</span><span class="sxs-lookup"><span data-stu-id="9d83d-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="9d83d-137">要件</span><span class="sxs-lookup"><span data-stu-id="9d83d-137">Requirements</span></span>  
 <span data-ttu-id="9d83d-138">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9d83d-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d83d-139">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="9d83d-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="9d83d-140">**.NET framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9d83d-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d83d-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d83d-141">See also</span></span>  
[<span data-ttu-id="9d83d-142">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="9d83d-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

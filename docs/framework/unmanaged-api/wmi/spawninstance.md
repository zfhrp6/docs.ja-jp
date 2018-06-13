---
title: SpawnInstance 関数 (アンマネージ API リファレンス)
description: SpawnInstance 関数では、クラスの新しいインスタンスを作成します。
ms.date: 11/06/2017
api_name:
- SpawnInstance
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnInstance
helpviewer_keywords:
- SpawnInstance function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f8189f0adb62aa32cd0b85ca5a653aa466c7032
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460463"
---
# <a name="spawninstance-function"></a><span data-ttu-id="e7b58-103">SpawnInstance 関数</span><span class="sxs-lookup"><span data-stu-id="e7b58-103">SpawnInstance function</span></span>
<span data-ttu-id="e7b58-104">クラスの新しいインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e7b58-104">Creates a new instance of a class.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="e7b58-105">構文</span><span class="sxs-lookup"><span data-stu-id="e7b58-105">Syntax</span></span>  
  
```  
HRESULT SpawnInstance (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance); 
```  

## <a name="parameters"></a><span data-ttu-id="e7b58-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e7b58-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e7b58-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="e7b58-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="e7b58-108">[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="e7b58-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lFlags`  
<span data-ttu-id="e7b58-109">[in]予約されています。</span><span class="sxs-lookup"><span data-stu-id="e7b58-109">[in] Reserved.</span></span> <span data-ttu-id="e7b58-110">このパラメーターは、0 を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e7b58-110">This parameter must be 0.</span></span>

`ppNewInstance`  
<span data-ttu-id="e7b58-111">[out]クラスの新しいインスタンスへのポインターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e7b58-111">[out] Receives the pointer to the new instance of the class.</span></span> <span data-ttu-id="e7b58-112">エラーが発生する場合、新しいオブジェクトが返される、および`ppNewInstance`左は変更されていません。</span><span class="sxs-lookup"><span data-stu-id="e7b58-112">If an error occurs, a new object is not returned, and `ppNewInstance` is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="e7b58-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="e7b58-113">Return value</span></span>

<span data-ttu-id="e7b58-114">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="e7b58-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e7b58-115">定数</span><span class="sxs-lookup"><span data-stu-id="e7b58-115">Constant</span></span>  |<span data-ttu-id="e7b58-116">[値]</span><span class="sxs-lookup"><span data-stu-id="e7b58-116">Value</span></span>  |<span data-ttu-id="e7b58-117">説明</span><span class="sxs-lookup"><span data-stu-id="e7b58-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="e7b58-118">0x80041020</span><span class="sxs-lookup"><span data-stu-id="e7b58-118">0x80041020</span></span> | <span data-ttu-id="e7b58-119">`ptr` 有効なクラス定義ではないと、新しいインスタンスを生成することはできません。</span><span class="sxs-lookup"><span data-stu-id="e7b58-119">`ptr` is not a valid class definition and cannot spawn new instances.</span></span> <span data-ttu-id="e7b58-120">不完全か、それが登録されていない Windows 管理で呼び出すことによって[PutClassWmi](putclasswmi.md)です。</span><span class="sxs-lookup"><span data-stu-id="e7b58-120">Either it is incomplete or it has not been registered with Windows Management by calling [PutClassWmi](putclasswmi.md).</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="e7b58-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="e7b58-121">0x80041006</span></span> | <span data-ttu-id="e7b58-122">操作を完了するのに十分なメモリがあります。</span><span class="sxs-lookup"><span data-stu-id="e7b58-122">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e7b58-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e7b58-123">0x80041008</span></span> | <span data-ttu-id="e7b58-124">`ppNewClass` は `null` です。</span><span class="sxs-lookup"><span data-stu-id="e7b58-124">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="e7b58-125">0</span><span class="sxs-lookup"><span data-stu-id="e7b58-125">0</span></span> | <span data-ttu-id="e7b58-126">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="e7b58-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e7b58-127">コメント</span><span class="sxs-lookup"><span data-stu-id="e7b58-127">Remarks</span></span>

<span data-ttu-id="e7b58-128">この関数への呼び出しをラップする、 [IWbemClassObject::SpawnInstance](https://msdn.microsoft.com/library/aa391458(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e7b58-128">This function wraps a call to the [IWbemClassObject::SpawnInstance](https://msdn.microsoft.com/library/aa391458(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="e7b58-129">`ptr` クラス定義から取得する Windows の管理。</span><span class="sxs-lookup"><span data-stu-id="e7b58-129">`ptr` must be a class definition obtained from Windows Management.</span></span> <span data-ttu-id="e7b58-130">(インスタンスからインスタンスの生成がサポートされていることに注意してくださいが返されたインスタンスが空)。次のクラス定義を使用するには、新しいインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e7b58-130">(Note that spawning an instance from an instance is supported but the returned instance is empty.) You then use this class definition to create new instances.</span></span> <span data-ttu-id="e7b58-131">呼び出し、 [PutInstanceWmi](putinstancewmi.md) Windows 管理インスタンスを作成する場合は、関数が必要です。</span><span class="sxs-lookup"><span data-stu-id="e7b58-131">A call to the [PutInstanceWmi](putinstancewmi.md) function is required if you intend to write the instance to Windows Management.</span></span>




<span data-ttu-id="e7b58-132">返される新しいオブジェクト`ppNewClass`現在のオブジェクトのサブクラスに自動的になります。</span><span class="sxs-lookup"><span data-stu-id="e7b58-132">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="e7b58-133">この動作はオーバーライドできません。</span><span class="sxs-lookup"><span data-stu-id="e7b58-133">This behavior cannot be overridden.</span></span> <span data-ttu-id="e7b58-134">サブクラス (派生クラス) を作成できる他の方法はありません。</span><span class="sxs-lookup"><span data-stu-id="e7b58-134">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="e7b58-135">要件</span><span class="sxs-lookup"><span data-stu-id="e7b58-135">Requirements</span></span>  
 <span data-ttu-id="e7b58-136">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e7b58-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7b58-137">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e7b58-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e7b58-138">**.NET framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e7b58-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7b58-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7b58-139">See also</span></span>  
[<span data-ttu-id="e7b58-140">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="e7b58-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

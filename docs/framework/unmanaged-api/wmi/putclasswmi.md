---
title: "PutClassWmi 関数 (アンマネージ API リファレンス)"
description: "PutClassWmi 関数は、新しいクラスを作成または既存のものを更新します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- PutClassWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutClassWmi
helpviewer_keywords:
- PutClassWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 219cec2096cd3d1dfe1e0d3c0903b62692e444e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="putclasswmi-function"></a><span data-ttu-id="3529c-103">PutClassWmi 関数</span><span class="sxs-lookup"><span data-stu-id="3529c-103">PutClassWmi function</span></span>
<span data-ttu-id="3529c-104">新しいクラスを作成または既存のものを更新します。</span><span class="sxs-lookup"><span data-stu-id="3529c-104">Creates a new class or updates an existing one.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="3529c-105">構文</span><span class="sxs-lookup"><span data-stu-id="3529c-105">Syntax</span></span>  
  
```  
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a><span data-ttu-id="3529c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3529c-106">Parameters</span></span>

`pObject`    
<span data-ttu-id="3529c-107">[in]有効なクラス定義へのポインター。</span><span class="sxs-lookup"><span data-stu-id="3529c-107">[in] A pointer to a valid class definition.</span></span> <span data-ttu-id="3529c-108">すべての必要なプロパティ値を持つ正しく初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3529c-108">It must be correctly initialized with all the required property values.</span></span>

`lFlags`   
<span data-ttu-id="3529c-109">[in]この関数の動作に影響するフラグの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="3529c-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="3529c-110">次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="3529c-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="3529c-111">定数</span><span class="sxs-lookup"><span data-stu-id="3529c-111">Constant</span></span>  |<span data-ttu-id="3529c-112">[値]</span><span class="sxs-lookup"><span data-stu-id="3529c-112">Value</span></span>  |<span data-ttu-id="3529c-113">説明</span><span class="sxs-lookup"><span data-stu-id="3529c-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="3529c-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="3529c-114">0x20000</span></span> | <span data-ttu-id="3529c-115">場合設定、WMI では、修正済みのフレーバーで、修飾子は保存されません。</span><span class="sxs-lookup"><span data-stu-id="3529c-115">If set, WMI does not store any qualifiers with the amended flavor.</span></span> </br> <span data-ttu-id="3529c-116">セットと見なされます、このオブジェクトがローカライズされていないとすべての修飾子がある storedwith されていない場合はこのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="3529c-116">If not set, it is assumed that this object is not localized, and all qualifiers are storedwith this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="3529c-117">0</span><span class="sxs-lookup"><span data-stu-id="3529c-117">0</span></span> | <span data-ttu-id="3529c-118">存在したり、既に存在する場合は、上書きしない場合は、クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3529c-118">Create the class if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="3529c-119">1</span><span class="sxs-lookup"><span data-stu-id="3529c-119">1</span></span> | <span data-ttu-id="3529c-120">クラスを更新します。</span><span class="sxs-lookup"><span data-stu-id="3529c-120">Update the class.</span></span> <span data-ttu-id="3529c-121">クラスは、呼び出しの成功に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3529c-121">The class must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="3529c-122">2</span><span class="sxs-lookup"><span data-stu-id="3529c-122">2</span></span> | <span data-ttu-id="3529c-123">クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3529c-123">Create the class.</span></span> <span data-ttu-id="3529c-124">クラスが既に存在する場合、呼び出しが失敗します。</span><span class="sxs-lookup"><span data-stu-id="3529c-124">The call fails if the class already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="3529c-125">0x10</span><span class="sxs-lookup"><span data-stu-id="3529c-125">0x10</span></span> | <span data-ttu-id="3529c-126">フラグは、半同期呼び出しがします。</span><span class="sxs-lookup"><span data-stu-id="3529c-126">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_OWNER_UPDATE` | <span data-ttu-id="3529c-127">0x10000</span><span class="sxs-lookup"><span data-stu-id="3529c-127">0x10000</span></span> | <span data-ttu-id="3529c-128">呼び出すときに、プッシュ プロバイダーはこのフラグを指定する必要があります`PutClassWmi`をこのクラスが変更されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="3529c-128">Push providers must specify this flag when calling `PutClassWmi` to indicate that this class has changed.</span></span> |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | <span data-ttu-id="3529c-129">0</span><span class="sxs-lookup"><span data-stu-id="3529c-129">0</span></span> | <span data-ttu-id="3529c-130">派生クラスを持たないとそのクラスのインスタンスがない場合に更新するクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="3529c-130">Allows a class to be updated if there are no derived classes and no instances of that class.</span></span> <span data-ttu-id="3529c-131">更新を実行できます常に、変更の説明の修飾子など、重要でない修飾子に場合。</span><span class="sxs-lookup"><span data-stu-id="3529c-131">It also allows updates in all cases if the change is just to unimportant qualifiers, such as the Description qualifier.</span></span> <span data-ttu-id="3529c-132">クラスのインスタンスには、または変更は、重要な修飾子には、更新プログラムは失敗します。</span><span class="sxs-lookup"><span data-stu-id="3529c-132">If the class has instances or changes are to important qualifiers, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | <span data-ttu-id="3529c-133">0x20</span><span class="sxs-lookup"><span data-stu-id="3529c-133">0x20</span></span> | <span data-ttu-id="3529c-134">変更には、子のクラスとの競合は発生しません限り、子クラスがある場合でも、クラスの更新プログラムを許可します。</span><span class="sxs-lookup"><span data-stu-id="3529c-134">Allows updates of classes even if there are child classes as long as the change does not cause any conflicts with child classes.</span></span> <span data-ttu-id="3529c-135">たとえば、このフラグは、子クラスのいずれかで記述されていない基底クラスに追加する新しいプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3529c-135">For example, this flag allows a new property to be added to the base class that was not previously mentioned in any of the child classes.</span></span> <span data-ttu-id="3529c-136">クラスのインスタンスが存在する場合、更新は失敗します。</span><span class="sxs-lookup"><span data-stu-id="3529c-136">If the class has instances, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | <span data-ttu-id="3529c-137">0x40</span><span class="sxs-lookup"><span data-stu-id="3529c-137">0x40</span></span> | <span data-ttu-id="3529c-138">競合する子クラスが存在する場合は、クラスの更新プログラムを強制的にします。</span><span class="sxs-lookup"><span data-stu-id="3529c-138">forces updates of classes when conflicting child classes exist.</span></span> <span data-ttu-id="3529c-139">たとえば、このフラグでは、クラス修飾子は、子クラスの定義し、基本クラスの既存の 1 つと競合する同じ区切り記号を追加しようとする場合、更新プログラムが強制されます。</span><span class="sxs-lookup"><span data-stu-id="3529c-139">For example, this flag forces an update if a class qualifier is defined in a child class, and the base class tries to add the same qualifier which conflicts with thte existing one.</span></span> <span data-ttu-id="3529c-140">強制モードでは、子クラスで競合する修飾子を削除することによって tis 競合を解決します。</span><span class="sxs-lookup"><span data-stu-id="3529c-140">In force mode, tis conflict is resolved by deleting the conflicting qualifier in the child class.</span></span> |

`pCtx`  
<span data-ttu-id="3529c-141">[in]この値は、通常、`null`です。</span><span class="sxs-lookup"><span data-stu-id="3529c-141">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="3529c-142">ポインターはそれ以外の場合、 [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx)要求されたクラスを提供しているプロバイダーで使用できるインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="3529c-142">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppCallResult`  
<span data-ttu-id="3529c-143">[out]場合`null`、このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="3529c-143">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="3529c-144">場合`lFlags`含む`WBEM_FLAG_RETURN_IMMEDIATELY`、関数を直ちに返します`WBEM_S_NO_ERROR`です。</span><span class="sxs-lookup"><span data-stu-id="3529c-144">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="3529c-145">`ppCallResult`パラメーターは、新しいへのポインターを受け取ります[IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="3529c-145">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="3529c-146">戻り値</span><span class="sxs-lookup"><span data-stu-id="3529c-146">Return value</span></span>

<span data-ttu-id="3529c-147">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="3529c-147">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="3529c-148">定数</span><span class="sxs-lookup"><span data-stu-id="3529c-148">Constant</span></span>  |<span data-ttu-id="3529c-149">[値]</span><span class="sxs-lookup"><span data-stu-id="3529c-149">Value</span></span>  |<span data-ttu-id="3529c-150">説明</span><span class="sxs-lookup"><span data-stu-id="3529c-150">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="3529c-151">0x80041003</span><span class="sxs-lookup"><span data-stu-id="3529c-151">0x80041003</span></span> | <span data-ttu-id="3529c-152">ユーザーには、作成またはクラスを変更する権限がありません。</span><span class="sxs-lookup"><span data-stu-id="3529c-152">The user does not have permission to create or modify classes.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="3529c-153">0x80041001</span><span class="sxs-lookup"><span data-stu-id="3529c-153">0x80041001</span></span> | <span data-ttu-id="3529c-154">不明なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3529c-154">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="3529c-155">0x80041010</span><span class="sxs-lookup"><span data-stu-id="3529c-155">0x80041010</span></span> | <span data-ttu-id="3529c-156">指定したクラスが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="3529c-156">The specified class is not valid.</span></span> <span data-ttu-id="3529c-157">通常、これが示す`pObject`インスタンス オブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="3529c-157">Typically, this indicates that `pObject` specifies an instance object.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="3529c-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="3529c-158">0x80041008</span></span> | <span data-ttu-id="3529c-159">パラメーターが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="3529c-159">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID OPERATION` | <span data-ttu-id="3529c-160">0x80041016</span><span class="sxs-lookup"><span data-stu-id="3529c-160">0x80041016</span></span> | <span data-ttu-id="3529c-161">指定されたクラス名が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="3529c-161">The specified class name is not valid.</span></span> |
| `WBEM_E_CLASS_HAS_CHILDREN` | <span data-ttu-id="3529c-162">0x80041025</span><span class="sxs-lookup"><span data-stu-id="3529c-162">0x80041025</span></span> | <span data-ttu-id="3529c-163">サブクラスを無効にする変更を加えるしようとしました。</span><span class="sxs-lookup"><span data-stu-id="3529c-163">An attempt was made to make a change that would invalidate a subclass.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="3529c-164">0x80041019</span><span class="sxs-lookup"><span data-stu-id="3529c-164">0x80041019</span></span> | <span data-ttu-id="3529c-165">`WBEM_FLAG_CREATE_ONLY`フラグが指定されましたが、クラスが既に存在します。</span><span class="sxs-lookup"><span data-stu-id="3529c-165">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the class already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="3529c-166">0x80041002</span><span class="sxs-lookup"><span data-stu-id="3529c-166">0x80041002</span></span> | <span data-ttu-id="3529c-167">`WBEM_FLAG_UPDATE_ONLY`指定された`lFlags`クラスが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="3529c-167">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, and the class was not found.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="3529c-168">0x80041020</span><span class="sxs-lookup"><span data-stu-id="3529c-168">0x80041020</span></span> | <span data-ttu-id="3529c-169">クラスに必要なプロパティがすべて設定されています。</span><span class="sxs-lookup"><span data-stu-id="3529c-169">The required properties for classes have not all been set.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="3529c-170">0x80041006</span><span class="sxs-lookup"><span data-stu-id="3529c-170">0x80041006</span></span> | <span data-ttu-id="3529c-171">操作を完了するのに十分なメモリがあります。</span><span class="sxs-lookup"><span data-stu-id="3529c-171">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="3529c-172">0x80041033</span><span class="sxs-lookup"><span data-stu-id="3529c-172">0x80041033</span></span> | <span data-ttu-id="3529c-173">WMI は、おそらく停止および再起動されました。</span><span class="sxs-lookup"><span data-stu-id="3529c-173">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="3529c-174">呼び出す[ConnectServerWmi](connectserverwmi.md)もう一度です。</span><span class="sxs-lookup"><span data-stu-id="3529c-174">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="3529c-175">0x80041015</span><span class="sxs-lookup"><span data-stu-id="3529c-175">0x80041015</span></span> | <span data-ttu-id="3529c-176">リモート プロシージャ コール (RPC) リンクで、現在のプロセスと WMI との間に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="3529c-176">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="3529c-177">0</span><span class="sxs-lookup"><span data-stu-id="3529c-177">0</span></span> | <span data-ttu-id="3529c-178">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="3529c-178">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="3529c-179">コメント</span><span class="sxs-lookup"><span data-stu-id="3529c-179">Remarks</span></span>

<span data-ttu-id="3529c-180">この関数への呼び出しをラップする、 [IWbemServices::PutClass](https://msdn.microsoft.com/library/aa392113(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="3529c-180">This function wraps a call to the [IWbemServices::PutClass](https://msdn.microsoft.com/library/aa392113(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="3529c-181">ユーザーは、アンダー スコア chacater で開始または終了する名前を持つクラスを作成しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="3529c-181">The user may not create classes with names that begin or end with an underscore chacater</span></span>

<span data-ttu-id="3529c-182">呼び出して追加のエラー情報を取得するには、関数呼び出しに失敗した場合、 [GetErrorInfo](geterrorinfo.md)関数。</span><span class="sxs-lookup"><span data-stu-id="3529c-182">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="3529c-183">必要条件</span><span class="sxs-lookup"><span data-stu-id="3529c-183">Requirements</span></span>  
 <span data-ttu-id="3529c-184">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3529c-184">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3529c-185">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="3529c-185">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="3529c-186">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3529c-186">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3529c-187">関連項目</span><span class="sxs-lookup"><span data-stu-id="3529c-187">See also</span></span>  
[<span data-ttu-id="3529c-188">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="3529c-188">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

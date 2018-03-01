---
title: "PutInstanceWmi 関数 (アンマネージ API リファレンス)"
description: "PutInstanceWmi 関数を作成または既存のクラスのインスタンスを更新します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b1996103eea87562226537f9aa90dc337c56313c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="putinstancewmi-function"></a><span data-ttu-id="2a92d-103">PutInstanceWmi 関数</span><span class="sxs-lookup"><span data-stu-id="2a92d-103">PutInstanceWmi function</span></span>
<span data-ttu-id="2a92d-104">作成するか、既存のクラスのインスタンスを更新します。</span><span class="sxs-lookup"><span data-stu-id="2a92d-104">Creates or updates an instance of an existing class.</span></span> <span data-ttu-id="2a92d-105">インスタンスは、WMI リポジトリに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="2a92d-105">The instance is written to the WMI repository.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="2a92d-106">構文</span><span class="sxs-lookup"><span data-stu-id="2a92d-106">Syntax</span></span>  
  
```  
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a><span data-ttu-id="2a92d-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2a92d-107">Parameters</span></span>

`pInst`    
<span data-ttu-id="2a92d-108">[in]書き込まれるインスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2a92d-108">[in] A pointer to the instance to be writen.</span></span>

`lFlags`   
<span data-ttu-id="2a92d-109">[in]この関数の動作に影響するフラグの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="2a92d-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="2a92d-110">次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="2a92d-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="2a92d-111">定数</span><span class="sxs-lookup"><span data-stu-id="2a92d-111">Constant</span></span>  |<span data-ttu-id="2a92d-112">[値]</span><span class="sxs-lookup"><span data-stu-id="2a92d-112">Value</span></span>  |<span data-ttu-id="2a92d-113">説明</span><span class="sxs-lookup"><span data-stu-id="2a92d-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="2a92d-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="2a92d-114">0x20000</span></span> | <span data-ttu-id="2a92d-115">かどうか設定、WMI は格納されませんされた修飾子で、 **Amended**フレーバー。</span><span class="sxs-lookup"><span data-stu-id="2a92d-115">If set, WMI does not store any qualifiers with the **Amended** flavor.</span></span> </br> <span data-ttu-id="2a92d-116">セットと見なされます、このオブジェクトがローカライズされていないとすべての修飾子がある storedwith されていない場合はこのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="2a92d-116">If not set, it is assumed that this object is not localized, and all qualifiers are storedwith this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="2a92d-117">0</span><span class="sxs-lookup"><span data-stu-id="2a92d-117">0</span></span> | <span data-ttu-id="2a92d-118">存在したり、既に存在する場合は、上書きしない場合は、インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="2a92d-118">Create the instance if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="2a92d-119">1</span><span class="sxs-lookup"><span data-stu-id="2a92d-119">1</span></span> | <span data-ttu-id="2a92d-120">インスタンスを更新します。</span><span class="sxs-lookup"><span data-stu-id="2a92d-120">Update the instance.</span></span> <span data-ttu-id="2a92d-121">成功するへの呼び出しのインスタンスが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a92d-121">The instance must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="2a92d-122">2</span><span class="sxs-lookup"><span data-stu-id="2a92d-122">2</span></span> | <span data-ttu-id="2a92d-123">インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="2a92d-123">Create the instance.</span></span> <span data-ttu-id="2a92d-124">インスタンスが既に存在する場合、呼び出しが失敗します。</span><span class="sxs-lookup"><span data-stu-id="2a92d-124">The call fails if the instance already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="2a92d-125">0x10</span><span class="sxs-lookup"><span data-stu-id="2a92d-125">0x10</span></span> | <span data-ttu-id="2a92d-126">フラグは、半同期呼び出しがします。</span><span class="sxs-lookup"><span data-stu-id="2a92d-126">The flag causes a semisynchronous call.</span></span> |

`pCtx`  
<span data-ttu-id="2a92d-127">[in]この値は、通常、`null`です。</span><span class="sxs-lookup"><span data-stu-id="2a92d-127">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="2a92d-128">ポインターはそれ以外の場合、 [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx)要求されたクラスを提供しているプロバイダーで使用できるインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="2a92d-128">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppCallResult`  
<span data-ttu-id="2a92d-129">[out]場合`null`、このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="2a92d-129">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="2a92d-130">場合`lFlags`含む`WBEM_FLAG_RETURN_IMMEDIATELY`、関数を直ちに返します`WBEM_S_NO_ERROR`です。</span><span class="sxs-lookup"><span data-stu-id="2a92d-130">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="2a92d-131">`ppCallResult`パラメーターは、新しいへのポインターを受け取ります[IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="2a92d-131">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="2a92d-132">戻り値</span><span class="sxs-lookup"><span data-stu-id="2a92d-132">Return value</span></span>

<span data-ttu-id="2a92d-133">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="2a92d-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2a92d-134">定数</span><span class="sxs-lookup"><span data-stu-id="2a92d-134">Constant</span></span>  |<span data-ttu-id="2a92d-135">[値]</span><span class="sxs-lookup"><span data-stu-id="2a92d-135">Value</span></span>  |<span data-ttu-id="2a92d-136">説明</span><span class="sxs-lookup"><span data-stu-id="2a92d-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="2a92d-137">0x80041003</span><span class="sxs-lookup"><span data-stu-id="2a92d-137">0x80041003</span></span> | <span data-ttu-id="2a92d-138">ユーザーには、指定したクラスのインスタンスを更新するアクセス許可がありません。</span><span class="sxs-lookup"><span data-stu-id="2a92d-138">The user does not have permission to update an instance of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="2a92d-139">0x80041001</span><span class="sxs-lookup"><span data-stu-id="2a92d-139">0x80041001</span></span> | <span data-ttu-id="2a92d-140">不明なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="2a92d-140">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="2a92d-141">0x80041010</span><span class="sxs-lookup"><span data-stu-id="2a92d-141">0x80041010</span></span> | <span data-ttu-id="2a92d-142">このインスタンスをサポートするクラスが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="2a92d-142">The class supporting this instance is not valid.</span></span> |
| `WBEM_E_ILLEGAL_NULL` | <span data-ttu-id="2a92d-143">0x80041028</span><span class="sxs-lookup"><span data-stu-id="2a92d-143">0x80041028</span></span> | <span data-ttu-id="2a92d-144">`null`できないプロパティに指定されました`null`でマークされているいずれかなど、**インデックス**または**not_**修飾子です。</span><span class="sxs-lookup"><span data-stu-id="2a92d-144">a `null` was specified for a property that cannot be `null`, such as one that is marked by an **Indexed** or **Not_Null** qualifier.</span></span> |
| `WBEM_E_INVALID_OBJECT` | <span data-ttu-id="2a92d-145">0x8004100f</span><span class="sxs-lookup"><span data-stu-id="2a92d-145">0x8004100f</span></span> | <span data-ttu-id="2a92d-146">指定したインスタンスが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="2a92d-146">The specified instance is not valid.</span></span> <span data-ttu-id="2a92d-147">(たとえば、呼び出す`PutInstanceWmi`クラスにこの値を返します)。</span><span class="sxs-lookup"><span data-stu-id="2a92d-147">(For example, calling `PutInstanceWmi` with a class returns this value.)</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2a92d-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2a92d-148">0x80041008</span></span> | <span data-ttu-id="2a92d-149">パラメーターが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="2a92d-149">A parameter is not valid.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="2a92d-150">0x80041019</span><span class="sxs-lookup"><span data-stu-id="2a92d-150">0x80041019</span></span> | <span data-ttu-id="2a92d-151">`WBEM_FLAG_CREATE_ONLY`フラグが指定されましたが、インスタンスは既に存在します。</span><span class="sxs-lookup"><span data-stu-id="2a92d-151">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the instance already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="2a92d-152">0x80041002</span><span class="sxs-lookup"><span data-stu-id="2a92d-152">0x80041002</span></span> | <span data-ttu-id="2a92d-153">`WBEM_FLAG_UPDATE_ONLY`指定された`lFlags`は、インスタンスが存在しません。</span><span class="sxs-lookup"><span data-stu-id="2a92d-153">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, but the instance does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="2a92d-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="2a92d-154">0x80041006</span></span> | <span data-ttu-id="2a92d-155">操作を完了するのに十分なメモリがあります。</span><span class="sxs-lookup"><span data-stu-id="2a92d-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="2a92d-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="2a92d-156">0x80041033</span></span> | <span data-ttu-id="2a92d-157">WMI は、おそらく停止および再起動されました。</span><span class="sxs-lookup"><span data-stu-id="2a92d-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="2a92d-158">呼び出す[ConnectServerWmi](connectserverwmi.md)もう一度です。</span><span class="sxs-lookup"><span data-stu-id="2a92d-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="2a92d-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="2a92d-159">0x80041015</span></span> | <span data-ttu-id="2a92d-160">リモート プロシージャ コール (RPC) リンクで、現在のプロセスと WMI との間に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="2a92d-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="2a92d-161">0</span><span class="sxs-lookup"><span data-stu-id="2a92d-161">0</span></span> | <span data-ttu-id="2a92d-162">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="2a92d-162">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="2a92d-163">コメント</span><span class="sxs-lookup"><span data-stu-id="2a92d-163">Remarks</span></span>

<span data-ttu-id="2a92d-164">この関数への呼び出しをラップする、 [IWbemServices::PutInstance](https://msdn.microsoft.com/library/aa392115(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="2a92d-164">This function wraps a call to the [IWbemServices::PutInstance](https://msdn.microsoft.com/library/aa392115(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="2a92d-165">`PutInstanceWmi`関数のインスタンスを作成して、更新のみの既存のクラスのインスタンスをサポートします。</span><span class="sxs-lookup"><span data-stu-id="2a92d-165">The `PutInstanceWmi` function supports creating instances and updating instances of existing classes only.</span></span>  <span data-ttu-id="2a92d-166">方法に応じて`pCtx`パラメーターが設定されており、一部またはすべてのインスタンスのプロパティが更新されます。</span><span class="sxs-lookup"><span data-stu-id="2a92d-166">Depending on how the `pCtx` parameter is set, either some or all of the properties of the instance are updated.</span></span> 

<span data-ttu-id="2a92d-167">ときに、インスタンスを指す`pInst`サブクラスが派生するクラスを担当するすべてのプロバイダーの呼び出し、サブクラスでは、Windows の管理に属しています。</span><span class="sxs-lookup"><span data-stu-id="2a92d-167">When the instance pointed to by `pInst` belongs to a subclass, Windows Management calls all the providers responsible for the classes from which the subclass derives.</span></span> <span data-ttu-id="2a92d-168">元の成功する必要がありますすべてこれらのプロバイダーの`PutInstanceWmi`の要求に成功します。</span><span class="sxs-lookup"><span data-stu-id="2a92d-168">All of these providers must succeed for the original `PutInstanceWmi` request to succeed.</span></span> <span data-ttu-id="2a92d-169">階層の最上位のクラスをサポートするプロバイダーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2a92d-169">The provider supporting the topmost class in the hierarchy is called first.</span></span> <span data-ttu-id="2a92d-170">呼び出し元の order が最上位のクラスのサブクラスを続行し、Windows 管理によって示されるインスタンスを所有しているクラスのプロバイダーに到達するまで、上から下へ進みます`pInst`です。</span><span class="sxs-lookup"><span data-stu-id="2a92d-170">The calling order continues with the subclass of the topmost class and proceeds from top to bottom until Windows Management reaches the provider for the class owning the instance pointed to by `pInst`.</span></span>
<span data-ttu-id="2a92d-171">Windows の管理には、インスタンスの子クラスのいずれかのプロバイダーは呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="2a92d-171">Windows Management does not call the providers for any of the child classes of an instance.</span></span> 

<span data-ttu-id="2a92d-172">アプリケーションは、クラスの階層構造に属するインスタンスを更新する必要がありますと、`pInst`パラメーターは、変更するプロパティを含むインスタンスを指す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a92d-172">When an application must update an instance that belongs to a class hierarchy, the `pInst` parameter must point to the instance containing the properties to be modified.</span></span> <span data-ttu-id="2a92d-173">つまり、ターゲット インスタンスが属しているを検討**ClassB**です。</span><span class="sxs-lookup"><span data-stu-id="2a92d-173">That is, consider a target instance that belongs to **ClassB**.</span></span> <span data-ttu-id="2a92d-174">**ClassB**から派生したインスタンス**ClassA**、および**ClassA**プロパティを定義**PropA**です。</span><span class="sxs-lookup"><span data-stu-id="2a92d-174">The **ClassB** instance derives from **ClassA**, and **ClassA** defines the property **PropA**.</span></span> <span data-ttu-id="2a92d-175">アプリケーションがの値を変更するか**PropA**で、 **ClassB**に設定する必要がありますインスタンス、`pInst`のインスタンスではなく、そのインスタンスに**ClassA**.</span><span class="sxs-lookup"><span data-stu-id="2a92d-175">If an application wants to make a change to the value of **PropA** in the **ClassB** instance, it must set `pInst` to that instance rather than an instance of **ClassA**.</span></span>

<span data-ttu-id="2a92d-176">呼び出す`PutInstanceWmi`抽象クラスのインスタンスでは許可されていません。</span><span class="sxs-lookup"><span data-stu-id="2a92d-176">Calling `PutInstanceWmi` on an instance of an abstract class is not allowed.</span></span>

<span data-ttu-id="2a92d-177">呼び出して追加のエラー情報を取得するには、関数呼び出しに失敗した場合、 [GetErrorInfo](geterrorinfo.md)関数。</span><span class="sxs-lookup"><span data-stu-id="2a92d-177">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="2a92d-178">必要条件</span><span class="sxs-lookup"><span data-stu-id="2a92d-178">Requirements</span></span>  
 <span data-ttu-id="2a92d-179">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2a92d-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a92d-180">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="2a92d-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2a92d-181">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2a92d-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a92d-182">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a92d-182">See also</span></span>  
[<span data-ttu-id="2a92d-183">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="2a92d-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

---
title: CreateInstanceEnumWmi 関数 (アンマネージ API リファレンス)
description: CreateInstanceEnumWmi 関数では、選択条件を満たす、指定されたクラスのインスタンスを含む列挙子を返します。
ms.date: 11/06/2017
api_name:
- CreateInstanceEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstanceEnumWmi
helpviewer_keywords:
- CreateInstanceEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f9297d34b01c03075db67bd904a81e589bfcc10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461377"
---
# <a name="createinstanceenumwmi-function"></a><span data-ttu-id="72b73-103">CreateInstanceEnumWmi 関数</span><span class="sxs-lookup"><span data-stu-id="72b73-103">CreateInstanceEnumWmi function</span></span>
<span data-ttu-id="72b73-104">指定された選択条件を満たす指定したクラスのインスタンスを返す列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="72b73-104">Returns an enumerator that returns the instances of a specified class that meet specified selection criteria.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="72b73-105">構文</span><span class="sxs-lookup"><span data-stu-id="72b73-105">Syntax</span></span>  
  
```  
HRESULT CreateInstanceEnumWmi (
   [in] BSTR                    strFilter,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
); 
```  

## <a name="parameters"></a><span data-ttu-id="72b73-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="72b73-106">Parameters</span></span>

`strFilter`    
<span data-ttu-id="72b73-107">[in]インスタンスが必要となるクラスの名前。</span><span class="sxs-lookup"><span data-stu-id="72b73-107">[in] The name of the class for which instances are desired.</span></span> <span data-ttu-id="72b73-108">このパラメーターを指定できません`null`です。</span><span class="sxs-lookup"><span data-stu-id="72b73-108">This parameter cannot be `null`.</span></span>

`lFlags`   
<span data-ttu-id="72b73-109">[in]この関数の動作に影響するフラグの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="72b73-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="72b73-110">次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="72b73-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="72b73-111">定数</span><span class="sxs-lookup"><span data-stu-id="72b73-111">Constant</span></span>  |<span data-ttu-id="72b73-112">[値]</span><span class="sxs-lookup"><span data-stu-id="72b73-112">Value</span></span>  |<span data-ttu-id="72b73-113">説明</span><span class="sxs-lookup"><span data-stu-id="72b73-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="72b73-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="72b73-114">0x20000</span></span> | <span data-ttu-id="72b73-115">場合は、関数のセットは、現在の接続のロケールのローカライズされた名前空間に格納されている修正済みの修飾子を取得します。</span><span class="sxs-lookup"><span data-stu-id="72b73-115">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="72b73-116">指定しない場合、セット、関数は、イミディ エイトの名前空間に格納されている修飾子のみを取得します。</span><span class="sxs-lookup"><span data-stu-id="72b73-116">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="72b73-117">0</span><span class="sxs-lookup"><span data-stu-id="72b73-117">0</span></span> | <span data-ttu-id="72b73-118">列挙体には、階層内のすべてのサブクラスとこれが含まれています。</span><span class="sxs-lookup"><span data-stu-id="72b73-118">The enumeration includes this and all subclasses in the hierarchy.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="72b73-119">1</span><span class="sxs-lookup"><span data-stu-id="72b73-119">1</span></span> | <span data-ttu-id="72b73-120">列挙体は、このクラスの純粋なインスタンスのみを含むおよびのサブクラスが見つかりません。 このクラスでプロパティを提供するすべてのインスタンスを除外します。</span><span class="sxs-lookup"><span data-stu-id="72b73-120">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="72b73-121">0x10</span><span class="sxs-lookup"><span data-stu-id="72b73-121">0x10</span></span> | <span data-ttu-id="72b73-122">フラグは、半同期呼び出しがします。</span><span class="sxs-lookup"><span data-stu-id="72b73-122">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="72b73-123">0x20</span><span class="sxs-lookup"><span data-stu-id="72b73-123">0x20</span></span> | <span data-ttu-id="72b73-124">この関数は、順方向専用の列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="72b73-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="72b73-125">呼び出しを許可しませんが、通常、順方向専用の列挙子は、高速および従来の列挙子よりも少ないメモリを使用して[クローン](clone.md)です。</span><span class="sxs-lookup"><span data-stu-id="72b73-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="72b73-126">0</span><span class="sxs-lookup"><span data-stu-id="72b73-126">0</span></span> | <span data-ttu-id="72b73-127">WMI は、リリースされるまで、enumration 内のオブジェクトへのポインターを保持します。</span><span class="sxs-lookup"><span data-stu-id="72b73-127">WMI retains pointers to objects in the enumration until they are released.</span></span> | 

<span data-ttu-id="72b73-128">推奨されるフラグは`WBEM_FLAG_RETURN_IMMEDIATELY`と`WBEM_FLAG_FORWARD_ONLY`最適なパフォーマンスをします。</span><span class="sxs-lookup"><span data-stu-id="72b73-128">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`  
<span data-ttu-id="72b73-129">[in]この値は、通常、`null`です。</span><span class="sxs-lookup"><span data-stu-id="72b73-129">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="72b73-130">ポインターはそれ以外の場合、 [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx)インスタンスを使用して、要求されたインスタンスを提供しているプロバイダーによって可能性があります。</span><span class="sxs-lookup"><span data-stu-id="72b73-130">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that may be used by the provider that is providing the requested instances.</span></span>

`ppEnum`  
<span data-ttu-id="72b73-131">[out]列挙子へのポインターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="72b73-131">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`  
<span data-ttu-id="72b73-132">[in]承認レベル。</span><span class="sxs-lookup"><span data-stu-id="72b73-132">[in] The authorization level.</span></span>

<span data-ttu-id="72b73-133">`impLevel` [in]権限借用レベルです。</span><span class="sxs-lookup"><span data-stu-id="72b73-133">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="72b73-134">[in]ポインター、 [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx)を現在の名前空間を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="72b73-134">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="72b73-135">[in]ユーザー名。</span><span class="sxs-lookup"><span data-stu-id="72b73-135">[in] The user name.</span></span> <span data-ttu-id="72b73-136">参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="72b73-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="72b73-137">[in]パスワードです。</span><span class="sxs-lookup"><span data-stu-id="72b73-137">[in] The password.</span></span> <span data-ttu-id="72b73-138">参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="72b73-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="72b73-139">[in]ユーザーのドメイン名。</span><span class="sxs-lookup"><span data-stu-id="72b73-139">[in] The domain name of the user.</span></span> <span data-ttu-id="72b73-140">参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="72b73-140">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="72b73-141">戻り値</span><span class="sxs-lookup"><span data-stu-id="72b73-141">Return value</span></span>

<span data-ttu-id="72b73-142">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="72b73-142">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="72b73-143">定数</span><span class="sxs-lookup"><span data-stu-id="72b73-143">Constant</span></span>  |<span data-ttu-id="72b73-144">[値]</span><span class="sxs-lookup"><span data-stu-id="72b73-144">Value</span></span>  |<span data-ttu-id="72b73-145">説明</span><span class="sxs-lookup"><span data-stu-id="72b73-145">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="72b73-146">0x80041003</span><span class="sxs-lookup"><span data-stu-id="72b73-146">0x80041003</span></span> | <span data-ttu-id="72b73-147">ユーザーには、指定したクラスのインスタンスを表示するアクセス許可がありません。</span><span class="sxs-lookup"><span data-stu-id="72b73-147">The user does not have permission to view instances of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="72b73-148">0x80041001</span><span class="sxs-lookup"><span data-stu-id="72b73-148">0x80041001</span></span> | <span data-ttu-id="72b73-149">不明なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="72b73-149">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="72b73-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="72b73-150">0x80041010</span></span> | <span data-ttu-id="72b73-151">`strFilter` は存在しません。</span><span class="sxs-lookup"><span data-stu-id="72b73-151">`strFilter` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="72b73-152">0x80041008</span><span class="sxs-lookup"><span data-stu-id="72b73-152">0x80041008</span></span> | <span data-ttu-id="72b73-153">パラメーターが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="72b73-153">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="72b73-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="72b73-154">0x80041006</span></span> | <span data-ttu-id="72b73-155">操作を完了するのに十分なメモリがあります。</span><span class="sxs-lookup"><span data-stu-id="72b73-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="72b73-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="72b73-156">0x80041033</span></span> | <span data-ttu-id="72b73-157">WMI は、おそらく停止および再起動されました。</span><span class="sxs-lookup"><span data-stu-id="72b73-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="72b73-158">呼び出す[ConnectServerWmi](connectserverwmi.md)もう一度です。</span><span class="sxs-lookup"><span data-stu-id="72b73-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="72b73-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="72b73-159">0x80041015</span></span> | <span data-ttu-id="72b73-160">リモート プロシージャ コール (RPC) リンクで、現在のプロセスと WMI との間に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="72b73-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="72b73-161">0</span><span class="sxs-lookup"><span data-stu-id="72b73-161">0</span></span> | <span data-ttu-id="72b73-162">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="72b73-162">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="72b73-163">コメント</span><span class="sxs-lookup"><span data-stu-id="72b73-163">Remarks</span></span>

<span data-ttu-id="72b73-164">この関数への呼び出しをラップする、[で iwbemservices::createclassenum](https://msdn.microsoft.com/library/aa392097(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="72b73-164">This function wraps a call to the [IWbemServices::CreateClassEnum](https://msdn.microsoft.com/library/aa392097(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="72b73-165">返された列挙子がゼロの要素を持つことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="72b73-165">Note that the returned enumerator can have zero elements.</span></span>

<span data-ttu-id="72b73-166">呼び出して追加のエラー情報を取得するには、関数呼び出しに失敗した場合、 [GetErrorInfo](geterrorinfo.md)関数。</span><span class="sxs-lookup"><span data-stu-id="72b73-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="72b73-167">要件</span><span class="sxs-lookup"><span data-stu-id="72b73-167">Requirements</span></span>  
 <span data-ttu-id="72b73-168">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="72b73-168">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72b73-169">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="72b73-169">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="72b73-170">**.NET framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="72b73-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72b73-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="72b73-171">See also</span></span>  
[<span data-ttu-id="72b73-172">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="72b73-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

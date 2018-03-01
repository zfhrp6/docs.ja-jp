---
title: "CreateClassEnumWmi 関数 (アンマネージ API リファレンス)"
description: "CreateClassEnumWmi 関数では、指定した条件に適合するすべてのクラスの列挙子を返します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- CreateClassEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateClassEnumWmi
helpviewer_keywords:
- CreateClassEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2058bad61af79244d211afb6a7661ca1642db070
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="createclassenumwmi-function"></a><span data-ttu-id="f9a55-103">CreateClassEnumWmi 関数</span><span class="sxs-lookup"><span data-stu-id="f9a55-103">CreateClassEnumWmi function</span></span>
<span data-ttu-id="f9a55-104">指定した選択条件を満たすすべてのクラスの列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="f9a55-104">Returns an enumerator for all classes that satisfy the specified selection criteria.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f9a55-105">構文</span><span class="sxs-lookup"><span data-stu-id="f9a55-105">Syntax</span></span>  
  
```  
HRESULT CreateClassEnumWmi (
   [in] BSTR                    strSuperclass,
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

## <a name="parameters"></a><span data-ttu-id="f9a55-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f9a55-106">Parameters</span></span>

`strSuperclass`    
<span data-ttu-id="f9a55-107">[in]ない場合`null`空白または親クラスの名前を指定する、列挙子は、このクラスのサブクラスのみを返します。</span><span class="sxs-lookup"><span data-stu-id="f9a55-107">[in] If not `null` or blank, specifies the name of a parent class; the enumerator returns only subclasses of this class.</span></span> <span data-ttu-id="f9a55-108">場合は`null`または空白と`lFlags`WBEM_FLAG_SHALLOW 場合、最上位クラス (親クラスを持たないクラス) だけを返します。</span><span class="sxs-lookup"><span data-stu-id="f9a55-108">If it is `null` or blank and `lFlags` is WBEM_FLAG_SHALLOW, returns only top-level classes (classes with no parent class).</span></span> <span data-ttu-id="f9a55-109">場合は`null`または空白と`lFlags`は`WBEM_FLAG_DEEP`、名前空間内のすべてのクラスを返します。</span><span class="sxs-lookup"><span data-stu-id="f9a55-109">If it is `null` or blank and `lFlags` is `WBEM_FLAG_DEEP`, returns all classes in the namespace.</span></span>

`lFlags`   
<span data-ttu-id="f9a55-110">[in]この関数の動作に影響するフラグの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="f9a55-110">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="f9a55-111">次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="f9a55-111">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="f9a55-112">定数</span><span class="sxs-lookup"><span data-stu-id="f9a55-112">Constant</span></span>  |<span data-ttu-id="f9a55-113">[値]</span><span class="sxs-lookup"><span data-stu-id="f9a55-113">Value</span></span>  |<span data-ttu-id="f9a55-114">説明</span><span class="sxs-lookup"><span data-stu-id="f9a55-114">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="f9a55-115">0x20000</span><span class="sxs-lookup"><span data-stu-id="f9a55-115">0x20000</span></span> | <span data-ttu-id="f9a55-116">場合は、関数のセットは、現在の接続のロケールのローカライズされた名前空間に格納されている修正済みの修飾子を取得します。</span><span class="sxs-lookup"><span data-stu-id="f9a55-116">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="f9a55-117">指定しない場合、セット、関数は、イミディ エイトの名前空間に格納されている修飾子のみを取得します。</span><span class="sxs-lookup"><span data-stu-id="f9a55-117">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="f9a55-118">0</span><span class="sxs-lookup"><span data-stu-id="f9a55-118">0</span></span> | <span data-ttu-id="f9a55-119">列挙には、このクラスではなく、階層ですべてのサブクラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f9a55-119">The enumeration includes all subclasses in the hierarchy, but not this class.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="f9a55-120">1</span><span class="sxs-lookup"><span data-stu-id="f9a55-120">1</span></span> | <span data-ttu-id="f9a55-121">列挙体は、このクラスの純粋なインスタンスのみを含むおよびのサブクラスが見つかりません。 このクラスでプロパティを提供するすべてのインスタンスを除外します。</span><span class="sxs-lookup"><span data-stu-id="f9a55-121">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="f9a55-122">0x10</span><span class="sxs-lookup"><span data-stu-id="f9a55-122">0x10</span></span> | <span data-ttu-id="f9a55-123">フラグは、半同期呼び出しがします。</span><span class="sxs-lookup"><span data-stu-id="f9a55-123">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="f9a55-124">0x20</span><span class="sxs-lookup"><span data-stu-id="f9a55-124">0x20</span></span> | <span data-ttu-id="f9a55-125">この関数は、順方向専用の列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="f9a55-125">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="f9a55-126">呼び出しを許可しませんが、通常、順方向専用の列挙子は、高速および従来の列挙子よりも少ないメモリを使用して[クローン](clone.md)です。</span><span class="sxs-lookup"><span data-stu-id="f9a55-126">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="f9a55-127">0</span><span class="sxs-lookup"><span data-stu-id="f9a55-127">0</span></span> | <span data-ttu-id="f9a55-128">WMI は、リリースされるまで、enumration 内のオブジェクトへのポインターを保持します。</span><span class="sxs-lookup"><span data-stu-id="f9a55-128">WMI retains pointers to objects in the enumration until they are released.</span></span> | 

<span data-ttu-id="f9a55-129">推奨されるフラグは`WBEM_FLAG_RETURN_IMMEDIATELY`と`WBEM_FLAG_FORWARD_ONLY`最適なパフォーマンスをします。</span><span class="sxs-lookup"><span data-stu-id="f9a55-129">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`  
<span data-ttu-id="f9a55-130">[in]この値は、通常、`null`です。</span><span class="sxs-lookup"><span data-stu-id="f9a55-130">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="f9a55-131">ポインターはそれ以外の場合、 [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx)要求されたクラスを提供しているプロバイダーで使用できるインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="f9a55-131">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppEnum`  
<span data-ttu-id="f9a55-132">[out]列挙子へのポインターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="f9a55-132">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`  
<span data-ttu-id="f9a55-133">[in]承認レベル。</span><span class="sxs-lookup"><span data-stu-id="f9a55-133">[in] The authorization level.</span></span>

<span data-ttu-id="f9a55-134">`impLevel`[in]権限借用レベルです。</span><span class="sxs-lookup"><span data-stu-id="f9a55-134">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="f9a55-135">[in]ポインター、 [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx)を現在の名前空間を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f9a55-135">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="f9a55-136">[in]ユーザー名。</span><span class="sxs-lookup"><span data-stu-id="f9a55-136">[in] The user name.</span></span> <span data-ttu-id="f9a55-137">参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="f9a55-137">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="f9a55-138">[in]パスワードです。</span><span class="sxs-lookup"><span data-stu-id="f9a55-138">[in] The password.</span></span> <span data-ttu-id="f9a55-139">参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="f9a55-139">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="f9a55-140">[in]ユーザーのドメイン名。</span><span class="sxs-lookup"><span data-stu-id="f9a55-140">[in] The domain name of the user.</span></span> <span data-ttu-id="f9a55-141">参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="f9a55-141">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="f9a55-142">戻り値</span><span class="sxs-lookup"><span data-stu-id="f9a55-142">Return value</span></span>

<span data-ttu-id="f9a55-143">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="f9a55-143">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f9a55-144">定数</span><span class="sxs-lookup"><span data-stu-id="f9a55-144">Constant</span></span>  |<span data-ttu-id="f9a55-145">[値]</span><span class="sxs-lookup"><span data-stu-id="f9a55-145">Value</span></span>  |<span data-ttu-id="f9a55-146">説明</span><span class="sxs-lookup"><span data-stu-id="f9a55-146">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="f9a55-147">0x80041003</span><span class="sxs-lookup"><span data-stu-id="f9a55-147">0x80041003</span></span> | <span data-ttu-id="f9a55-148">ユーザーには、1 つ以上の関数が返すことができるクラスを表示するアクセス許可がありません。</span><span class="sxs-lookup"><span data-stu-id="f9a55-148">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="f9a55-149">0x80041001</span><span class="sxs-lookup"><span data-stu-id="f9a55-149">0x80041001</span></span> | <span data-ttu-id="f9a55-150">不明なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f9a55-150">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="f9a55-151">0x80041010</span><span class="sxs-lookup"><span data-stu-id="f9a55-151">0x80041010</span></span> | <span data-ttu-id="f9a55-152">`strSuperClass` は存在しません。</span><span class="sxs-lookup"><span data-stu-id="f9a55-152">`strSuperClass` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f9a55-153">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f9a55-153">0x80041008</span></span> | <span data-ttu-id="f9a55-154">パラメーターが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="f9a55-154">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f9a55-155">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f9a55-155">0x80041006</span></span> | <span data-ttu-id="f9a55-156">操作を完了するのに十分なメモリがあります。</span><span class="sxs-lookup"><span data-stu-id="f9a55-156">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="f9a55-157">0x80041033</span><span class="sxs-lookup"><span data-stu-id="f9a55-157">0x80041033</span></span> | <span data-ttu-id="f9a55-158">WMI は、おそらく停止および再起動されました。</span><span class="sxs-lookup"><span data-stu-id="f9a55-158">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="f9a55-159">呼び出す[ConnectServerWmi](connectserverwmi.md)もう一度です。</span><span class="sxs-lookup"><span data-stu-id="f9a55-159">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="f9a55-160">0x80041015</span><span class="sxs-lookup"><span data-stu-id="f9a55-160">0x80041015</span></span> | <span data-ttu-id="f9a55-161">リモート プロシージャ コール (RPC) リンクで、現在のプロセスと WMI との間に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="f9a55-161">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f9a55-162">0</span><span class="sxs-lookup"><span data-stu-id="f9a55-162">0</span></span> | <span data-ttu-id="f9a55-163">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="f9a55-163">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f9a55-164">コメント</span><span class="sxs-lookup"><span data-stu-id="f9a55-164">Remarks</span></span>

<span data-ttu-id="f9a55-165">この関数への呼び出しをラップする、[で iwbemservices::createclassenum](https://msdn.microsoft.com/library/aa392095(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f9a55-165">This function wraps a call to the [IWbemServices::CreateClassEnum](https://msdn.microsoft.com/library/aa392095(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="f9a55-166">呼び出して追加のエラー情報を取得するには、関数呼び出しに失敗した場合、 [GetErrorInfo](geterrorinfo.md)関数。</span><span class="sxs-lookup"><span data-stu-id="f9a55-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="f9a55-167">必要条件</span><span class="sxs-lookup"><span data-stu-id="f9a55-167">Requirements</span></span>  
 <span data-ttu-id="f9a55-168">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f9a55-168">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9a55-169">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f9a55-169">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f9a55-170">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f9a55-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9a55-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9a55-171">See also</span></span>  
[<span data-ttu-id="f9a55-172">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f9a55-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

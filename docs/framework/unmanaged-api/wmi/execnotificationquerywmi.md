---
title: "ExecNotificationQueryWmi 関数 (アンマネージ API リファレンス)"
description: "ExecNotificationQueryWmi 関数は、イベントを受信するクエリを実行します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- ExecNotificationQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecNotificationQueryWmi
helpviewer_keywords:
- ExecNotificationQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d6dd0926d2262f8d0aa125b86755017a65a95a7f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="execnotificationquerywmi-function"></a><span data-ttu-id="583d9-103">ExecNotificationQueryWmi 関数</span><span class="sxs-lookup"><span data-stu-id="583d9-103">ExecNotificationQueryWmi function</span></span>
<span data-ttu-id="583d9-104">イベントを受信するクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="583d9-104">Executes a query to receive events.</span></span> <span data-ttu-id="583d9-105">呼び出しが、すぐに返され、受信したときに、呼び出し元がイベントの返された列挙子をポーリングすることです。</span><span class="sxs-lookup"><span data-stu-id="583d9-105">The call returns immediately, and the caller can poll the returned enumerator for events as they arrive.</span></span> <span data-ttu-id="583d9-106">返された列挙子を解放するには、クエリが取り消されます。</span><span class="sxs-lookup"><span data-stu-id="583d9-106">Releasing the returned enumerator cancels the query.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="583d9-107">構文</span><span class="sxs-lookup"><span data-stu-id="583d9-107">Syntax</span></span>  
  
```  
HRESULT ExecNotificationQueryWmi (
   [in] BSTR                    strQueryLanguage,
   [in] BSTR                    strQuery,
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

## <a name="parameters"></a><span data-ttu-id="583d9-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="583d9-108">Parameters</span></span>

`strQueryLanguage`    
<span data-ttu-id="583d9-109">[in]Windows 管理でサポートされる有効なクエリ言語での文字列です。</span><span class="sxs-lookup"><span data-stu-id="583d9-109">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="583d9-110">WMI クエリ言語の頭字語である"WQL"でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="583d9-110">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`  
<span data-ttu-id="583d9-111">[in]クエリのテキスト。</span><span class="sxs-lookup"><span data-stu-id="583d9-111">[in] The text of the query.</span></span> <span data-ttu-id="583d9-112">このパラメーターを指定できません`null`です。</span><span class="sxs-lookup"><span data-stu-id="583d9-112">This parameter cannot be `null`.</span></span>

`lFlags`   
<span data-ttu-id="583d9-113">[in]この関数の動作に影響する次の 2 つのフラグの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="583d9-113">[in] A combination of the following two flags that affect the behavior of this function.</span></span> <span data-ttu-id="583d9-114">これらの値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。</span><span class="sxs-lookup"><span data-stu-id="583d9-114">These values are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> 

| <span data-ttu-id="583d9-115">定数</span><span class="sxs-lookup"><span data-stu-id="583d9-115">Constant</span></span> | <span data-ttu-id="583d9-116">[値]</span><span class="sxs-lookup"><span data-stu-id="583d9-116">Value</span></span>  | <span data-ttu-id="583d9-117">説明</span><span class="sxs-lookup"><span data-stu-id="583d9-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="583d9-118">0x10</span><span class="sxs-lookup"><span data-stu-id="583d9-118">0x10</span></span> | <span data-ttu-id="583d9-119">フラグは、半同期呼び出しがします。</span><span class="sxs-lookup"><span data-stu-id="583d9-119">The flag causes a semisynchronous call.</span></span> <span data-ttu-id="583d9-120">このフラグが設定されていない場合、呼び出しが失敗します。</span><span class="sxs-lookup"><span data-stu-id="583d9-120">If this flag is not set, the call fails.</span></span> <span data-ttu-id="583d9-121">これは、イベントが継続的に、受信したため、ユーザーは、返された列挙子をポーリングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="583d9-121">This is because events are received continuously, which means the user must poll the returned enumerator.</span></span> <span data-ttu-id="583d9-122">この呼び出しを無期限にブロックするようにするが不可能です。</span><span class="sxs-lookup"><span data-stu-id="583d9-122">Blocking this call indefinitely makes that impossible.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="583d9-123">0x20</span><span class="sxs-lookup"><span data-stu-id="583d9-123">0x20</span></span> | <span data-ttu-id="583d9-124">この関数は、順方向専用の列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="583d9-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="583d9-125">呼び出しを許可しませんが、通常、順方向専用の列挙子は、高速および従来の列挙子よりも少ないメモリを使用して[クローン](clone.md)です。</span><span class="sxs-lookup"><span data-stu-id="583d9-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |

`pCtx`  
<span data-ttu-id="583d9-126">[in]この値は、通常、`null`です。</span><span class="sxs-lookup"><span data-stu-id="583d9-126">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="583d9-127">ポインターはそれ以外の場合、 [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx)要求イベントを提供しているプロバイダーで使用できるインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="583d9-127">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested events.</span></span> 

`ppEnum`  
<span data-ttu-id="583d9-128">[out]エラーが発生しなかった場合は、クエリの結果セット内のインスタンスを取得する呼び出し元を許可する列挙子へのポインターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="583d9-128">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="583d9-129">参照してください、[解説](#remarks)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="583d9-129">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`  
<span data-ttu-id="583d9-130">[in]承認レベル。</span><span class="sxs-lookup"><span data-stu-id="583d9-130">[in] The authorization level.</span></span>

<span data-ttu-id="583d9-131">`impLevel`[in]権限借用レベルです。</span><span class="sxs-lookup"><span data-stu-id="583d9-131">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="583d9-132">[in]ポインター、 [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx)を現在の名前空間を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="583d9-132">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="583d9-133">[in]ユーザー名。</span><span class="sxs-lookup"><span data-stu-id="583d9-133">[in] The user name.</span></span> <span data-ttu-id="583d9-134">参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="583d9-134">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="583d9-135">[in]パスワードです。</span><span class="sxs-lookup"><span data-stu-id="583d9-135">[in] The password.</span></span> <span data-ttu-id="583d9-136">参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="583d9-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="583d9-137">[in]ユーザーのドメイン名。</span><span class="sxs-lookup"><span data-stu-id="583d9-137">[in] The domain name of the user.</span></span> <span data-ttu-id="583d9-138">参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="583d9-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="583d9-139">戻り値</span><span class="sxs-lookup"><span data-stu-id="583d9-139">Return value</span></span>

<span data-ttu-id="583d9-140">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="583d9-140">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="583d9-141">定数</span><span class="sxs-lookup"><span data-stu-id="583d9-141">Constant</span></span>  |<span data-ttu-id="583d9-142">[値]</span><span class="sxs-lookup"><span data-stu-id="583d9-142">Value</span></span>  |<span data-ttu-id="583d9-143">説明</span><span class="sxs-lookup"><span data-stu-id="583d9-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="583d9-144">0x80041003</span><span class="sxs-lookup"><span data-stu-id="583d9-144">0x80041003</span></span> | <span data-ttu-id="583d9-145">ユーザーには、1 つ以上の関数が返すことができるクラスを表示するアクセス許可がありません。</span><span class="sxs-lookup"><span data-stu-id="583d9-145">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="583d9-146">0x80041001</span><span class="sxs-lookup"><span data-stu-id="583d9-146">0x80041001</span></span> | <span data-ttu-id="583d9-147">不明なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="583d9-147">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="583d9-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="583d9-148">0x80041008</span></span> | <span data-ttu-id="583d9-149">パラメーターが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="583d9-149">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="583d9-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="583d9-150">0x80041010</span></span> | <span data-ttu-id="583d9-151">クエリでは、存在しないクラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="583d9-151">The query specifies a class that does not exist.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | <span data-ttu-id="583d9-152">0x80042002</span><span class="sxs-lookup"><span data-stu-id="583d9-152">0x80042002</span></span> | <span data-ttu-id="583d9-153">イベントの配信にあまり有効桁数が要求されました。</span><span class="sxs-lookup"><span data-stu-id="583d9-153">Too much precision in delivery of events has been requested.</span></span> <span data-ttu-id="583d9-154">大規模なポーリング許容範囲を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="583d9-154">A larger polling tolerance must be specified.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | <span data-ttu-id="583d9-155">0x80042001</span><span class="sxs-lookup"><span data-stu-id="583d9-155">0x80042001</span></span> | <span data-ttu-id="583d9-156">クエリ requess Windows 管理より多くの情報を提供できます。</span><span class="sxs-lookup"><span data-stu-id="583d9-156">The query requess more information than Windows Management can provide.</span></span> <span data-ttu-id="583d9-157">これは、`HRESULT`イベント クエリが名前空間のすべてのオブジェクトをポーリングする要求の結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="583d9-157">This `HRESULT` is returned when an event query results in a request to poll all objects in a namespace.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="583d9-158">0x80041017</span><span class="sxs-lookup"><span data-stu-id="583d9-158">0x80041017</span></span> | <span data-ttu-id="583d9-159">クエリでは、構文エラーがありました。</span><span class="sxs-lookup"><span data-stu-id="583d9-159">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="583d9-160">0x80041018</span><span class="sxs-lookup"><span data-stu-id="583d9-160">0x80041018</span></span> | <span data-ttu-id="583d9-161">要求されたクエリ言語がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="583d9-161">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="583d9-162">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="583d9-162">0x8004106c</span></span> | <span data-ttu-id="583d9-163">クエリが複雑すぎます。</span><span class="sxs-lookup"><span data-stu-id="583d9-163">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="583d9-164">0x80041006</span><span class="sxs-lookup"><span data-stu-id="583d9-164">0x80041006</span></span> | <span data-ttu-id="583d9-165">操作を完了するのに十分なメモリがあります。</span><span class="sxs-lookup"><span data-stu-id="583d9-165">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="583d9-166">0x80041033</span><span class="sxs-lookup"><span data-stu-id="583d9-166">0x80041033</span></span> | <span data-ttu-id="583d9-167">WMI は、おそらく停止および再起動されました。</span><span class="sxs-lookup"><span data-stu-id="583d9-167">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="583d9-168">呼び出す[ConnectServerWmi](connectserverwmi.md)もう一度です。</span><span class="sxs-lookup"><span data-stu-id="583d9-168">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="583d9-169">0x80041015</span><span class="sxs-lookup"><span data-stu-id="583d9-169">0x80041015</span></span> | <span data-ttu-id="583d9-170">リモート プロシージャ コール (RPC) リンクで、現在のプロセスと WMI との間に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="583d9-170">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_UNPARSABLE_QUERY` | <span data-ttu-id="583d9-171">0x80041058</span><span class="sxs-lookup"><span data-stu-id="583d9-171">0x80041058</span></span> | <span data-ttu-id="583d9-172">クエリを解析できません。</span><span class="sxs-lookup"><span data-stu-id="583d9-172">The query cannot be parsed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="583d9-173">0</span><span class="sxs-lookup"><span data-stu-id="583d9-173">0</span></span> | <span data-ttu-id="583d9-174">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="583d9-174">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="583d9-175">コメント</span><span class="sxs-lookup"><span data-stu-id="583d9-175">Remarks</span></span>

<span data-ttu-id="583d9-176">この関数への呼び出しをラップする、 [IWbemServices::ExecNotificationQuery](https://msdn.microsoft.com/library/aa392105(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="583d9-176">This function wraps a call to the [IWbemServices::ExecNotificationQuery](https://msdn.microsoft.com/library/aa392105(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="583d9-177">関数から返された後に呼び出し元は、定期的に渡されます、返された`ppEnum`オブジェクトを[次](next.md)かどうか、提供されているイベントを表示する関数。</span><span class="sxs-lookup"><span data-stu-id="583d9-177">After the function returns, the caller periodically passes the returned `ppEnum` object to the [Next](next.md) function to see if any events are available.</span></span>

<span data-ttu-id="583d9-178">数に制限は`AND`と`OR`WQL クエリで使用できるキーワード。</span><span class="sxs-lookup"><span data-stu-id="583d9-178">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="583d9-179">多数の複雑なクエリで使用される WQL キーワードには、WMI を返す可能性があります、 `WBEM_E_QUOTA_VIOLATION` (または 0x8004106c) としてのエラー コード、`HRESULT`値。</span><span class="sxs-lookup"><span data-stu-id="583d9-179">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="583d9-180">WQL のキーワードの制限は、どの程度複雑なクエリがによって異なります。</span><span class="sxs-lookup"><span data-stu-id="583d9-180">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="583d9-181">呼び出して追加のエラー情報を取得するには、関数呼び出しに失敗した場合、 [GetErrorInfo](geterrorinfo.md)関数。</span><span class="sxs-lookup"><span data-stu-id="583d9-181">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="583d9-182">必要条件</span><span class="sxs-lookup"><span data-stu-id="583d9-182">Requirements</span></span>  
 <span data-ttu-id="583d9-183">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="583d9-183">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="583d9-184">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="583d9-184">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="583d9-185">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="583d9-185">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="583d9-186">関連項目</span><span class="sxs-lookup"><span data-stu-id="583d9-186">See also</span></span>  
[<span data-ttu-id="583d9-187">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="583d9-187">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

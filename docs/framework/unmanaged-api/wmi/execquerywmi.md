---
title: "ExecQueryWmi 関数 (アンマネージ API リファレンス)"
description: "ExecQueryWmi 関数は、オブジェクトを取得するクエリを実行します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ExecQueryWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ExecQueryWmi
helpviewer_keywords: ExecQueryWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ebd5463fd3b4109203e829da8e3683bbb79cf59
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="execquerywmi-function"></a><span data-ttu-id="53b71-103">ExecQueryWmi 関数</span><span class="sxs-lookup"><span data-stu-id="53b71-103">ExecQueryWmi function</span></span>
<span data-ttu-id="53b71-104">オブジェクトを取得するクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="53b71-104">Executes a query to retrieve objects.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="53b71-105">構文</span><span class="sxs-lookup"><span data-stu-id="53b71-105">Syntax</span></span>  
  
```  
HRESULT ExecQueryWmi (
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

## <a name="parameters"></a><span data-ttu-id="53b71-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="53b71-106">Parameters</span></span>

`strQueryLanguage`    
<span data-ttu-id="53b71-107">[in]Windows 管理でサポートされる有効なクエリ言語での文字列です。</span><span class="sxs-lookup"><span data-stu-id="53b71-107">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="53b71-108">WMI クエリ言語の頭字語である"WQL"でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="53b71-108">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`  
<span data-ttu-id="53b71-109">[in]クエリのテキスト。</span><span class="sxs-lookup"><span data-stu-id="53b71-109">[in] The text of the query.</span></span> <span data-ttu-id="53b71-110">このパラメーターを指定できません`null`です。</span><span class="sxs-lookup"><span data-stu-id="53b71-110">This parameter cannot be `null`.</span></span>

`lFlags`   
<span data-ttu-id="53b71-111">[in]この関数の動作に影響するフラグの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="53b71-111">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="53b71-112">次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="53b71-112">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

| <span data-ttu-id="53b71-113">定数</span><span class="sxs-lookup"><span data-stu-id="53b71-113">Constant</span></span> | <span data-ttu-id="53b71-114">値</span><span class="sxs-lookup"><span data-stu-id="53b71-114">Value</span></span>  | <span data-ttu-id="53b71-115">説明</span><span class="sxs-lookup"><span data-stu-id="53b71-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="53b71-116">0x20000</span><span class="sxs-lookup"><span data-stu-id="53b71-116">0x20000</span></span> | <span data-ttu-id="53b71-117">場合は、関数のセットは、現在の接続のロケールのローカライズされた名前空間に格納されている修正済みの修飾子を取得します。</span><span class="sxs-lookup"><span data-stu-id="53b71-117">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="53b71-118">指定しない場合、セット、関数は、イミディ エイトの名前空間に格納されている修飾子のみを取得します。</span><span class="sxs-lookup"><span data-stu-id="53b71-118">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="53b71-119">0x10</span><span class="sxs-lookup"><span data-stu-id="53b71-119">0x10</span></span> | <span data-ttu-id="53b71-120">フラグは、半同期呼び出しがします。</span><span class="sxs-lookup"><span data-stu-id="53b71-120">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="53b71-121">0x20</span><span class="sxs-lookup"><span data-stu-id="53b71-121">0x20</span></span> | <span data-ttu-id="53b71-122">この関数は、順方向専用の列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="53b71-122">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="53b71-123">呼び出しを許可しませんが、通常、順方向専用の列挙子は、高速および従来の列挙子よりも少ないメモリを使用して[クローン](clone.md)です。</span><span class="sxs-lookup"><span data-stu-id="53b71-123">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="53b71-124">0</span><span class="sxs-lookup"><span data-stu-id="53b71-124">0</span></span> | <span data-ttu-id="53b71-125">WMI は、リリースされるまで、enumration 内のオブジェクトへのポインターを保持します。</span><span class="sxs-lookup"><span data-stu-id="53b71-125">WMI retains pointers to objects in the enumration until they are released.</span></span> | 
| `WBEM_FLAG_ENSURE_LOCATABLE` | <span data-ttu-id="53b71-126">0x100</span><span class="sxs-lookup"><span data-stu-id="53b71-126">0x100</span></span> | <span data-ttu-id="53b71-127">返されるオブジェクトがあるのに十分な情報にためことにより、そのシステムのプロパティなど**_ _path**、 **_relpath**、および**__SERVER**、されない`null`です。</span><span class="sxs-lookup"><span data-stu-id="53b71-127">Ensures that any returned objects have enough information in them so that system properties, such as **__PATH**, **__RELPATH**, and **__SERVER**, are not `null`.</span></span> |
| `WBEM_FLAG_PROTOTYPE` | <span data-ttu-id="53b71-128">2</span><span class="sxs-lookup"><span data-stu-id="53b71-128">2</span></span> | <span data-ttu-id="53b71-129">このフラグは、プロトタイプの作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="53b71-129">This flag is used for prototyping.</span></span> <span data-ttu-id="53b71-130">クエリは実行されませんし、代わりに、よくある結果オブジェクトのようなオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="53b71-130">It does not execute the query and instead returns an object that looks like a typical result object.</span></span> |
| `WBEM_FLAG_DIRECT_READ` | <span data-ttu-id="53b71-131">0x200</span><span class="sxs-lookup"><span data-stu-id="53b71-131">0x200</span></span> | <span data-ttu-id="53b71-132">原因は直接、親クラス、または任意のサブクラスに関係なく指定されたクラスのプロバイダーへのアクセスです。</span><span class="sxs-lookup"><span data-stu-id="53b71-132">Causes direct access to the provider for the class specified without regard to its parent class or any subclasses.</span></span> |

<span data-ttu-id="53b71-133">推奨されるフラグは`WBEM_FLAG_RETURN_IMMEDIATELY`と`WBEM_FLAG_FORWARD_ONLY`最適なパフォーマンスをします。</span><span class="sxs-lookup"><span data-stu-id="53b71-133">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`  
<span data-ttu-id="53b71-134">[in]この値は、通常、`null`です。</span><span class="sxs-lookup"><span data-stu-id="53b71-134">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="53b71-135">ポインターはそれ以外の場合、 [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx)要求されたクラスを提供しているプロバイダーで使用できるインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="53b71-135">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppEnum`  
<span data-ttu-id="53b71-136">[out]エラーが発生しなかった場合は、クエリの結果セット内のインスタンスを取得する呼び出し元を許可する列挙子へのポインターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="53b71-136">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="53b71-137">クエリでは、0 個のインスタンスを含む結果セットを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="53b71-137">The query can have a result set with zero instances.</span></span> <span data-ttu-id="53b71-138">参照してください、[解説](#remarks)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="53b71-138">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`  
<span data-ttu-id="53b71-139">[in]承認レベル。</span><span class="sxs-lookup"><span data-stu-id="53b71-139">[in] The authorization level.</span></span>

<span data-ttu-id="53b71-140">`impLevel`[in]権限借用レベルです。</span><span class="sxs-lookup"><span data-stu-id="53b71-140">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="53b71-141">[in]ポインター、 [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx)を現在の名前空間を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="53b71-141">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="53b71-142">[in]ユーザー名。</span><span class="sxs-lookup"><span data-stu-id="53b71-142">[in] The user name.</span></span> <span data-ttu-id="53b71-143">参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="53b71-143">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="53b71-144">[in]パスワードです。</span><span class="sxs-lookup"><span data-stu-id="53b71-144">[in] The password.</span></span> <span data-ttu-id="53b71-145">参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="53b71-145">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="53b71-146">[in]ユーザーのドメイン名。</span><span class="sxs-lookup"><span data-stu-id="53b71-146">[in] The domain name of the user.</span></span> <span data-ttu-id="53b71-147">参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="53b71-147">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="53b71-148">戻り値</span><span class="sxs-lookup"><span data-stu-id="53b71-148">Return value</span></span>

<span data-ttu-id="53b71-149">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="53b71-149">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="53b71-150">定数</span><span class="sxs-lookup"><span data-stu-id="53b71-150">Constant</span></span>  |<span data-ttu-id="53b71-151">値</span><span class="sxs-lookup"><span data-stu-id="53b71-151">Value</span></span>  |<span data-ttu-id="53b71-152">説明</span><span class="sxs-lookup"><span data-stu-id="53b71-152">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="53b71-153">0x80041003</span><span class="sxs-lookup"><span data-stu-id="53b71-153">0x80041003</span></span> | <span data-ttu-id="53b71-154">ユーザーには、1 つ以上の関数が返すことができるクラスを表示するアクセス許可がありません。</span><span class="sxs-lookup"><span data-stu-id="53b71-154">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="53b71-155">0x80041001</span><span class="sxs-lookup"><span data-stu-id="53b71-155">0x80041001</span></span> | <span data-ttu-id="53b71-156">不明なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="53b71-156">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="53b71-157">0x80041008</span><span class="sxs-lookup"><span data-stu-id="53b71-157">0x80041008</span></span> | <span data-ttu-id="53b71-158">パラメーターが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="53b71-158">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="53b71-159">0x80041017</span><span class="sxs-lookup"><span data-stu-id="53b71-159">0x80041017</span></span> | <span data-ttu-id="53b71-160">クエリでは、構文エラーがありました。</span><span class="sxs-lookup"><span data-stu-id="53b71-160">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="53b71-161">0x80041018</span><span class="sxs-lookup"><span data-stu-id="53b71-161">0x80041018</span></span> | <span data-ttu-id="53b71-162">要求されたクエリ言語がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="53b71-162">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="53b71-163">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="53b71-163">0x8004106c</span></span> | <span data-ttu-id="53b71-164">クエリが複雑すぎます。</span><span class="sxs-lookup"><span data-stu-id="53b71-164">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="53b71-165">0x80041006</span><span class="sxs-lookup"><span data-stu-id="53b71-165">0x80041006</span></span> | <span data-ttu-id="53b71-166">操作を完了するのに十分なメモリがあります。</span><span class="sxs-lookup"><span data-stu-id="53b71-166">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="53b71-167">0x80041033</span><span class="sxs-lookup"><span data-stu-id="53b71-167">0x80041033</span></span> | <span data-ttu-id="53b71-168">WMI は、おそらく停止および再起動されました。</span><span class="sxs-lookup"><span data-stu-id="53b71-168">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="53b71-169">呼び出す[ConnectServerWmi](connectserverwmi.md)もう一度です。</span><span class="sxs-lookup"><span data-stu-id="53b71-169">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="53b71-170">0x80041015</span><span class="sxs-lookup"><span data-stu-id="53b71-170">0x80041015</span></span> | <span data-ttu-id="53b71-171">リモート プロシージャ コール (RPC) リンクで、現在のプロセスと WMI との間に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="53b71-171">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="53b71-172">0x80041002</span><span class="sxs-lookup"><span data-stu-id="53b71-172">0x80041002</span></span> | <span data-ttu-id="53b71-173">クエリでは、存在しないクラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="53b71-173">The query specifies a class that does not exist.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="53b71-174">0</span><span class="sxs-lookup"><span data-stu-id="53b71-174">0</span></span> | <span data-ttu-id="53b71-175">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="53b71-175">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="53b71-176">コメント</span><span class="sxs-lookup"><span data-stu-id="53b71-176">Remarks</span></span>

<span data-ttu-id="53b71-177">この関数への呼び出しをラップする、 [IWbemServices::ExecQuery](https://msdn.microsoft.com/library/aa392107(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="53b71-177">This function wraps a call to the [IWbemServices::ExecQuery](https://msdn.microsoft.com/library/aa392107(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="53b71-178">この関数で指定されたクエリの処理、`strQuery`パラメーターと、呼び出し元が、クエリの結果をアクセス列挙子を作成します。</span><span class="sxs-lookup"><span data-stu-id="53b71-178">This function processes the query specified in the `strQuery` parameter and creates an enumerator through which the caller can access the query results.</span></span> <span data-ttu-id="53b71-179">列挙子がへのポインター、 [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx)インターフェイス以外のクエリ結果で利用できるクラス オブジェクトのインスタンスである、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433(v=vs.85).aspx)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="53b71-179">The enumerator is a pointer to an [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx) interface; the query results are instances of class objects made available through the [IWbemClassObject](https://msdn.microsoft.com/library/aa391433(v=vs.85).aspx) interface.</span></span>

<span data-ttu-id="53b71-180">数に制限は`AND`と`OR`WQL クエリで使用できるキーワード。</span><span class="sxs-lookup"><span data-stu-id="53b71-180">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="53b71-181">多数の複雑なクエリで使用される WQL キーワードには、WMI を返す可能性があります、 `WBEM_E_QUOTA_VIOLATION` (または 0x8004106c) としてのエラー コード、`HRESULT`値。</span><span class="sxs-lookup"><span data-stu-id="53b71-181">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="53b71-182">WQL のキーワードの制限は、どの程度複雑なクエリがによって異なります。</span><span class="sxs-lookup"><span data-stu-id="53b71-182">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="53b71-183">呼び出して追加のエラー情報を取得するには、関数呼び出しに失敗した場合、 [GetErrorInfo](geterrorinfo.md)関数。</span><span class="sxs-lookup"><span data-stu-id="53b71-183">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="53b71-184">要件</span><span class="sxs-lookup"><span data-stu-id="53b71-184">Requirements</span></span>  
 <span data-ttu-id="53b71-185">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="53b71-185">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53b71-186">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="53b71-186">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="53b71-187">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="53b71-187">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53b71-188">関連項目</span><span class="sxs-lookup"><span data-stu-id="53b71-188">See also</span></span>  
[<span data-ttu-id="53b71-189">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="53b71-189">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

---
title: "ConnectServerWmi 関数 (アンマネージ API リファレンス)"
description: "ConnectServerWmi 関数では、DCOM を使用して、WMI 名前空間への接続を作成します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ConnectServerWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ConnectServerWmi
helpviewer_keywords: ConnectServerWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dc821bddf1d33ea1144fef0821b81cf027d8f92f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="connectserverwmi-function"></a><span data-ttu-id="62451-103">ConnectServerWmi 関数</span><span class="sxs-lookup"><span data-stu-id="62451-103">ConnectServerWmi function</span></span>
<span data-ttu-id="62451-104">指定したコンピューターで WMI 名前空間に使用する DCOM による接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="62451-104">Creates a connection through DCOM to a WMI namespace on a specified computer.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="62451-105">構文</span><span class="sxs-lookup"><span data-stu-id="62451-105">Syntax</span></span>  
  
```  
HRESULT ConnectServerWmi (
   [in] BSTR               strNetworkResource,
   [in] BSTR               strUser,
   [in] BSTR               strPassword,
   [in] BSTR               strLocale,
   [in] long               lSecurityFlags,
   [in] BSTR               strAuthority,
   [in] IWbemContext*      pCtx,
   [out] IWbemServices**   ppNamespace,
   [in] DWORD              impLevel, 
   [in] DWORD              authLevel
);
```  
## <a name="parameters"></a><span data-ttu-id="62451-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="62451-106">Parameters</span></span>

<span data-ttu-id="62451-107">`strNetworkResource`[in]有効なポインター`BSTR`正しい WMI 名前空間のオブジェクトのパスを格納しています。</span><span class="sxs-lookup"><span data-stu-id="62451-107">`strNetworkResource` [in] Pointer to a valid `BSTR` that contains the object path of the correct WMI namespace.</span></span> <span data-ttu-id="62451-108">参照してください、[解説](#remarks)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="62451-108">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="62451-109">`strUser`[in]有効なポインター`BSTR`ユーザー名を格納しています。</span><span class="sxs-lookup"><span data-stu-id="62451-109">`strUser` [in] A pointer to a valid `BSTR` that contains the user name.</span></span> <span data-ttu-id="62451-110">A`null`値が現在のセキュリティ コンテキストを示します。</span><span class="sxs-lookup"><span data-stu-id="62451-110">A `null` value indicates the current security context.</span></span> <span data-ttu-id="62451-111">ユーザーが現在のものとは異なるドメインから場合`strUser`円記号で区切られたドメインとユーザー名を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="62451-111">If the user is from a different domain than the current one, `strUser` can also contain the domain and user name separated by a backslash.</span></span> <span data-ttu-id="62451-112">`strUser`できますもあるでユーザー プリンシパル名 (UPN) を書式設定、として suhc  *userName@domainName*です。</span><span class="sxs-lookup"><span data-stu-id="62451-112">`strUser` can also be in user principal name (UPN) format, suhc as *userName@domainName*.</span></span> <span data-ttu-id="62451-113">参照してください、[解説](#remarks)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="62451-113">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="62451-114">`strPassword`[in]有効なポインター`BSTR`パスワードを格納しています。</span><span class="sxs-lookup"><span data-stu-id="62451-114">`strPassword` [in] A pointer to a valid `BSTR` that contains the password.</span></span> <span data-ttu-id="62451-115">A`null`現在のセキュリティ コンテキストを示します。</span><span class="sxs-lookup"><span data-stu-id="62451-115">A `null` indicates the current security context.</span></span> <span data-ttu-id="62451-116">空の文字列 ("")、有効な長さ 0 のパスワードを示します。</span><span class="sxs-lookup"><span data-stu-id="62451-116">An empty string ("") indicates a valid zero-length password.</span></span>

<span data-ttu-id="62451-117">`strLocale`[in]有効なポインター`BSTR`を示す、適切なロケール情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="62451-117">`strLocale` [in] A pointer to a valid `BSTR` that indicates the correct locale for information retrieval.</span></span> <span data-ttu-id="62451-118">Microsoft ロケールの識別子、文字列の形式は"MS\_*xxx*"ここで、 *xxx*ロケール識別子 (LCID) を示す 16 進数形式で文字列です。</span><span class="sxs-lookup"><span data-stu-id="62451-118">For Microsoft locale identifiers, the format of the string is "MS\_*xxx*", where *xxx* is a string in hexadecimal form that indicates the locale identifier (LCID).</span></span> <span data-ttu-id="62451-119">無効なロケールが指定されているかどうか、メソッドが返されます`WBEM_E_INVALID_PARAMETER`代わりに、サーバーの既定のロケールが使用されている Windows 7 を除きます。</span><span class="sxs-lookup"><span data-stu-id="62451-119">If an invalid locale is specified, the method returns `WBEM_E_INVALID_PARAMETER` except on Windows 7, where the default locale of the server is used instead.</span></span> <span data-ttu-id="62451-120">場合 ' null 1、現在のロケールを使用します。</span><span class="sxs-lookup"><span data-stu-id="62451-120">If \`null1, the current locale is used.</span></span> 
 
<span data-ttu-id="62451-121">`lSecurityFlags`[in]渡すフラグ、`ConnectServerWmi`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="62451-121">`lSecurityFlags` [in] Flags to pass to the `ConnectServerWmi` method.</span></span> <span data-ttu-id="62451-122">このパラメーターにゼロ (0) の値の結果への呼び出しで`ConnectServerWmi`サーバーへの接続が確立された後にのみを返すことです。</span><span class="sxs-lookup"><span data-stu-id="62451-122">A value of zero (0) for this parameter results in the call to `ConnectServerWmi` returning only after a connection to the server is established.</span></span> <span data-ttu-id="62451-123">これは、結果、応答していない無制限にサーバーが切断されたかどうか、アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="62451-123">This could result in an application not responding indefinitely if the server is broken.</span></span> <span data-ttu-id="62451-124">その他の有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="62451-124">The other valid values are:</span></span>

| <span data-ttu-id="62451-125">定数</span><span class="sxs-lookup"><span data-stu-id="62451-125">Constant</span></span>  | <span data-ttu-id="62451-126">[値]</span><span class="sxs-lookup"><span data-stu-id="62451-126">Value</span></span>  | <span data-ttu-id="62451-127">説明</span><span class="sxs-lookup"><span data-stu-id="62451-127">Description</span></span>  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | <span data-ttu-id="62451-128">0x40</span><span class="sxs-lookup"><span data-stu-id="62451-128">0x40</span></span> | <span data-ttu-id="62451-129">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="62451-129">Reserved for internal use.</span></span> <span data-ttu-id="62451-130">使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="62451-130">Do not use.</span></span> |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | <span data-ttu-id="62451-131">0x80</span><span class="sxs-lookup"><span data-stu-id="62451-131">0x80</span></span> | <span data-ttu-id="62451-132">`ConnectServerWmi`2 分以内を返します。</span><span class="sxs-lookup"><span data-stu-id="62451-132">`ConnectServerWmi` returns in two minutes or less.</span></span> |

<span data-ttu-id="62451-133">`strAuthority`[in]ユーザーのドメイン名。</span><span class="sxs-lookup"><span data-stu-id="62451-133">`strAuthority` [in] The domain name of the user.</span></span> <span data-ttu-id="62451-134">次の値のいずれかを取ります。</span><span class="sxs-lookup"><span data-stu-id="62451-134">It can have the following values:</span></span>

| <span data-ttu-id="62451-135">[値]</span><span class="sxs-lookup"><span data-stu-id="62451-135">Value</span></span> | <span data-ttu-id="62451-136">説明</span><span class="sxs-lookup"><span data-stu-id="62451-136">Description</span></span> |
|---------|---------|
| <span data-ttu-id="62451-137">空白</span><span class="sxs-lookup"><span data-stu-id="62451-137">blank</span></span> | <span data-ttu-id="62451-138">NTLM 認証を使用すると、し、現在のユーザー NTLM ドメインを使用します。</span><span class="sxs-lookup"><span data-stu-id="62451-138">NTLM authentication is used, and the NTLM domain of the current user is used.</span></span> <span data-ttu-id="62451-139">場合`strUser`ドメイン (推奨される場所) を指定します。 ここで指定してはなりませんがします。</span><span class="sxs-lookup"><span data-stu-id="62451-139">If `strUser` specifies the domain (the recommended location), it must not be specified here.</span></span> <span data-ttu-id="62451-140">この関数を返します`WBEM_E_INVALID_PARAMETER`両方のパラメーターでドメインを指定する場合。</span><span class="sxs-lookup"><span data-stu-id="62451-140">The function returns `WBEM_E_INVALID_PARAMETER` if you specify the domain in both parameters.</span></span> |
| <span data-ttu-id="62451-141">Kerberos:*プリンシパル名*</span><span class="sxs-lookup"><span data-stu-id="62451-141">Kerberos:*principal name*</span></span> | <span data-ttu-id="62451-142">Kerberos 認証を使用して、このパラメーターには、Kerberos プリンシパル名が含まれています。</span><span class="sxs-lookup"><span data-stu-id="62451-142">Kerberos authentication is used, and this parameter contains a Kerberos principal name.</span></span> |
| <span data-ttu-id="62451-143">NTLMDOMAIN:*ドメイン名*</span><span class="sxs-lookup"><span data-stu-id="62451-143">NTLMDOMAIN:*domain name*</span></span> | <span data-ttu-id="62451-144">NT LAN Manager 認証を使用して、このパラメーターには、NTLM ドメイン名が含まれています。</span><span class="sxs-lookup"><span data-stu-id="62451-144">NT LAN Manager authentication is used, and this parameter contains an NTLM domain name.</span></span> |

`pCtx`   
<span data-ttu-id="62451-145">[in]このパラメーターは、通常、`null`です。</span><span class="sxs-lookup"><span data-stu-id="62451-145">[in] Typically, this parameter is is `null`.</span></span> <span data-ttu-id="62451-146">ポインターはそれ以外の場合、 [IWbemContext](https://msdn.microsoft.com/library/aa391465%28v=vs.85%29.aspx)オブジェクトが 1 つ以上の動的クラス プロバイダーで必要です。</span><span class="sxs-lookup"><span data-stu-id="62451-146">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465%28v=vs.85%29.aspx) object required by one or more dynamic class providers.</span></span> 

`ppNamespace`  
<span data-ttu-id="62451-147">[out]ポインターを受け取る関数が戻るとき、 [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx)オブジェクトを指定した名前空間にバインドします。</span><span class="sxs-lookup"><span data-stu-id="62451-147">[out] When the function returns, receives a pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object bound to the specified namespace.</span></span> <span data-ttu-id="62451-148">指すように設定されている`null`ときにエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="62451-148">It is set to point to `null` when there is an error.</span></span>

`impLevel`  
<span data-ttu-id="62451-149">[in]権限借用レベルです。</span><span class="sxs-lookup"><span data-stu-id="62451-149">[in] The impersonation level.</span></span>

`authLevel`  
<span data-ttu-id="62451-150">[in]承認レベル。</span><span class="sxs-lookup"><span data-stu-id="62451-150">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="62451-151">戻り値</span><span class="sxs-lookup"><span data-stu-id="62451-151">Return value</span></span>

<span data-ttu-id="62451-152">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="62451-152">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="62451-153">定数</span><span class="sxs-lookup"><span data-stu-id="62451-153">Constant</span></span>  |<span data-ttu-id="62451-154">[値]</span><span class="sxs-lookup"><span data-stu-id="62451-154">Value</span></span>  |<span data-ttu-id="62451-155">説明</span><span class="sxs-lookup"><span data-stu-id="62451-155">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="62451-156">0x80041001</span><span class="sxs-lookup"><span data-stu-id="62451-156">0x80041001</span></span> | <span data-ttu-id="62451-157">一般的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="62451-157">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="62451-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="62451-158">0x80041008</span></span> | <span data-ttu-id="62451-159">パラメーターが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="62451-159">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="62451-160">0x80041006</span><span class="sxs-lookup"><span data-stu-id="62451-160">0x80041006</span></span> | <span data-ttu-id="62451-161">操作を完了するのに十分なメモリがあります。</span><span class="sxs-lookup"><span data-stu-id="62451-161">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="62451-162">0</span><span class="sxs-lookup"><span data-stu-id="62451-162">0</span></span> | <span data-ttu-id="62451-163">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="62451-163">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="62451-164">コメント</span><span class="sxs-lookup"><span data-stu-id="62451-164">Remarks</span></span>

<span data-ttu-id="62451-165">この関数への呼び出しをラップする、 [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="62451-165">This function wraps a call to the [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) method.</span></span>

 <span data-ttu-id="62451-166">既定の名前空間へのローカル アクセスの`strNetworkResource`単純なオブジェクトのパスを指定できます:"root \default"または"\\.\root\default"です。</span><span class="sxs-lookup"><span data-stu-id="62451-166">For local access to the default namespace, `strNetworkResource` can be a simple object path: "root\default" or "\\.\root\default".</span></span> <span data-ttu-id="62451-167">リモート コンピューター上の既定の名前空間にアクセスするため、COM または Microsoft と互換性のあるネットワークを使用して、コンピューター名を含める:"\\myserver\root\default"です。</span><span class="sxs-lookup"><span data-stu-id="62451-167">For access to the default namespace on a remote computer using COM or Microsoft-compatible networking, include the computer name: "\\myserver\root\default".</span></span> <span data-ttu-id="62451-168">コンピューター名は、DNS 名または IP アドレス使用することができますも。</span><span class="sxs-lookup"><span data-stu-id="62451-168">The computer name also can be a DNS name or IP address.</span></span> <span data-ttu-id="62451-169">`ConnectServerWmi`関数は、IPv6 を実行するコンピューターとも接続できます IPv6 アドレスを使用します。</span><span class="sxs-lookup"><span data-stu-id="62451-169">The `ConnectServerWmi` function can also connect with computers running IPv6 using an IPv6 address.</span></span>

<span data-ttu-id="62451-170">`strUser`空の文字列にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="62451-170">`strUser` cannot be an empty string.</span></span> <span data-ttu-id="62451-171">ドメインが指定されている場合`strAuthority`、その必要がありますいないに含めることも`strUser`、または、関数を返します`WBEM_E_INVALID_PARAMETER`です。</span><span class="sxs-lookup"><span data-stu-id="62451-171">If the domain is specified in `strAuthority`, it must not also be included in `strUser`, or the function returns `WBEM_E_INVALID_PARAMETER`.</span></span>


## <a name="requirements"></a><span data-ttu-id="62451-172">必要条件</span><span class="sxs-lookup"><span data-stu-id="62451-172">Requirements</span></span>  
 <span data-ttu-id="62451-173">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="62451-173">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62451-174">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="62451-174">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="62451-175">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="62451-175">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62451-176">関連項目</span><span class="sxs-lookup"><span data-stu-id="62451-176">See also</span></span>  
[<span data-ttu-id="62451-177">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="62451-177">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

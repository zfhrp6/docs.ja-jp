---
title: "&lt;localServiceSettings&gt; 要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0658549c-3f65-46dd-8c5c-9895441ed734
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1e251c226484788b7ebc059cd68caf1f3c150c62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltlocalservicesettingsgt-element"></a><span data-ttu-id="9290a-102">&lt;localServiceSettings&gt; 要素</span><span class="sxs-lookup"><span data-stu-id="9290a-102">&lt;localServiceSettings&gt; element</span></span>
<span data-ttu-id="9290a-103">このバインディングのローカル サービスのセキュリティ設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="9290a-103">Specifies the security settings of a local service for this binding.</span></span>  
  
 <span data-ttu-id="9290a-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="9290a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="9290a-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="9290a-105">\<bindings></span></span>  
<span data-ttu-id="9290a-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="9290a-106">\<customBinding></span></span>  
<span data-ttu-id="9290a-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="9290a-107">\<binding></span></span>  
<span data-ttu-id="9290a-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="9290a-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9290a-109">構文</span><span class="sxs-lookup"><span data-stu-id="9290a-109">Syntax</span></span>  
  
```xml  
<security>  
   <localServiceSettings detectReplays="Boolean"  
      inactivityTimeout="TimeSpan"  
      issuedCookieLifeTime="TimeSpan"  
      maxCachedCookies="Integer"   
      maxClockSkew="TimeSpan"   
      maxPendingSessions="Integer"  
      maxStatefulNegotiations="Integer"  
      negotiationTimeout="TimeSpan"  
      reconnectTransportOnFailure="Boolean"  
            replayCacheSize="Integer"  
      replayWindow="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      timestampValidityDuration="TimeSpan" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9290a-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="9290a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9290a-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="9290a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9290a-112">属性</span><span class="sxs-lookup"><span data-stu-id="9290a-112">Attributes</span></span>  
  
|<span data-ttu-id="9290a-113">属性</span><span class="sxs-lookup"><span data-stu-id="9290a-113">Attribute</span></span>|<span data-ttu-id="9290a-114">説明</span><span class="sxs-lookup"><span data-stu-id="9290a-114">Description</span></span>|  
|---------------|-----------------|  
|`detectReplays`|<span data-ttu-id="9290a-115">チャネルに対するリプレイ攻撃を検出し、自動的に処理するかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="9290a-115">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="9290a-116">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="9290a-116">The default is `false`.</span></span>|  
|`inactivityTimeout`|<span data-ttu-id="9290a-117">チャネルがタイムアウトまで待機する非アクティブな期間を指定する、正の <xref:System.TimeSpan>。既定値は "01:00:00" です。</span><span class="sxs-lookup"><span data-stu-id="9290a-117">A positive <xref:System.TimeSpan> that specifies the duration of inactivity the channel waits before it times out. The default is "01:00:00".</span></span>|  
|`issuedCookieLifeTime`|<span data-ttu-id="9290a-118">すべての新しいセキュリティ クッキーに発行される有効期間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="9290a-118">A <xref:System.TimeSpan> that specifies the lifetime issued to all new security cookies.</span></span> <span data-ttu-id="9290a-119">有効期間を超えるクッキーは、再利用され、再度ネゴシエートされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9290a-119">Cookies that exceed their lifetime are recycled and need to be negotiated again.</span></span> <span data-ttu-id="9290a-120">既定値は、"10:00:00" です。</span><span class="sxs-lookup"><span data-stu-id="9290a-120">The default value is "10:00:00".</span></span>|  
|`maxCachedCookies`|<span data-ttu-id="9290a-121">キャッシュできるクッキーの最大数を指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="9290a-121">A positive integer that specifies the maximum number of cookies that can be cached.</span></span> <span data-ttu-id="9290a-122">既定値は 1000 です。</span><span class="sxs-lookup"><span data-stu-id="9290a-122">The default is 1000.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="9290a-123">通信している双方の 2 つのシステム クロックのずれの最長時間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="9290a-123">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="9290a-124">既定値は、"00:05:00" です。</span><span class="sxs-lookup"><span data-stu-id="9290a-124">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="9290a-125">この値が既定値に設定されている場合、受信側はメッセージが受信された時間より前後最大 5 分間の送信時間タイム スタンプを持つメッセージを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="9290a-125">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="9290a-126">送信時間テストにパスしないメッセージは拒否されます。</span><span class="sxs-lookup"><span data-stu-id="9290a-126">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="9290a-127">この設定は、`replayWindow` 属性と組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="9290a-127">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxPendingSessions`|<span data-ttu-id="9290a-128">サービスがサポートする保留状態のセキュリティ セッションの最大数を指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="9290a-128">A positive integer that specifies the maximum number of pending security sessions that the service supports.</span></span> <span data-ttu-id="9290a-129">この制限に達すると、すべての新しいクライアントが SOAP エラーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="9290a-129">When this limit is reached, all new clients receive SOAP faults.</span></span> <span data-ttu-id="9290a-130">既定値は 1000 です。</span><span class="sxs-lookup"><span data-stu-id="9290a-130">The default value is 1000.</span></span>|  
|`maxStatefulNegotiations`|<span data-ttu-id="9290a-131">同時にアクティブにできるセキュリティ ネゴシエーションの数を指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="9290a-131">A positive integer that specifies the number of security negotiations that can be active concurrently.</span></span> <span data-ttu-id="9290a-132">制限を超えるネゴシエーション セッションはキューに置かれ、制限内に空きができた場合にのみ完了できます。</span><span class="sxs-lookup"><span data-stu-id="9290a-132">Negotiation sessions in excess of the limit are queued and can only be completed when a space below the limit becomes available.</span></span> <span data-ttu-id="9290a-133">既定値は 1024 です。</span><span class="sxs-lookup"><span data-stu-id="9290a-133">The default value is 1024.</span></span>|  
|`negotiationTimeout`|<span data-ttu-id="9290a-134">チャネルによって使用されるセキュリティ ポリシーの有効期間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="9290a-134">A <xref:System.TimeSpan> that specifies the lifetime of the security policy used by channel.</span></span> <span data-ttu-id="9290a-135">有効期間が切れると、チャネルは新しいセキュリティ ポリシーについてクライアントと再度ネゴシエートします。</span><span class="sxs-lookup"><span data-stu-id="9290a-135">When the time expires, the channel renegotiates with the client for a new security policy.</span></span> <span data-ttu-id="9290a-136">既定値は、"00:02:00" です。</span><span class="sxs-lookup"><span data-stu-id="9290a-136">The default value is "00:02:00".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="9290a-137">WS-ReliableMessaging を使用した接続が、トランスポート エラーの後再接続を試みるかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="9290a-137">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="9290a-138">既定値は `true` です。これは、再接続の試行が無限に行われることを意味します。</span><span class="sxs-lookup"><span data-stu-id="9290a-138">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="9290a-139">循環は非アクティブ タイムアウトにより破棄され、再接続できない場合はチャネルが例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="9290a-139">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="9290a-140">リプレイ検証で使用される、キャッシュ済みの nonce 数を指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="9290a-140">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="9290a-141">この制限を越えると、最も古い nonce が削除され、新しいメッセージ用に新しい nonce が作成されます。</span><span class="sxs-lookup"><span data-stu-id="9290a-141">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="9290a-142">既定値は 500000 です。</span><span class="sxs-lookup"><span data-stu-id="9290a-142">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="9290a-143">個別のメッセージ nonce の有効期間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="9290a-143">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="9290a-144">この期間が過ぎると、以前に送信されたメッセージと同じ nonce を持つメッセージは受け入れられません。</span><span class="sxs-lookup"><span data-stu-id="9290a-144">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="9290a-145">この属性は、リプレイ攻撃を防ぐために `maxClockSkew` 属性と組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="9290a-145">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="9290a-146">攻撃者は、メッセージのリプレイ ウィンドウの期限が切れた後にメッセージをリプレイする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9290a-146">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="9290a-147">ただし、このメッセージは `maxClockSkew` テストに失敗します。このテストは、メッセージが受信された時間の前後指定時間以内の送信時間タイムスタンプを持つメッセージを拒否します。</span><span class="sxs-lookup"><span data-stu-id="9290a-147">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="9290a-148">イニシエーターがセキュリティ セッションのキーを更新するまでの期間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="9290a-148">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="9290a-149">既定値は "10:00:00" です。</span><span class="sxs-lookup"><span data-stu-id="9290a-149">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="9290a-150">キーの更新中に、前のセッション キーが受信メッセージで有効な時間間隔を指定する <xref:System.TimeSpan> です。</span><span class="sxs-lookup"><span data-stu-id="9290a-150">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="9290a-151">既定値は "00:05:00" です。</span><span class="sxs-lookup"><span data-stu-id="9290a-151">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="9290a-152">キーの更新中、クライアントおよびサーバーは、常に、利用可能な最新のキーを使用してメッセージを送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9290a-152">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="9290a-153">どちらのパーティも、ロールオーバー時間に達するまで、前のセッション キーで保護された受信メッセージを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="9290a-153">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="9290a-154">タイムスタンプの有効期間を指定する正の <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="9290a-154">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="9290a-155">既定値は "00:15:00" です。</span><span class="sxs-lookup"><span data-stu-id="9290a-155">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9290a-156">子要素</span><span class="sxs-lookup"><span data-stu-id="9290a-156">Child Elements</span></span>  
 <span data-ttu-id="9290a-157">なし。</span><span class="sxs-lookup"><span data-stu-id="9290a-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9290a-158">親要素</span><span class="sxs-lookup"><span data-stu-id="9290a-158">Parent Elements</span></span>  
  
|<span data-ttu-id="9290a-159">要素</span><span class="sxs-lookup"><span data-stu-id="9290a-159">Element</span></span>|<span data-ttu-id="9290a-160">説明</span><span class="sxs-lookup"><span data-stu-id="9290a-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9290a-161">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="9290a-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="9290a-162">カスタム バインドのセキュリティ オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="9290a-162">Specifies the security options for a custom binding.</span></span>|  
|[<span data-ttu-id="9290a-163">\<secureConversationBootstrap ></span><span class="sxs-lookup"><span data-stu-id="9290a-163">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="9290a-164">セキュリティで保護されたメッセージ交換サービスの開始に使用される既定値を指定します。</span><span class="sxs-lookup"><span data-stu-id="9290a-164">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9290a-165">コメント</span><span class="sxs-lookup"><span data-stu-id="9290a-165">Remarks</span></span>  
 <span data-ttu-id="9290a-166">この設定は、サービスのセキュリティ ポリシーの一部として公開されず、クライアントのバインディングには影響を与えないため、ローカルです。</span><span class="sxs-lookup"><span data-stu-id="9290a-166">The settings are local because they are not published as part of the security policy of the service and do not affect the client's binding.</span></span>  
  
 <span data-ttu-id="9290a-167">`localServiceSecuritySettings` 要素の以下の属性は、サービス拒否 (DOS) セキュリティ攻撃を軽減するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9290a-167">The following attributes of the `localServiceSecuritySettings` element can help mitigate a denial-of-service (DOS) security attack:</span></span>  
  
-   <span data-ttu-id="9290a-168">`maxCachedCookies`: SPNEGO または SSL の各ネゴシエーションの実行後にサーバーによってキャッシュされる、期限付きの SecurityContextTokens の最大数を制御します。</span><span class="sxs-lookup"><span data-stu-id="9290a-168">`maxCachedCookies`: controls the maximum number of time-bounded SecurityContextTokens that are cached by the server after doing SPNEGO or SSL negotiation.</span></span>  
  
-   <span data-ttu-id="9290a-169">`issuedCookieLifetime`: SPNEGO または SSL の各ネゴシエーションに続いてサーバーが発行する SecurityContextTokens の有効期限を制御します。</span><span class="sxs-lookup"><span data-stu-id="9290a-169">`issuedCookieLifetime`: controls the lifetime of the SecurityContextTokens that are issued by the server following SPNEGO or SSL negotiation.</span></span> <span data-ttu-id="9290a-170">サーバーは、この期間だけ SecurityContextTokens をキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="9290a-170">The server caches the SecurityContextTokens for this period of time.</span></span>  
  
-   <span data-ttu-id="9290a-171">`maxPendingSessions`: サーバーで確立されているが、そのアプリケーション メッセージが処理されていない、セキュリティで保護されたメッセージ交換の最大数を制御します。</span><span class="sxs-lookup"><span data-stu-id="9290a-171">`maxPendingSessions`: controls the maximum number of secure conversations that are established at the server but for which no application messages have been processed.</span></span> <span data-ttu-id="9290a-172">このクォータは、クライアントが、セキュリティで保護されたメッセージ交換をサービスで確立しないようにします。それによって、サービスはクライアントごとの状態を保持できますが、それらの状態を使用することはありません。</span><span class="sxs-lookup"><span data-stu-id="9290a-172">This quota prevents clients from establishing secure conversations at the service, thereby causing the service to maintain state for each client, but never using them.</span></span>  
  
-   <span data-ttu-id="9290a-173">`inactivityTimeout`: サービスが、セキュリティで保護されたメッセージ交換を、それに対するアプリケーション メッセージを受信しなくても維持する最長時間を制御します。</span><span class="sxs-lookup"><span data-stu-id="9290a-173">`inactivityTimeout`: controls the maximum time that the service keeps a secure conversation alive without ever receiving an application message on it.</span></span> <span data-ttu-id="9290a-174">このクォータは、クライアントが、セキュリティで保護されたメッセージ交換をサービスで確立しないようにします。それによって、サービスはクライアントごとの状態を保持できますが、それらの状態を使用することはありません。</span><span class="sxs-lookup"><span data-stu-id="9290a-174">This quota prevents clients from establishing secure conversations at the service, thereby causing the service to maintain state for each client, but never using them.</span></span>  
  
 <span data-ttu-id="9290a-175">セキュリティで保護されたメッセージ交換セッションでは、バインディングの `inactivityTimeout` 属性および `receiveTimeout` 属性の両方が、セッション タイムアウトに影響します。</span><span class="sxs-lookup"><span data-stu-id="9290a-175">In a secure conversation session, note that both `inactivityTimeout` and the `receiveTimeout` attributes on the binding affect session timeout.</span></span> <span data-ttu-id="9290a-176">2 つのうち短い方が、タイムアウトが発生する時間を決定します。</span><span class="sxs-lookup"><span data-stu-id="9290a-176">The shorter of the two determines when timeouts occur.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9290a-177">関連項目</span><span class="sxs-lookup"><span data-stu-id="9290a-177">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalServiceSettings%2A>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="9290a-178">バインディング</span><span class="sxs-lookup"><span data-stu-id="9290a-178">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="9290a-179">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="9290a-179">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="9290a-180">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="9290a-180">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="9290a-181">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="9290a-181">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="9290a-182">方法: SecurityBindingElement を使用してカスタム バインディングを作成します。</span><span class="sxs-lookup"><span data-stu-id="9290a-182">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="9290a-183">カスタム バインディングのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="9290a-183">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)

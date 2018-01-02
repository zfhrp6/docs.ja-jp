---
title: "&lt;localClientSettings&gt; 要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e906564eb86a2fcd7a82c194bac65416bbeab518
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltlocalclientsettingsgt-element"></a><span data-ttu-id="8bfd4-102">&lt;localClientSettings&gt; 要素</span><span class="sxs-lookup"><span data-stu-id="8bfd4-102">&lt;localClientSettings&gt; element</span></span>
<span data-ttu-id="8bfd4-103">このバインディングのローカル クライアントのセキュリティ設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-103">Specifies the security settings of a local client for this binding.</span></span>  
  
 <span data-ttu-id="8bfd4-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="8bfd4-104">\<system.serviceModel></span></span>  
<span data-ttu-id="8bfd4-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="8bfd4-105">\<bindings></span></span>  
<span data-ttu-id="8bfd4-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8bfd4-106">\<customBinding></span></span>  
<span data-ttu-id="8bfd4-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="8bfd4-107">\<binding></span></span>  
<span data-ttu-id="8bfd4-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="8bfd4-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bfd4-109">構文</span><span class="sxs-lookup"><span data-stu-id="8bfd4-109">Syntax</span></span>  
  
```xml  
<security>  
   <localClientSettings cacheCookies="Boolean"  
      cookieRenewalThresholdPercentage="Integer"  
      detectReplays="Boolean"  
      maxClockSkew="TimeSpan"  
      maxCookieCachingTime="TimeSpan"  
      reconnectTransportOnFailure="Boolean"  
      replayCacheSize="Integer"  
      replayWindow="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      timestampValidityDuration="TimeSpan" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8bfd4-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8bfd4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8bfd4-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8bfd4-112">属性</span><span class="sxs-lookup"><span data-stu-id="8bfd4-112">Attributes</span></span>  
  
|<span data-ttu-id="8bfd4-113">属性</span><span class="sxs-lookup"><span data-stu-id="8bfd4-113">Attribute</span></span>|<span data-ttu-id="8bfd4-114">説明</span><span class="sxs-lookup"><span data-stu-id="8bfd4-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheCookies`|<span data-ttu-id="8bfd4-115">クッキーのキャッシュが有効かどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-115">A Boolean value that specifies whether cookie caching is enabled.</span></span> <span data-ttu-id="8bfd4-116">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-116">The default is `false`.</span></span>|  
|`cookieRenewalThresholdPercentage`|<span data-ttu-id="8bfd4-117">更新できるクッキーの最大パーセンテージを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-117">An integer that specifies the maximum percentage of cookies that can be renewed.</span></span> <span data-ttu-id="8bfd4-118">この値は、0 ～ 100 (0 と 100を含む) のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-118">This value should be between 0 and 100 inclusively.</span></span> <span data-ttu-id="8bfd4-119">既定値は 90 です。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-119">The default is 90.</span></span>|  
|`detectReplays`|<span data-ttu-id="8bfd4-120">チャネルに対するリプレイ攻撃を検出し、自動的に処理するかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-120">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="8bfd4-121">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-121">The default is `false`.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="8bfd4-122">通信している双方の 2 つのシステム クロックのずれの最長時間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-122">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="8bfd4-123">既定値は、"00:05:00" です。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-123">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="8bfd4-124">この値が既定値に設定されている場合、受信側はメッセージが受信された時間より前後最大 5 分間の送信時間タイム スタンプを持つメッセージを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-124">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="8bfd4-125">送信時間テストにパスしないメッセージは拒否されます。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-125">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="8bfd4-126">この設定は、`replayWindow` 属性と組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-126">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxCookieCachingTime`|<span data-ttu-id="8bfd4-127">クッキーの最長有効期間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-127">A <xref:System.TimeSpan> that specifies the maximum lifetime of cookies.</span></span> <span data-ttu-id="8bfd4-128">デフォルト値は "10675199.02:48:05.4775807" です。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-128">The default value is "10675199.02:48:05.4775807".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="8bfd4-129">WS-ReliableMessaging を使用した接続が、トランスポート エラーの後再接続を試みるかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-129">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="8bfd4-130">既定値は `true` です。これは、再接続の試行が無限に行われることを意味します。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-130">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="8bfd4-131">循環は非アクティブ タイムアウトにより破棄され、再接続できない場合はチャネルが例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-131">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="8bfd4-132">リプレイ検証で使用される、キャッシュ済みの nonce 数を指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-132">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="8bfd4-133">この制限を越えると、最も古い nonce が削除され、新しいメッセージ用に新しい nonce が作成されます。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-133">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="8bfd4-134">既定値は 500000 です。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-134">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="8bfd4-135">個別のメッセージ nonce の有効期間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-135">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="8bfd4-136">この期間が過ぎると、以前に送信されたメッセージと同じ nonce を持つメッセージは受け入れられません。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-136">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="8bfd4-137">この属性は、リプレイ攻撃を防ぐために `maxClockSkew` 属性と組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-137">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="8bfd4-138">攻撃者は、メッセージのリプレイ ウィンドウの期限が切れた後にメッセージをリプレイする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-138">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="8bfd4-139">ただし、このメッセージは `maxClockSkew` テストに失敗します。このテストは、メッセージが受信された時間の前後指定時間以内の送信時間タイムスタンプを持つメッセージを拒否します。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-139">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="8bfd4-140">イニシエーターがセキュリティ セッションのキーを更新するまでの期間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-140">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="8bfd4-141">既定値は "10:00:00" です。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-141">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="8bfd4-142">キーの更新中に、前のセッション キーが受信メッセージで有効な時間間隔を指定する <xref:System.TimeSpan> です。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-142">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="8bfd4-143">既定値は "00:05:00" です。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-143">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="8bfd4-144">キーの更新中、クライアントおよびサーバーは、常に、利用可能な最新のキーを使用してメッセージを送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-144">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="8bfd4-145">どちらのパーティも、ロールオーバー時間に達するまで、前のセッション キーで保護された受信メッセージを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-145">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="8bfd4-146">タイムスタンプの有効期間を指定する正の <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-146">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="8bfd4-147">既定値は "00:15:00" です。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-147">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8bfd4-148">子要素</span><span class="sxs-lookup"><span data-stu-id="8bfd4-148">Child Elements</span></span>  
 <span data-ttu-id="8bfd4-149">なし</span><span class="sxs-lookup"><span data-stu-id="8bfd4-149">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8bfd4-150">親要素</span><span class="sxs-lookup"><span data-stu-id="8bfd4-150">Parent Elements</span></span>  
  
|<span data-ttu-id="8bfd4-151">要素</span><span class="sxs-lookup"><span data-stu-id="8bfd4-151">Element</span></span>|<span data-ttu-id="8bfd4-152">説明</span><span class="sxs-lookup"><span data-stu-id="8bfd4-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8bfd4-153">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="8bfd4-153">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="8bfd4-154">カスタム バインドのセキュリティ オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-154">Specifies the security options for a custom binding.</span></span>|  
|[<span data-ttu-id="8bfd4-155">\<secureConversationBootstrap ></span><span class="sxs-lookup"><span data-stu-id="8bfd4-155">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="8bfd4-156">セキュリティで保護されたメッセージ交換サービスの開始に使用される既定値を指定します。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-156">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bfd4-157">コメント</span><span class="sxs-lookup"><span data-stu-id="8bfd4-157">Remarks</span></span>  
 <span data-ttu-id="8bfd4-158">この設定は、サービスのセキュリティ ポリシーから派生する設定ではないという点でローカルです。</span><span class="sxs-lookup"><span data-stu-id="8bfd4-158">The settings are local in the sense that they are not settings derived from the security policy of the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bfd4-159">参照</span><span class="sxs-lookup"><span data-stu-id="8bfd4-159">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="8bfd4-160">バインディング</span><span class="sxs-lookup"><span data-stu-id="8bfd4-160">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="8bfd4-161">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="8bfd4-161">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="8bfd4-162">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="8bfd4-162">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="8bfd4-163">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8bfd4-163">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="8bfd4-164">方法 : SecurityBindingElement を使用してカスタム バインディングを作成する</span><span class="sxs-lookup"><span data-stu-id="8bfd4-164">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="8bfd4-165">カスタム バインド セキュリティ</span><span class="sxs-lookup"><span data-stu-id="8bfd4-165">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)

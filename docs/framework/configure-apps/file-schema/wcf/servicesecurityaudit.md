---
title: '&lt;serviceSecurityAudit&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba517369-a034-4f8e-a2c4-66517716062b
caps.latest.revision: "17"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f0c708c19761f6086e1b5c2fdd15904c76fe3de9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicesecurityauditgt"></a><span data-ttu-id="e99e1-102">&lt;serviceSecurityAudit&gt;</span><span class="sxs-lookup"><span data-stu-id="e99e1-102">&lt;serviceSecurityAudit&gt;</span></span>
<span data-ttu-id="e99e1-103">サービス操作中にセキュリティ イベントの監査を有効にする設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="e99e1-103">Specifies settings that enable auditing of security events during service operations.</span></span>  
  
 <span data-ttu-id="e99e1-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e99e1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e99e1-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="e99e1-105">\<behaviors></span></span>  
<span data-ttu-id="e99e1-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e99e1-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e99e1-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="e99e1-107">\<behavior></span></span>  
<span data-ttu-id="e99e1-108">\<serviceSecurityAudit ></span><span class="sxs-lookup"><span data-stu-id="e99e1-108">\<serviceSecurityAudit></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e99e1-109">構文</span><span class="sxs-lookup"><span data-stu-id="e99e1-109">Syntax</span></span>  
  
```xml  
<serviceSecurityAudit   
   auditLogLocation="Default/Application/Security"  
   messageAuthenticationAuditLevel= None/Success/Failure/SuccessAndFailure"   serviceAuthorizationAuditLevel="None/Success/Failure/SuccessAndFailure"  
   suppressAuditFailure="Boolean"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e99e1-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e99e1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e99e1-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e99e1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e99e1-112">属性</span><span class="sxs-lookup"><span data-stu-id="e99e1-112">Attributes</span></span>  
  
|<span data-ttu-id="e99e1-113">属性</span><span class="sxs-lookup"><span data-stu-id="e99e1-113">Attribute</span></span>|<span data-ttu-id="e99e1-114">説明</span><span class="sxs-lookup"><span data-stu-id="e99e1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e99e1-115">auditLogLocation</span><span class="sxs-lookup"><span data-stu-id="e99e1-115">auditLogLocation</span></span>|<span data-ttu-id="e99e1-116">監査ログの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="e99e1-116">Specifies the location of the audit log.</span></span> <span data-ttu-id="e99e1-117">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="e99e1-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e99e1-118">-既定値: セキュリティ イベントはログに書き込ま、アプリケーション イベント ログおよび Windows XP に Windows Server 2003 および Windows Vista で。</span><span class="sxs-lookup"><span data-stu-id="e99e1-118">-   Default: Security events are written to the application log on Windows XP, and to the Event Log on Windows Server 2003 and Windows Vista.</span></span><br /><span data-ttu-id="e99e1-119">アプリケーション: 監査イベントには、アプリケーション イベント ログが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="e99e1-119">-   Application: Audit events are written to the Application Event Log.</span></span><br /><span data-ttu-id="e99e1-120">セキュリティ: 監査イベントには、セキュリティ イベント ログが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="e99e1-120">-   Security: Audit events are written to the Security Event Log.</span></span><br /><br /> <span data-ttu-id="e99e1-121">既定値は Default です。</span><span class="sxs-lookup"><span data-stu-id="e99e1-121">The default value is Default.</span></span> <span data-ttu-id="e99e1-122">詳細については、「<xref:System.ServiceModel.AuditLogLocation>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e99e1-122">For more information, see <xref:System.ServiceModel.AuditLogLocation>.</span></span>|  
|<span data-ttu-id="e99e1-123">suppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="e99e1-123">suppressAuditFailure</span></span>|<span data-ttu-id="e99e1-124">監査ログへの書き込みエラーを非表示にする動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="e99e1-124">A Boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span><br /><br /> <span data-ttu-id="e99e1-125">アプリケーションには、監査ログへの書き込みエラーを通知する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e99e1-125">Applications should be notified for failures of writing to the audit log.</span></span> <span data-ttu-id="e99e1-126">アプリケーションが監査エラーを処理するように設計されていない場合は、この属性を使用して、監査ログへの書き込みでのエラーが表示されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e99e1-126">If your application is not designed to handle audit failures, you should use this attribute to suppress failures in writing to the audit log.</span></span><br /><br /> <span data-ttu-id="e99e1-127">この属性が `true` の場合、監査イベントの書き込み試行の結果発生する例外 (ただし、OutOfMemoryException、StackOverFlowException、ThreadAbortException、および ArgumentException を除く) はシステムによって処理され、アプリケーションには伝達されません。</span><span class="sxs-lookup"><span data-stu-id="e99e1-127">If this attribute is `true`, exceptions other than OutOfMemoryException, StackOverFlowException, ThreadAbortException, and ArgumentException that result from attempts to write audit events are handled by the system, and are not propagated to the application.</span></span> <span data-ttu-id="e99e1-128">この属性が `false` の場合、監査イベントの書き込み試行の結果発生する例外は、すべてアプリケーションまで渡されます。</span><span class="sxs-lookup"><span data-stu-id="e99e1-128">If this attribute is `false`, all exceptions that result from attempts to write audit events are passed up to the application.</span></span><br /><br /> <span data-ttu-id="e99e1-129">既定値は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="e99e1-129">The default is `true`.</span></span>|  
|<span data-ttu-id="e99e1-130">serviceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="e99e1-130">serviceAuthorizationAuditLevel</span></span>|<span data-ttu-id="e99e1-131">監査ログに記録される承認イベントの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="e99e1-131">Specifies the types of authorization events that are recorded in the audit log.</span></span> <span data-ttu-id="e99e1-132">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="e99e1-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e99e1-133">-None: サービス承認イベントの監査が実行されます。</span><span class="sxs-lookup"><span data-stu-id="e99e1-133">-   None: No auditing of service authorization events is performed.</span></span><br /><span data-ttu-id="e99e1-134">-Success: 成功したサービス承認イベントだけが監査されます。</span><span class="sxs-lookup"><span data-stu-id="e99e1-134">-   Success: Only successful service authorization events are audited.</span></span><br /><span data-ttu-id="e99e1-135">-エラー: 失敗したサービス承認イベントだけが監査されます。</span><span class="sxs-lookup"><span data-stu-id="e99e1-135">-   Failure: Only failure service authorization events are audited.</span></span><br /><span data-ttu-id="e99e1-136">-SuccessAndFailure: 両方サービス承認イベントの成功と失敗を監査します。</span><span class="sxs-lookup"><span data-stu-id="e99e1-136">-   SuccessAndFailure: Both success and failure service authorization events are audited.</span></span><br /><br /> <span data-ttu-id="e99e1-137">既定値は None です。</span><span class="sxs-lookup"><span data-stu-id="e99e1-137">The default value is None.</span></span> <span data-ttu-id="e99e1-138">詳細については、「<xref:System.ServiceModel.AuditLevel>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e99e1-138">For more information, see <xref:System.ServiceModel.AuditLevel>.</span></span>|  
|<span data-ttu-id="e99e1-139">messageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="e99e1-139">messageAuthenticationAuditLevel</span></span>|<span data-ttu-id="e99e1-140">ログに記録されるメッセージ認証監査イベントの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="e99e1-140">Specifies the type of message authentication audit events logged.</span></span> <span data-ttu-id="e99e1-141">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="e99e1-141">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e99e1-142">-None: 監査イベントがありませんが生成されます。</span><span class="sxs-lookup"><span data-stu-id="e99e1-142">-   None: No audit events are generated.</span></span><br /><span data-ttu-id="e99e1-143">-Success: 成功したセキュリティ (メッセージ署名の検証、暗号、およびトークンの検証を含む完全な検証) イベントだけが記録されます。</span><span class="sxs-lookup"><span data-stu-id="e99e1-143">-   Success: Only successful security (full validation including message signature validation, cipher, and token validation) events are logged.</span></span><br /><span data-ttu-id="e99e1-144">-エラー: 失敗したイベントだけが記録されます。</span><span class="sxs-lookup"><span data-stu-id="e99e1-144">-   Failure: Only failure events are logged.</span></span><br /><span data-ttu-id="e99e1-145">の両方 SuccessAndFailure: 成功と失敗のイベントが記録されます。</span><span class="sxs-lookup"><span data-stu-id="e99e1-145">-   SuccessAndFailure: Both success and failure events are logged.</span></span><br /><br /> <span data-ttu-id="e99e1-146">既定値は None です。</span><span class="sxs-lookup"><span data-stu-id="e99e1-146">The default value is None.</span></span> <span data-ttu-id="e99e1-147">詳細については、「<xref:System.ServiceModel.AuditLevel>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e99e1-147">For more information, see <xref:System.ServiceModel.AuditLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e99e1-148">子要素</span><span class="sxs-lookup"><span data-stu-id="e99e1-148">Child Elements</span></span>  
 <span data-ttu-id="e99e1-149">なし。</span><span class="sxs-lookup"><span data-stu-id="e99e1-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e99e1-150">親要素</span><span class="sxs-lookup"><span data-stu-id="e99e1-150">Parent Elements</span></span>  
  
|<span data-ttu-id="e99e1-151">要素</span><span class="sxs-lookup"><span data-stu-id="e99e1-151">Element</span></span>|<span data-ttu-id="e99e1-152">説明</span><span class="sxs-lookup"><span data-stu-id="e99e1-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e99e1-153">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="e99e1-153">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="e99e1-154">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="e99e1-154">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e99e1-155">コメント</span><span class="sxs-lookup"><span data-stu-id="e99e1-155">Remarks</span></span>  
 <span data-ttu-id="e99e1-156">この構成要素は、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 認証イベントの監査に使用されます。</span><span class="sxs-lookup"><span data-stu-id="e99e1-156">This configuraton element is used to audit [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] authentication events.</span></span> <span data-ttu-id="e99e1-157">監査を有効にすると、成功した認証、失敗した認証、またはその両方を監査できます。</span><span class="sxs-lookup"><span data-stu-id="e99e1-157">When auditing is enabled, either successful or failed authentication attempts (or both) can be audited.</span></span> <span data-ttu-id="e99e1-158">イベントは、3 種類のイベント ログ (アプリケーション ログ、セキュリティ ログ、およびオペレーティング システムのバージョンに対する既定のログ) のいずれかに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="e99e1-158">The events are written to one of three event logs: application, security, or the default log for the operating system version.</span></span> <span data-ttu-id="e99e1-159">イベント ログはすべて、Windows イベント ビューアーを使用して表示できます。</span><span class="sxs-lookup"><span data-stu-id="e99e1-159">The event logs can all be viewed using the Windows Event viewer.</span></span>  
  
 <span data-ttu-id="e99e1-160">この構成要素を使用する詳細な例についてを参照してください。[サービス監査動作](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md)です。</span><span class="sxs-lookup"><span data-stu-id="e99e1-160">For a detailed example of using this configuration element, see [Service Auditing Behavior](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md).</span></span>  
  
 <span data-ttu-id="e99e1-161">監査イベントは既定で、Windows XP の場合はアプリケーション ログに、Windows Server 2003 と Windows Vista の場合はセキュリティ ログに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e99e1-161">By default, on Windows XP the audit events can be seen in the Application Log; while on Windows Server 2003 and Windows Vista, the audit events can be seen in the Security Log.</span></span> <span data-ttu-id="e99e1-162">監査イベントの場所は、`auditLogLocation` 属性を "Application" または "Security" に設定することによって指定できます。</span><span class="sxs-lookup"><span data-stu-id="e99e1-162">The location of audit events can be specified by setting the `auditLogLocation` attribute to 'Application' or 'Security'.</span></span> <span data-ttu-id="e99e1-163">詳細については、次を参照してください。[する方法: セキュリティ イベントの監査](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)です。</span><span class="sxs-lookup"><span data-stu-id="e99e1-163">For more information, see [How to: Audit Security Events](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).</span></span> <span data-ttu-id="e99e1-164">イベントをセキュリティ ログに書き込む場合は、[ローカル セキュリティ ポリシー] -> [オブジェクト アクセスの監査] で、[成功] と [失敗] の各チェック ボックスをオンにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e99e1-164">If the events are written in the Security Log, the LocalSecurityPolicy-> Enable Object Access should be set for "Success" and "Failure".</span></span>  
  
 <span data-ttu-id="e99e1-165">イベント ログを調べる場合、監査イベントのソースは "ServiceModel Audit 3.0.0.0" です。</span><span class="sxs-lookup"><span data-stu-id="e99e1-165">When looking at the event log, the source of the audit events is "ServiceModel Audit 3.0.0.0".</span></span> <span data-ttu-id="e99e1-166">メッセージ認証監査レコードには "MessageAuthentication" のカテゴリ、サービス承認監査レコードには "ServiceAuthorization" のカテゴリが設定されます。</span><span class="sxs-lookup"><span data-stu-id="e99e1-166">Message authentication audit records have a category of "MessageAuthentication" while service authorization audit records have a category of 'ServiceAuthorization'.</span></span>  
  
 <span data-ttu-id="e99e1-167">メッセージ認証監査イベントは、メッセージの改ざんや期限切れの有無、クライアントによるサービス認証の成否などに適用されます。</span><span class="sxs-lookup"><span data-stu-id="e99e1-167">Message authentication audit events cover whether the message was tampered with, whether the message has expired and whether the client can authenticate to the service.</span></span> <span data-ttu-id="e99e1-168">このイベントでは、認証の成功または失敗に関する情報とクライアント ID、およびメッセージ送信先のエンドポイントとそのメッセージに関連付けられたアクションに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="e99e1-168">They provide information about whether the authentication succeeded or failed along with the identity of the client and the endpoint the message was sent to along with the action associated with the message.</span></span>  
  
 <span data-ttu-id="e99e1-169">サービス承認監査イベントは、サービス承認マネージャーによって決定される承認に適用されます。</span><span class="sxs-lookup"><span data-stu-id="e99e1-169">Service authorization audit events cover the authorization decision made by a service authorization manager.</span></span> <span data-ttu-id="e99e1-170">このイベントでは、承認の成功または失敗に関する情報とクライアント ID、メッセージ送信先のエンドポイント、そのメッセージに関連付けられたアクション、受信メッセージから生成された承認コンテキストの ID、およびアクセス決定を行った承認マネージャーの種類に関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="e99e1-170">They provide information about whether authorization succeeded of failed along with the identity of the client, the endpoint the message was sent to, the action associated with the message, the identifier of the authorization context that was generated from the incoming message and the type of the authorization manager that made the access decision.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e99e1-171">例</span><span class="sxs-lookup"><span data-stu-id="e99e1-171">Example</span></span>  
  
```xml  
<system.serviceModel>  
   <serviceBehaviors>  
      <behavior name="NewBehavior">  
         <serviceSecurityAudit auditLogLocation="Application"   
             suppressAuditFailure="true"  
             serviceAuthorizationAuditLevel="Success"   
             messageAuthenticationAuditLevel="Success" />  
      </behavior>  
   </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e99e1-172">関連項目</span><span class="sxs-lookup"><span data-stu-id="e99e1-172">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceSecurityAuditElement>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 [<span data-ttu-id="e99e1-173">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="e99e1-173">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="e99e1-174">監査</span><span class="sxs-lookup"><span data-stu-id="e99e1-174">Auditing</span></span>](../../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [<span data-ttu-id="e99e1-175">方法: セキュリティ イベントの監査</span><span class="sxs-lookup"><span data-stu-id="e99e1-175">How to: Audit Security Events</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)  
 [<span data-ttu-id="e99e1-176">サービス監査動作</span><span class="sxs-lookup"><span data-stu-id="e99e1-176">Service Auditing Behavior</span></span>](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md)

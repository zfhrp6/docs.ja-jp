---
title: "方法 : サービスで使用するカスタム承認マネージャーを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Communication Foundation, extending
- OperationRequirement class
ms.assetid: 6214afde-44c1-4bf5-ba07-5ad6493620ea
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cba64767aaac4092f3c6103f7417a9d707b9a380
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a><span data-ttu-id="5fcd5-102">方法 : サービスで使用するカスタム承認マネージャーを作成する</span><span class="sxs-lookup"><span data-stu-id="5fcd5-102">How to: Create a Custom Authorization Manager for a Service</span></span>
<span data-ttu-id="5fcd5-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 内の識別モデル インフラストラクチャでは、拡張性のあるクレーム ベースの承認モデルがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-103">The Identity Model infrastructure in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] supports an extensible claims-based authorization model.</span></span> <span data-ttu-id="5fcd5-104">クレームはトークンから抽出され、状況に応じてカスタム承認ポリシーによって処理されてから、<xref:System.IdentityModel.Policy.AuthorizationContext> に格納されます。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-104">Claims are extracted from tokens and optionally processed by custom authorization policies and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="5fcd5-105">承認マネージャーは、<xref:System.IdentityModel.Policy.AuthorizationContext> 内のクレームを検査して承認に関する決定を行います。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-105">An authorization manager examines the claims in the <xref:System.IdentityModel.Policy.AuthorizationContext> to make authorization decisions.</span></span>  
  
 <span data-ttu-id="5fcd5-106">既定では、承認に関する決定は、<xref:System.ServiceModel.ServiceAuthorizationManager> クラスによって行われますが、カスタム承認マネージャーを作成することによってオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-106">By default, authorization decisions are made by the <xref:System.ServiceModel.ServiceAuthorizationManager> class; however these decisions can be overridden by creating a custom authorization manager.</span></span> <span data-ttu-id="5fcd5-107">カスタム承認マネージャーを作成するには、<xref:System.ServiceModel.ServiceAuthorizationManager> から派生するクラスを作成し、<xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-107">To create a custom authorization manager, create a class that derives from <xref:System.ServiceModel.ServiceAuthorizationManager> and implement <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="5fcd5-108">承認に関する決定は、<xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> メソッド内で行われます。このメソッドは、アクセスが許可されている場合は `true` を返し、拒否されている場合は `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-108">Authorization decisions are made in the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method, which returns `true` when access is granted and `false` when access is denied.</span></span>  
  
 <span data-ttu-id="5fcd5-109">承認決定がメッセージ本文の内容に依存する場合は、<xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-109">If the authorization decision depends on the contents of the message body, use the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method.</span></span>  
  
 <span data-ttu-id="5fcd5-110">パフォーマンスの問題があるので、可能であればアプリケーションを再デザインして、承認決定でメッセージ本文にアクセスする必要がないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-110">Because of performance issues, if possible you should redesign your application so that the authorization decision does not require access to the message body.</span></span>  
  
 <span data-ttu-id="5fcd5-111">サービスのカスタム承認マネージャーは、コードまたは構成に登録できます。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-111">Registration of the custom authorization manager for a service can be done in code or configuration.</span></span>  
  
### <a name="to-create-a-custom-authorization-manager"></a><span data-ttu-id="5fcd5-112">カスタム承認マネージャーを作成するには</span><span class="sxs-lookup"><span data-stu-id="5fcd5-112">To create a custom authorization manager</span></span>  
  
1.  <span data-ttu-id="5fcd5-113"><xref:System.ServiceModel.ServiceAuthorizationManager> クラスからクラスを派生させます。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-113">Derive a class from the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
     [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]  
  
2.  <span data-ttu-id="5fcd5-114"><xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-114">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method.</span></span>  
  
     <span data-ttu-id="5fcd5-115"><xref:System.ServiceModel.OperationContext> メソッドに渡される <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> を使用して、承認に関する決定を行います。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-115">Use the <xref:System.ServiceModel.OperationContext> that is passed to the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method to make authorization decisions.</span></span>  
  
     <span data-ttu-id="5fcd5-116">承認に関する決定を行うために、<xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> メソッドを使用してカスタム クレーム `http://www.contoso.com/claims/allowedoperation` を検索する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-116">The following code example uses the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> method to find the custom claim `http://www.contoso.com/claims/allowedoperation` to make an authorization decision.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
     [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]  
  
### <a name="to-register-a-custom-authorization-manager-using-code"></a><span data-ttu-id="5fcd5-117">コードを使用してカスタム承認マネージャーを登録するには</span><span class="sxs-lookup"><span data-stu-id="5fcd5-117">To register a custom authorization manager using code</span></span>  
  
1.  <span data-ttu-id="5fcd5-118">カスタム承認マネージャーのインスタンスを作成し、これを <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> プロパティに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-118">Create an instance of the custom authorization manager and assign it to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> property.</span></span>  
  
     <span data-ttu-id="5fcd5-119"><xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> には、<xref:System.ServiceModel.ServiceHostBase.Authorization%2A> プロパティを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-119">The <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> can be accessed using <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> property.</span></span>  
  
     <span data-ttu-id="5fcd5-120">`MyServiceAuthorizationManager` カスタム承認マネージャーを登録するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-120">The following code example registers the `MyServiceAuthorizationManager` custom authorization manager.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
     [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]  
  
### <a name="to-register-a-custom-authorization-manager-using-configuration"></a><span data-ttu-id="5fcd5-121">構成を使用してカスタム承認マネージャーを登録するには</span><span class="sxs-lookup"><span data-stu-id="5fcd5-121">To register a custom authorization manager using configuration</span></span>  
  
1.  <span data-ttu-id="5fcd5-122">サービスの構成ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-122">Open the configuration file for the service.</span></span>  
  
2.  <span data-ttu-id="5fcd5-123">追加、 [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)を[\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)です。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).</span></span>  
  
     <span data-ttu-id="5fcd5-124">[ \<ServiceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)、追加、`serviceAuthorizationManagerType`属性し、その値をカスタム承認マネージャーを表す型に設定します。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-124">To the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md), add a `serviceAuthorizationManagerType` attribute and set its value to the type that represents the custom authorization manager.</span></span>  
  
3.  <span data-ttu-id="5fcd5-125">クライアントとサービスの間の通信をセキュリティで保護するバインディングを追加します。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-125">Add a binding that secures the communication between the client and service.</span></span>  
  
     <span data-ttu-id="5fcd5-126">この通信用に選択されたバインディングによって、<xref:System.IdentityModel.Policy.AuthorizationContext> に追加されるクレームが決まります。これは、カスタム承認マネージャーが承認に関する決定を行うために使用します。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-126">The binding that is chosen for this communication determines the claims that are added to the <xref:System.IdentityModel.Policy.AuthorizationContext>, which the custom authorization manager uses to make authorization decisions.</span></span> <span data-ttu-id="5fcd5-127">システム指定のバインディングの詳細については、次を参照してください。[システム指定のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)です。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-127">For more details about the system-provided bindings, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
4.  <span data-ttu-id="5fcd5-128">追加することで、サービス エンドポイントの動作を関連付ける、 [\<サービス >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md)要素の値を設定し、`behaviorConfiguration`属性の名前属性の値を[\<動作>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)要素。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-128">Associate the behavior to a service endpoint, by adding a [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element and set the value of the `behaviorConfiguration` attribute to the value of the name attribute for the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>  
  
     <span data-ttu-id="5fcd5-129">サービス エンドポイントの構成の詳細については、次を参照してください。[する方法: 構成でサービス エンドポイントの作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)です。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-129">For more information about configuring a service endpoint, see [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span></span>  
  
     <span data-ttu-id="5fcd5-130">カスタム承認マネージャー `Samples.MyServiceAuthorizationManager` を登録するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-130">The following code example registers the custom authorization manager `Samples.MyServiceAuthorizationManager`.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service   
              name="Microsoft.ServiceModel.Samples.CalculatorService"  
              behaviorConfiguration="CalculatorServiceBehavior">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
              </baseAddresses>  
            </host>  
            <endpoint address=""  
                      binding="wsHttpBinding_Calculator"  
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <WSHttpBinding>  
           <binding name = "wsHttpBinding_Calculator">  
             <security mode="Message">  
               <message clientCredentialType="Windows"/>  
             </security>  
            </binding>  
          </WSHttpBinding>  
    </bindings>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="CalculatorServiceBehavior">  
              <serviceAuthorization serviceAuthorizationManagerType="Samples.MyServiceAuthorizationManager,MyAssembly" />  
             </behavior>  
         </serviceBehaviors>  
       </behaviors>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
    > [!WARNING]
    >  <span data-ttu-id="5fcd5-131">serviceAuthorizationManagerType を指定する場合、文字列には、完全修飾型名、</span><span class="sxs-lookup"><span data-stu-id="5fcd5-131">Note that when you specify the serviceAuthorizationManagerType, the string must contain the fully qualified type name.</span></span> <span data-ttu-id="5fcd5-132">コンマ、型が定義されているアセンブリの名前が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-132">a comma, and the name of the assembly in which the type is defined.</span></span> <span data-ttu-id="5fcd5-133">アセンブリ名を省略した場合、WCF は、System.ServiceModel.dll から型を読み込もうとします。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-133">If you leave out the assembly name, WCF will attempt to load the type from System.ServiceModel.dll.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fcd5-134">例</span><span class="sxs-lookup"><span data-stu-id="5fcd5-134">Example</span></span>  
 <span data-ttu-id="5fcd5-135"><xref:System.ServiceModel.ServiceAuthorizationManager> メソッドのオーバーライドを含む <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> クラスの基本実装を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-135">The following code example demonstrates a basic implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class that includes overriding the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="5fcd5-136">このコード例は、<xref:System.IdentityModel.Policy.AuthorizationContext> のカスタム クレームを調べ、そのカスタム クレームのリソースが `true` のアクション値と一致した場合に <xref:System.ServiceModel.OperationContext> を返します。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-136">The example code examines the <xref:System.IdentityModel.Policy.AuthorizationContext> for a custom claim and returns `true` when the resource for that custom claim matches the action value from the <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="5fcd5-137">より完全な実装については、<xref:System.ServiceModel.ServiceAuthorizationManager>クラスを参照してください[承認ポリシー](../../../../docs/framework/wcf/samples/authorization-policy.md)です。</span><span class="sxs-lookup"><span data-stu-id="5fcd5-137">For a more complete implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class, see [Authorization Policy](../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
 [!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
 [!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="5fcd5-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="5fcd5-138">See Also</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [<span data-ttu-id="5fcd5-139">承認ポリシー</span><span class="sxs-lookup"><span data-stu-id="5fcd5-139">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)  
 [<span data-ttu-id="5fcd5-140">承認ポリシー</span><span class="sxs-lookup"><span data-stu-id="5fcd5-140">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)

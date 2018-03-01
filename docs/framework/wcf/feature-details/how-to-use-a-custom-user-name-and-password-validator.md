---
title: "方法 : カスタム ユーザー名およびパスワード検証を使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ee138c52c8cdd63137bf3c468ebbdd064d60d443
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="b4ef7-102">方法 : カスタム ユーザー名およびパスワード検証を使用する</span><span class="sxs-lookup"><span data-stu-id="b4ef7-102">How to: Use a Custom User Name and Password Validator</span></span>
<span data-ttu-id="b4ef7-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、認証にユーザー名とパスワードを使用すると、既定の Windows 認証を使用してユーザー名とパスワードが検証されます。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-103">By default, when a user name and password is used for authentication, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uses Windows to validate the user name and password.</span></span> <span data-ttu-id="b4ef7-104">ただし、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]では、カスタム ユーザー名とパスワードの認証スキームとも呼ばれる*バリデーター*です。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-104">However, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="b4ef7-105">ユーザー名およびパスワードのカスタム検証を組み込むには、<xref:System.IdentityModel.Selectors.UserNamePasswordValidator> から派生するクラスを作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-105">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>  
  
 <span data-ttu-id="b4ef7-106">サンプル アプリケーションについては、次を参照してください。[ユーザー名パスワード検証](../../../../docs/framework/wcf/samples/user-name-password-validator.md)です。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-106">For a sample application, see [User Name Password Validator](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span></span>  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="b4ef7-107">カスタムのユーザー名/パスワード検証コントロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="b4ef7-107">To create a custom user name and password validator</span></span>  
  
1.  <span data-ttu-id="b4ef7-108"><xref:System.IdentityModel.Selectors.UserNamePasswordValidator> から派生するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-108">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2.  <span data-ttu-id="b4ef7-109"><xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> メソッドをオーバーライドして、カスタム認証方式を実装します。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-109">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     <span data-ttu-id="b4ef7-110">次の例のコードは、<xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> メソッドをオーバーライドします。稼働環境では、このようなコードを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-110">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="b4ef7-111">このコードをカスタムのユーザー名/パスワード検証方式に置き換えます。この場合、ユーザー名とパスワードの組み合わせをデータベースから取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-111">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
     <span data-ttu-id="b4ef7-112">クライアントに認証エラーを返すには、<xref:System.ServiceModel.FaultException> メソッドで <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> をスローします。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-112">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="b4ef7-113">カスタムのユーザー名/パスワード検証コントロールを使用するようにサービスを構成するには</span><span class="sxs-lookup"><span data-stu-id="b4ef7-113">To configure a service to use a custom user name and password validator</span></span>  
  
1.  <span data-ttu-id="b4ef7-114">任意のトランスポート上のメッセージ セキュリティ、または HTTP(S) 上のトランスポート レベル セキュリティを使用するバインディングを構成します。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-114">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>  
  
     <span data-ttu-id="b4ef7-115">メッセージ セキュリティを使用する場合などの追加、システム指定のバインディングの 1 つ、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)、または[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)メッセージ セキュリティをサポートしています、`UserName`資格情報の種類。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-115">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>  
  
     <span data-ttu-id="b4ef7-116">HTTP (S) 経由でのトランスポート レベルのセキュリティを使用して、追加するか、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)または[ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)、 [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)または[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) HTTP (S) を使用して、`Basic`認証スキームです。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-116">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b4ef7-117">[!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] 以降を使用する場合は、メッセージおよびトランスポート セキュリティでカスタムのユーザー名/パスワード検証コントロールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-117">When [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] or later is used, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="b4ef7-118">[!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] では、カスタムのユーザー名/パスワード検証コントロールを使用できるのは、メッセージ セキュリティだけです。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-118">With [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], a custom username and password validator can only be used with message security.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="b4ef7-119">使用する方法についての\<netTcpBinding > このコンテキストで、次を参照してください[\<セキュリティ >。](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="b4ef7-119">For more information on using \<netTcpBinding> in this context, see [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span></span>  
  
    1.  <span data-ttu-id="b4ef7-120">構成ファイルで下にある、 [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)要素を追加、 [\<バインド >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)要素。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-120">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
    2.  <span data-ttu-id="b4ef7-121">追加、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)または[ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)バインディング セクションに要素。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-121">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b4ef7-122">作成する、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]バインド要素を参照してください[する方法: 構成でサービス バインディングを指定](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)です。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-122"> creating an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
    3.  <span data-ttu-id="b4ef7-123">設定、`mode`の属性、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)または[\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)に`Message`、 `Transport`、`or``TransportWithMessageCredential`です。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-123">Set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, `or``TransportWithMessageCredential`.</span></span>  
  
    4.  <span data-ttu-id="b4ef7-124">設定、`clientCredentialType`の属性、 [\<メッセージ >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)または[\<トランスポート >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-124">Set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>  
  
         <span data-ttu-id="b4ef7-125">メッセージ セキュリティを使用する場合は、設定、`clientCredentialType`の属性、 [\<メッセージ >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)に`UserName`です。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-125">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>  
  
         <span data-ttu-id="b4ef7-126">HTTP (S) 経由でのトランスポート レベルのセキュリティを使用して、設定、`clientCredentialType`の属性、 [\<トランスポート >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)または[\<トランスポート >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)に`Basic`です。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-126">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="b4ef7-127">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスがインターネット インフォメーション サービス (IIS) でトランスポート レベルのセキュリティを使用してホストされており、<xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> プロパティが <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom> に設定されている場合、カスタム認証方式では Windows 認証のサブセットが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-127">When a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="b4ef7-128">これは、このシナリオの場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] がカスタム認証を呼び出す前に IIS によって Windows 認証が実行されるためです。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-128">That is because in this scenario, IIS performs Windows authentication prior to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] invoking the custom authenticator.</span></span>  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b4ef7-129">作成する、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]バインド要素を参照してください[する方法: 構成でサービス バインディングを指定](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)です。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-129"> creating an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
     <span data-ttu-id="b4ef7-130">次のコード例は、バインディングの構成コードを示しています。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-130">The following example shows the configuration code for the binding.</span></span>  
  
    ```xml  
    <system.serviceModel>   
      <bindings>  
      <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="UserName" />  
            </security>  
          </binding>          
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
2.  <span data-ttu-id="b4ef7-131">受信 <xref:System.IdentityModel.Tokens.UserNameSecurityToken> セキュリティ トークンのユーザー名とパスワードの組み合わせを検証する際に、カスタムのユーザー名/パスワード検証コントロールを使用することを指定する動作を構成します。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-131">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>  
  
    1.  <span data-ttu-id="b4ef7-132">子として、 [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)要素を追加、 [\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)要素。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-132">As a child to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    2.  <span data-ttu-id="b4ef7-133">追加、 [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)を[\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)要素。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-133">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    3.  <span data-ttu-id="b4ef7-134">追加、 [\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)要素、`name`属性を適切な値にします。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-134">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
    4.  <span data-ttu-id="b4ef7-135">追加、 [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)を[\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)要素。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-135">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>  
  
    5.  <span data-ttu-id="b4ef7-136">追加、 [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)を[ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)です。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-136">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
    6.  <span data-ttu-id="b4ef7-137">`userNamePasswordValidationMode` を `Custom` に設定します。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-137">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="b4ef7-138">`userNamePasswordValidationMode` 値が設定されていない場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、カスタムのユーザー名/パスワード検証コントロールの代わりに Windows 認証が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-138">If the `userNamePasswordValidationMode` value is not set, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses Windows authentication instead of the custom user name and password validator.</span></span>  
  
    7.  <span data-ttu-id="b4ef7-139">`customUserNamePasswordValidatorType` を、カスタムのユーザー名/パスワード検証コントロールを表す型に設定します。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-139">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>  
  
     <span data-ttu-id="b4ef7-140">次の例に、この時点での `<serviceCredentials>` のフラグメントを示します。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-140">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a><span data-ttu-id="b4ef7-141">例</span><span class="sxs-lookup"><span data-stu-id="b4ef7-141">Example</span></span>  
 <span data-ttu-id="b4ef7-142">カスタムのユーザー名/パスワード検証コントロールを作成する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-142">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="b4ef7-143">稼働環境では、<xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> メソッドをオーバーライドするコードを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-143">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="b4ef7-144">このコードをカスタムのユーザー名/パスワード検証方式に置き換えます。この場合、ユーザー名とパスワードの組み合わせをデータベースから取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4ef7-144">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b4ef7-145">参照</span><span class="sxs-lookup"><span data-stu-id="b4ef7-145">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>  
 [<span data-ttu-id="b4ef7-146">方法 : ASP.NET メンバーシップ プロバイダーを使用する</span><span class="sxs-lookup"><span data-stu-id="b4ef7-146">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 [<span data-ttu-id="b4ef7-147">認証</span><span class="sxs-lookup"><span data-stu-id="b4ef7-147">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)

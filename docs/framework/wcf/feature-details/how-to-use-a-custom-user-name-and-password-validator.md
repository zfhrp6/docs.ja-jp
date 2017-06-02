---
title: "方法 : カスタム ユーザー名およびパスワード検証を使用する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF, ユーザー名とパスワード"
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# 方法 : カスタム ユーザー名およびパスワード検証を使用する
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、認証にユーザー名とパスワードを使用すると、既定の Windows 認証を使用してユーザー名とパスワードが検証されます。ただし、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、*"検証コントロール"* と呼ばれるカスタムのユーザー名\/パスワード認証方式を使用できます。ユーザー名およびパスワードのカスタム検証を組み込むには、<xref:System.IdentityModel.Selectors.UserNamePasswordValidator> から派生するクラスを作成して構成します。  
  
 サンプル アプリケーションについては、「[ユーザー名パスワード検証](../../../../docs/framework/wcf/samples/user-name-password-validator.md)」を参照してください。  
  
### カスタムのユーザー名\/パスワード検証コントロールを作成するには  
  
1.  <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> から派生するクラスを作成します。  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2.  <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> メソッドをオーバーライドして、カスタム認証方式を実装します。  
  
     次の例のコードは、<xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> メソッドをオーバーライドします。稼働環境では、このようなコードを使用しないでください。このコードをカスタムのユーザー名\/パスワード検証方式に置き換えます。この場合、ユーザー名とパスワードの組み合わせをデータベースから取得する必要があります。  
  
     クライアントに認証エラーを返すには、<xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> メソッドで <xref:System.ServiceModel.FaultException> をスローします。  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### カスタムのユーザー名\/パスワード検証コントロールを使用するようにサービスを構成するには  
  
1.  任意のトランスポート上のメッセージ セキュリティ、または HTTP\(S\) 上のトランスポート レベル セキュリティを使用するバインディングを構成します。  
  
     メッセージ セキュリティを使用する場合は、メッセージ セキュリティと `UserName` 資格情報の種類をサポートするシステム指定のバインディングのいずれか \([\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) や [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) など\) を追加します。  
  
     HTTP\(S\) 上のトランスポート レベル セキュリティを使用する場合は、[\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) と [\<basicHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) のいずれか、[\<netTcpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)、または HTTP\(S\) と `Basic` 認証方式を使用する [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) を追加します。  
  
    > [!NOTE]
    >  [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] 以降を使用する場合は、メッセージおよびトランスポート セキュリティでカスタムのユーザー名\/パスワード検証コントロールを使用できます。[!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] では、カスタムのユーザー名\/パスワード検証コントロールを使用できるのは、メッセージ セキュリティだけです。  
  
    > [!TIP]
    >  このコンテキストでの \<netTcpBinding\> の使用方法の詳細については、「[\<security\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)」を参照してください。  
  
    1.  構成ファイルの [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) 要素の下に、[\<bindings\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) 要素を追加します。  
  
    2.  [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) 要素または [\<basicHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) 要素をバインド セクションに追加します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] バインド要素の作成[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : 構成でサービス バインディングを指定する](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)」を参照してください。  
  
    3.  [\<security\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)または [\<security\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) の `mode` 属性を `Message`、`Transport`、または `TransportWithMessageCredential` に設定します。  
  
    4.  [\<message\>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)または [\<transport\>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) の `clientCredentialType` 属性を設定します。  
  
         メッセージ セキュリティを使用する場合は、[\<message\>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) の `clientCredentialType` 属性を `UserName` に設定します。  
  
         HTTP\(S\) 上でトランスポート レベルのセキュリティを使用する場合は、[\<transport\>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) または [\<transport\>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) の `clientCredentialType` 属性を `Basic` に設定します。  
  
        > [!NOTE]
        >  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスがインターネット インフォメーション サービス \(IIS\) でトランスポート レベルのセキュリティを使用してホストされており、<xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> プロパティが <xref:System.ServiceModel.Security.UserNamePasswordValidationMode> に設定されている場合、カスタム認証方式では Windows 認証のサブセットが使用されます。これは、このシナリオの場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] がカスタム認証を呼び出す前に IIS によって Windows 認証が実行されるためです。  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] バインド要素の作成[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : 構成でサービス バインディングを指定する](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)」を参照してください。  
  
     次のコード例は、バインディングの構成コードを示しています。  
  
    ```  
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
  
2.  受信 <xref:System.IdentityModel.Tokens.UserNameSecurityToken> セキュリティ トークンのユーザー名とパスワードの組み合わせを検証する際に、カスタムのユーザー名\/パスワード検証コントロールを使用することを指定する動作を構成します。  
  
    1.  [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) 要素の子として [\<behaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) 要素を追加します。  
  
    2.  [\<serviceBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) を [\<behaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) 要素に追加します。  
  
    3.  [\<behavior\>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) 要素を追加し、`name` 属性に適切な値を設定します。  
  
    4.  [\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)を [\<behavior\>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) 要素に追加します。  
  
    5.  [\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)に [\<userNameAuthentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)を追加します。  
  
    6.  `userNamePasswordValidationMode` を `Custom` に設定します。  
  
        > [!IMPORTANT]
        >  `userNamePasswordValidationMode` 値が設定されていない場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、カスタムのユーザー名\/パスワード検証コントロールの代わりに Windows 認証が使用されます。  
  
    7.  `customUserNamePasswordValidatorType` を、カスタムのユーザー名\/パスワード検証コントロールを表す型に設定します。  
  
     次の例に、この時点での `<serviceCredentials>` のフラグメントを示します。  
  
    ```  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## 使用例  
 カスタムのユーザー名\/パスワード検証コントロールを作成する方法を次のコード例に示します。稼働環境では、<xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> メソッドをオーバーライドするコードを使用しないでください。このコードをカスタムのユーザー名\/パスワード検証方式に置き換えます。この場合、ユーザー名とパスワードの組み合わせをデータベースから取得する必要があります。  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## 参照  
 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>   
 [方法 : ASP.NET メンバーシップ プロバイダーを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)   
 [認証](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
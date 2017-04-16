---
title: "方法 : ASP.NET メンバーシップ プロバイダーを使用する | Microsoft Docs"
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
  - "WCF と ASP.NET"
  - "WCF, 承認"
  - "WCF, セキュリティ"
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# 方法 : ASP.NET メンバーシップ プロバイダーを使用する
[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] メンバーシップ プロバイダーを使用すると、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 開発者は、ユーザーが一意のユーザー名とパスワードの組み合わせを作成できる Web サイトを作成できます。この機能を使用すれば、ユーザーはだれでもサイトでアカウントを作成し、そのサイトにサインインして、サービスに排他的にアクセスできます。これは、ユーザーが Windows ドメイン内にアカウントを持っていることが必要な Windows セキュリティとは対照的です。自分の資格情報 \(ユーザー名とパスワードの組み合わせ\) を提示したユーザーは、だれでもサイトとそのサービスを使用できるからです。  
  
 サンプル アプリケーションについては、「[メンバーシップとロール プロバイダー](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)」を参照してください。[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール プロバイダー機能の使用については、「[方法 : ASP.NET のロール プロバイダーとサービスを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)」を参照してください。  
  
 メンバーシップ機能では、SQL Server データベースを使用してユーザー情報を格納する必要があります。メンバーシップ機能には、パスワードを忘れたユーザーへの質問を行うためのメソッドも含まれています。  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 開発者は、セキュリティを向上させるためにこれらの機能を利用できます。この機能を [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションに統合した場合、ユーザーはユーザー名とパスワードの組み合わせを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント アプリケーションに提示する必要があります。データを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスに転送するには、<xref:System.ServiceModel.WSHttpBinding> \(構成では [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)\) のような、ユーザー名\/パスワード資格情報をサポートするバインディングを使用し、クライアントの資格情報の種類を `UserName` に設定します。サービス側では、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] セキュリティが、ユーザー名とパスワードに基づいてユーザーを認証し、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロールによって指定されるロールを割り当てます。  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、ユーザー名\/パスワードの組み合わせ、またはその他のユーザー情報をデータベースに格納するメソッドは提供されません。  
  
### メンバーシップ プロバイダーを構成するには  
  
1.  Web.config ファイルの \<`system.web`\> 要素の下に \<`membership`\> 要素を作成します。  
  
2.  `<membership>` `<providers> 要素の下に、` 要素を作成します。  
  
3.  \<`providers`\> 要素の子要素として、`<clear />` 要素を追加し、プロバイダーのコレクションをフラッシュします。  
  
4.  `<clear />`\< `要素の下に add`\>`name 要素を作成し、``type、``connectionStringName、``applicationName、``enablePasswordRetrieval、``enablePasswordReset、``requiresQuestionAndAnswer、``requiresUniqueEmail、``passwordFormat、および`  の各属性を適切な値に設定します。`name` 属性は、構成ファイルの値として後で使用します。`SqlMembershipProvider` に設定する方法の例を次に示します。  
  
     次の例は構成セクションを示します。  
  
    ```xml  
    <!-- Configure the Sql Membership Provider -->  
    <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">  
      <providers>  
        <clear />  
          <add   
            name="SqlMembershipProvider"   
            type="System.Web.Security.SqlMembershipProvider"   
            connectionStringName="SqlConn"  
            applicationName="MembershipAndRoleProviderSample"  
            enablePasswordRetrieval="false"  
            enablePasswordReset="false"  
            requiresQuestionAndAnswer="false"  
            requiresUniqueEmail="true"  
            passwordFormat="Hashed" />  
      </providers>  
    </membership>  
    ```  
  
### ユーザー名\/パスワードの組み合わせを受け入れるようにサービス セキュリティを構成するには  
  
1.  構成ファイルの [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)[\<bindings\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) 要素を追加します。  
  
2.  [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)をバインディング セクションに追加します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] バインド要素の作成[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : 構成でサービス バインディングを指定する](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)」を参照してください。  
  
3.  `<security>` 要素の `modeMessage 属性を`  に設定します。  
  
4.  \<`message`\> 要素の `clientCredentialType` 属性を `UserName` に設定します。これにより、ユーザー名\/パスワードの組み合わせがクライアントの資格情報として使用されるようになります。  
  
     次のコード例は、バインディングの構成コードを示しています。  
  
    ```xml  
    <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
      <!-- Set up a binding that uses UserName as the client credential type -->  
        <binding name="MembershipBinding">  
          <security mode ="Message">  
            <message clientCredentialType ="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    </system.serviceModel>  
    ```  
  
### メンバーシップ プロバイダーを使用するようにサービスを構成するには  
  
1.  `<system.serviceModel>` [\<behaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) 要素を追加します。  
  
2.  [\<serviceBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) を \<`behaviors`\> 要素に追加します。  
  
3.  [\<behavior\>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) を追加し、`name` 属性を適切な値に設定します。  
  
4.  [\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)\<`behaviorを` \> 要素に追加します。  
  
5.  [\<userNameAuthentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)を `<serviceCredentials>` 要素に追加します。  
  
6.  `userNamePasswordValidationMode` 属性を `MembershipProvider` に設定します。  
  
    > [!IMPORTANT]
    >  `userNamePasswordValidationMode` 値が設定されていない場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] メンバーシップ プロバイダーの代わりに Windows 認証を使用します。  
  
7.  `membershipProviderName` 属性をプロバイダーの名前 \(このトピックの最初の手順でプロバイダーを追加したときに指定したもの\) に設定します。次の例に、この時点での `<serviceCredentials>` のフラグメントを示します。  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
          <behavior name="MyServiceBehavior">  
             <serviceCredentials>  
                <userNameAuthentication   
                userNamePasswordValidationMode="MembershipProvider"  
                membershipProviderName="SqlMembershipProvider" />  
             </serviceCredentials>  
          </behavior>  
       </serviceBehaviors>  
    </behaviors>  
  
    ```  
  
## 使用例  
 次のコードは、ASP メンバーシップ機能を使用するサービスの構成を示します。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="MyServiceBehavior" name="Microsoft.Samples.GettingStarted.CalculatorService">  
        <endpoint address="http://microsoft.com/WCFservices/Calculator"  
          binding="wsHttpBinding" bindingConfiguration="MembershipBinding"  
          name="ASPmemberUserName" contract="Microsoft.Samples.GettingStarted.ICalculator" />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyServiceBehavior">  
          <serviceCredentials>  
            <userNameAuthentication   
              userNamePasswordValidationMode="MembershipProvider"  
              membershipProviderName="SqlMembershipProvider" />  
          </serviceCredentials>  
        </behavior>  
          </serviceBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MembershipBinding">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
  
```  
  
## 参照  
 [方法 : ASP.NET のロール プロバイダーとサービスを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)   
 [メンバーシップとロール プロバイダー](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
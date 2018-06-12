---
title: '方法 : ASP.NET メンバーシップ プロバイダーを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: d71e3679f4bf395b240c330fc573d6f613d1be07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>方法 : ASP.NET メンバーシップ プロバイダーを使用する
[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] メンバーシップ プロバイダーを使用すると、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 開発者は、ユーザーが一意のユーザー名とパスワードの組み合わせを作成できる Web サイトを作成できます。 この機能を使用すれば、ユーザーはだれでもサイトでアカウントを作成し、そのサイトにサインインして、サービスに排他的にアクセスできます。 これは、ユーザーが Windows ドメイン内にアカウントを持っていることが必要な Windows セキュリティとは対照的です。 自分の資格情報 (ユーザー名とパスワードの組み合わせ) を提示したユーザーは、だれでもサイトとそのサービスを使用できるからです。  
  
 サンプル アプリケーションについては「[メンバーシップとロール プロバイダー](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)」を参照してください。 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール プロバイダー機能の使用については [ASP.NET のロール プロバイダーとサービスの使用](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)に関する記事を参照してください。  
  
 メンバーシップ機能では、SQL Server データベースを使用してユーザー情報を格納する必要があります。 メンバーシップ機能には、パスワードを忘れたユーザーへの質問を行うためのメソッドも含まれています。  
  
 Windows Communication Foundation (WCF) 開発者は、これらの機能のセキュリティの目的で利用できます。 WCF アプリケーションに統合すると、ユーザーは、WCF クライアント アプリケーションにユーザー名/パスワードの組み合わせを指定する必要があります。 WCF サービスにデータを転送するには、ユーザー名/パスワードの資格情報をサポートするバインディングを <xref:System.ServiceModel.WSHttpBinding> (構成では、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) として使用して、クライアントの資格情報の種類を `UserName` に設定します。 サービスでは、WCF セキュリティがユーザー名とパスワードに基づいてユーザーを認証し、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]ロール によって指定されたロールを割り当てます。
  
> [!NOTE]
>  WCF では、ユーザー名/パスワードの組み合わせを持つデータベースまたはその他のユーザー情報を格納するメソッドは提供されません。  
  
### <a name="to-configure-the-membership-provider"></a>メンバーシップ プロバイダーを構成するには  
  
1.  Web.config ファイルで、<`system.web`> 要素の下に、<`membership`> 要素を作成します。  
  
2.  `<membership>` 要素の下に、`<providers>` 要素を作成します。  
  
3.  子として、<`providers`> 要素を追加、`<clear />`プロバイダーのコレクションをフラッシュする要素。  
  
4.  下にある、`<clear />`要素を作成、<`add`> 次の属性を持つ要素が適切な値に設定: `name`、 `type`、 `connectionStringName`、 `applicationName`、 `enablePasswordRetrieval`、 `enablePasswordReset`、 `requiresQuestionAndAnswer`、 `requiresUniqueEmail`、および`passwordFormat`です。 `name` 属性は、構成ファイルの値として後で使用します。 `SqlMembershipProvider` に設定する方法の例を次に示します。  
  
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
  
### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a>ユーザー名/パスワードの組み合わせを受け入れるようにサービス セキュリティを構成するには  
  
1.  構成ファイルで下にある、 [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)要素を追加、 [\<バインド >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)要素。  
  
2.  追加、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)バインディング セクションにします。 WCF バインド要素の作成の詳細については、次を参照してください。[する方法: 構成でサービス バインディングを指定](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)です。  
  
3.  `mode` 要素の `<security>` 属性を `Message` に設定します。  
  
4.  設定、`clientCredentialType`の属性、<`message`> 要素を`UserName`です。 これにより、ユーザー名/パスワードの組み合わせがクライアントの資格情報として使用されるようになります。  
  
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
  
### <a name="to-configure-a-service-to-use-the-membership-provider"></a>メンバーシップ プロバイダーを使用するようにサービスを構成するには  
  
1.  子として、`<system.serviceModel>`要素を追加、 [\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)要素  
  
2.  追加、 [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)に、<`behaviors`> 要素。  
  
3.  追加、 [\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)設定と、`name`属性を適切な値にします。  
  
4.  追加、 [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)に、<`behavior`> 要素。  
  
5.  追加、 [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)を`<serviceCredentials>`要素。  
  
6.  `userNamePasswordValidationMode` 属性を `MembershipProvider` に設定します。  
  
    > [!IMPORTANT]
    >  場合、`userNamePasswordValidationMode`値が設定されていない、WCF の代わりに Windows 認証を使用して、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]メンバーシップ プロバイダー。  
  
7.  `membershipProviderName` 属性をプロバイダーの名前 (このトピックの最初の手順でプロバイダーを追加したときに指定したもの) に設定します。 次の例に、この時点での `<serviceCredentials>` のフラグメントを示します。  
  
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
  
## <a name="example"></a>例  
 次のコードは、ASP メンバーシップ機能を使用するサービスの構成を示します。  
  
```xml  
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
  
## <a name="see-also"></a>関連項目  
 [方法 : ASP.NET のロール プロバイダーとサービスを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [メンバーシップとロール プロバイダー](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)

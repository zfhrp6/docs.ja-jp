---
title: '方法 : ASP.NET メンバーシップ プロバイダーを使用する'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 19fb83d21c77f3206c314a2e6c40562fcb75f151
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>方法 : ASP.NET メンバーシップ プロバイダーを使用する
[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] メンバーシップ プロバイダーを使用すると、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 開発者は、ユーザーが一意のユーザー名とパスワードの組み合わせを作成できる Web サイトを作成できます。 この機能を使用すれば、ユーザーはだれでもサイトでアカウントを作成し、そのサイトにサインインして、サービスに排他的にアクセスできます。 これは、ユーザーが Windows ドメイン内にアカウントを持っていることが必要な Windows セキュリティとは対照的です。 自分の資格情報 (ユーザー名とパスワードの組み合わせ) を提示したユーザーは、だれでもサイトとそのサービスを使用できるからです。  
  
 サンプル アプリケーションについては「[メンバーシップとロール プロバイダー](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)」を参照してください。 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール プロバイダー機能の使用については [ASP.NET のロール プロバイダーとサービスの使用](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)に関する記事を参照してください。  
  
 メンバーシップ機能では、SQL Server データベースを使用してユーザー情報を格納する必要があります。 メンバーシップ機能には、パスワードを忘れたユーザーへの質問を行うためのメソッドも含まれています。  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 開発者は、セキュリティを向上させるためにこれらの機能を利用できます。 この機能を [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションに統合した場合、ユーザーはユーザー名とパスワードの組み合わせを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント アプリケーションに提示する必要があります。 データを転送する、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]サービス, など、ユーザー名/パスワードの資格情報をサポートするバインドを使用して、 <xref:System.ServiceModel.WSHttpBinding> (構成では、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) し、クライアントの資格情報を設定型を`UserName`です。 サービス側では、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] セキュリティが、ユーザー名とパスワードに基づいてユーザーを認証し、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロールによって指定されるロールを割り当てます。  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、ユーザー名/パスワードの組み合わせ、またはその他のユーザー情報をデータベースに格納するメソッドは提供されません。  
  
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
  
2.  追加、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)バインディング セクションにします。 作成の詳細については、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]バインド要素を参照してください[する方法: 構成でサービス バインディングを指定](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)です。  
  
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
    >  `userNamePasswordValidationMode` 値が設定されていない場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] メンバーシップ プロバイダーの代わりに Windows 認証を使用します。  
  
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

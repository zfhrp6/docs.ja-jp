---
title: "方法 : ASP.NET のロール プロバイダーとサービスを使用する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 方法 : ASP.NET のロール プロバイダーとサービスを使用する
[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール プロバイダーを [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] メンバーシップ プロバイダーと共に使用すると、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 開発者は、サイトで使用するアカウントをユーザーが作成し、承認のためにユーザーにロールを割り当てることができる Web サイトを作成できます。この機能を使用すれば、ユーザーはだれでもサイトでアカウントを作成し、そのサイトにログインしてサービスに排他的にアクセスできます。これは、ユーザーが Windows ドメイン内にアカウントを持っていることが必要な Windows セキュリティとは対照的です。自分の資格情報 \(ユーザー名とパスワードの組み合わせ\) を提示したユーザーは、だれでもサイトとそのサービスを使用できます。  
  
 サンプル アプリケーションについては、「[メンバーシップとロール プロバイダー](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)」を参照してください。[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] のメンバーシップ プロバイダー機能[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : ASP.NET メンバーシップ プロバイダーを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)」を参照してください。  
  
 ロール プロバイダー機能では、SQL Server データベースを使用してユーザー情報を格納します。[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 開発者は、セキュリティを向上させるためにこれらの機能を利用できます。この機能を [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションに統合した場合、ユーザーはユーザー名とパスワードの組み合わせを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント アプリケーションに提示する必要があります。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でデータベースを使用できるようにするには、<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> クラスのインスタンスを作成し、その <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> プロパティを <xref:System.ServiceModel.Description.PrincipalPermissionMode> に設定してから、サービスをホストしている <xref:System.ServiceModel.ServiceHost> に対する動作のコレクションにそのインスタンスを追加します。  
  
### ロール プロバイダーを構成するには  
  
1.  Web.config ファイルで、\<`system.web`\> 要素の下に \<`roleManager`\> 要素を追加し、その `enabled` 属性を `true` に設定します。  
  
2.  `defaultProvider` 属性を `SqlRoleProvider` に追加します。  
  
3.  \<`roleManager`\> 要素の子として \<`providers`\> 要素を追加します。  
  
4.  次の例に示すように、\<`providers`\> 要素の子として \<`add`\> 要素を追加し、`name`、`type`、`connectionStringName`、および `applicationName` の各属性を適切な値に設定します。  
  
    ```  
    <!-- Configure the Sql Role Provider. -->  
    <roleManager enabled ="true"   
     defaultProvider ="SqlRoleProvider" >  
       <providers>  
         <add name ="SqlRoleProvider"   
           type="System.Web.Security.SqlRoleProvider"   
           connectionStringName="SqlConn"   
           applicationName="MembershipAndRoleProviderSample"/>  
       </providers>  
    </roleManager>  
    ```  
  
### ロール プロバイダーを使用するようにサービスを構成するには  
  
1.  Web.config ファイルで [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) 要素を追加します。  
  
2.  [\<behaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) 要素を \<`system.ServiceModel`\> 要素に追加します。  
  
3.  \<`behaviors`\> 要素に [\<serviceBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)を追加します。  
  
4.  [\<behavior\>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)を追加し、`name` 属性を適切な値に設定します。  
  
5.  [\<serviceAuthorization\>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)を \<`behavior`\> 要素に追加します。  
  
6.  `principalPermissionMode` 属性を `UseAspNetRoles` に追加します。  
  
7.  `roleProviderName` 属性を `SqlRoleProvider` に追加します。この構成の一部を次の例に示します。  
  
    ```  
    <behaviors>  
     <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
       <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                             roleProviderName ="SqlRoleProvider" />  
      </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
## 参照  
 [メンバーシップとロール プロバイダー](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)   
 [方法 : ASP.NET メンバーシップ プロバイダーを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
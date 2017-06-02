---
title: "方法 : ASP.NET の承認マネージャー ロール プロバイダーとサービスを使用する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 方法 : ASP.NET の承認マネージャー ロール プロバイダーとサービスを使用する
[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] が Web サービスをホストする場合は、承認マネージャーをアプリケーションに統合してサービスを承認することができます。  承認マネージャーを使用して、アプリケーション開発者は個々の操作を定義できます。また、個々の操作をグループ化してタスクを形成できます。  次に管理者は、ロールを承認して特定のタスクまたは個々の操作を実行できます。  承認マネージャーでは、ロール、タスク、操作、ユーザーを管理する管理ツールとして Microsoft 管理コンソール \(MMC\) スナップインが提供されます。  管理者は、承認マネージャーのポリシー ストアを XML ファイル、Active Directory、または Active Directory アプリケーション モード \(ADAM\) ストアに構成します。  
  
 承認マネージャーをアプリケーションに統合するには、Web サービスをホストする [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションの承認マネージャーの [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール プロバイダーを構成します。  他の [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール プロバイダーと同様、承認マネージャーの [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール プロバイダーは \<`providers`\> 要素を使用して構成します。  
  
 承認マネージャーをアプリケーションに統合する Web サービスの構成ファイルの一部を示すコード例を次に示します。  
  
```  
<system.web>  
    <roleManager enabled="true" defaultProvider="AzManRoleProvider">  
      <providers>  
        <add name="AzManRoleProvider"  
             type="System.Web.Security.AuthorizationStoreRoleProvider, System.Web, Version=2.0.0.0, Culture=neutral, publicKeyToken=b03f5f7f11d50a3a"  
             connectionStringName="AzManPolicyStoreConnectionString"   
             applicationName="SecureService"/>  
      </providers>  
    </roleManager>  
</system.web>  
```  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール プロバイダーと [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションを統合する [!INCLUDE[crabout](../../../../includes/crabout-md.md)] については、「[方法 : ASP.NET のロール プロバイダーとサービスを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)」を参照してください。  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] で承認マネージャーを使用する [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] については、「[方法: ASP.NET 2.0 で認証マネージャー \(AzMan\) を使用する](http://go.microsoft.com/fwlink/?LinkId=71303)」を参照してください。  
  
## 参照  
 [方法 : ASP.NET のロール プロバイダーとサービスを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
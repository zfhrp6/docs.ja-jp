---
title: "動作のセキュリティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19710ae3-f197-4d28-ba9d-52e465006819
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# 動作のセキュリティ
このセクションには、サービスの動作に対するセキュリティの構成を示すサンプルが含まれています。  
  
## このセクションの内容  
 [サービス監査動作](../../../../docs/framework/wcf/samples/service-auditing-behavior.md)  
 このサンプルでは、<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> を使用して、サービス操作中にセキュリティ イベントの監査を有効にする方法を示します。  
  
 [メンバーシップとロール プロバイダー](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)  
 このサンプルでは、サービスが [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] メンバーシップとロール プロバイダーを使用してクライアントを認証および承認するための方法を示します。  
  
 [サービス操作へのアクセスの承認](../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 このサンプルでは、[\<serviceAuthorization\>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)を使用して、サービス操作へのアクセスを承認する <xref:System.Security.Permissions.PrincipalPermissionAttribute> 属性を使用できるようにする方法を示します。  
  
 [クライアントの偽装](../../../../docs/framework/wcf/samples/impersonating-the-client.md)  
 サービスで呼び出し元のアプリケーションを偽装し、サービスが呼び出し元の代わりにシステム リソースにアクセスできるようにする方法を示します。
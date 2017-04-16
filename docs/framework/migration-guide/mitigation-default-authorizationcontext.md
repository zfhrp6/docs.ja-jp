---
title: "軽減策: 既定の AuthorizationContext | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6cfeee63-b148-429a-a7e6-6fe9b0cb7610
caps.latest.revision: 3
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 3
---
# 軽減策: 既定の AuthorizationContext
`null` の `authorizationPolicies` 引数を指定して <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29> を呼び出したときに返される <xref:System.IdentityModel.Policy.AuthorizationContext> の実装が [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] で変更されました。  
  
## 影響  
 まれに、カスタム認証を使用する WCF アプリの動作に違いが生じる可能性があります。  
  
## 軽減策  
 次の 2 つの方法のいずれかで、直前の動作を復元することができます。  
  
-   4.6 よりも前のバージョンの .NET Framework を対象とするようにアプリを再コンパイルする。  IIS でホストされるサービスでは、`<httpRuntime targetFramework="x.x" />` の要素を使用して、以前のバージョンの .NET Framework を対象とするようにします。  
  
-   app.config ファイルの `<appSettings>` セクションに以下の行を追加します。  
  
    ```  
    <add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />  
    ```  
  
## 参照  
 [変更の再ターゲット](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
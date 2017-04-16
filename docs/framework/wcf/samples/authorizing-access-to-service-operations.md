---
title: "サービス操作へのアクセスの承認 | Microsoft Docs"
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
  - "承認, Windows Communication Foundation サンプル"
  - "サービス操作へのアクセスの承認のサンプル [Windows Communication Foundation]"
  - "サービスの動作, アクセスの承認のサンプル"
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
caps.latest.revision: 23
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 23
---
# サービス操作へのアクセスの承認
このサンプルでは、<xref:System.Security.Permissions.PrincipalPermissionAttribute> 属性を使用できるようにする [\<serviceAuthorization\>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)を使用して、サービス操作へのアクセスを承認する方法を示します。  このサンプルは、「[概要](../../../../docs/framework/wcf/samples/getting-started-sample.md)」のサンプルに基づいています。  サービスとクライアントは、[\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)を使用して構成されています。  [\<security\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)の `mode` 属性は `Message` に、`clientCredentialType` は `Windows` に設定されています。  <xref:System.Security.Permissions.PrincipalPermissionAttribute> は各サービス メソッドに適用され、各操作へのアクセスを制限するために使用されます。  呼び出し元は、各操作にアクセスできる Windows 管理者である必要があります。  
  
 この例では、クライアントはコンソール アプリケーション \(.exe\) であり、サービスはインターネット インフォメーション サービス \(IIS\) によってホストされます。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 サービス構成ファイルは、次のように [\<serviceAuthorization\>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)を使用して `principalPermissionMode`  属性を設定します。  
  
```  
<behaviors>  
  <serviceBehaviors>  
    <behavior>  
      ...  
      <!-- The serviceAuthorization behavior sets the  
           principalPermissionMode to UseWindowsGroups.  
           This puts a WindowsPrincipal on the current thread when a   
           service is invoked. -->  
      <serviceAuthorization principalPermissionMode="UseWindowsGroups" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 `principalPermissionMode` を `UseWindowsGroups` に設定すると、Windows グループ名に基づいて <xref:System.Security.Permissions.PrincipalPermissionAttribute> を使用できるようになります。  
  
 呼び出し元が Windows 管理者グループのメンバーであることを要求するため、<xref:System.Security.Permissions.PrincipalPermissionAttribute> が各操作に適用されます。次のサンプル コードを参照してください。  
  
```  
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。  クライアントが管理者グループのメンバーであるアカウントで実行される場合、クライアントは各操作と正常に通信できます。それ以外のアカウントで実行される場合、アクセスは拒否されます。  承認エラーを試すには、管理グループのメンバーではないアカウントでクライアントを実行します。  クライアントをシャットダウンするには、コンソール ウィンドウで Enter キーを押します。  
  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler> を実装すると、サービスに承認エラーを通知することができます。  `IErrorHandler` の実装方法については、「[エラー処理およびレポートに対する制御の拡張](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)」を参照してください。  
  
### サンプルをセットアップ、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
## 参照
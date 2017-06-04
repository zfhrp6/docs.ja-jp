---
title: "構成を使用しない AJAX サービス | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
caps.latest.revision: 23
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 23
---
# 構成を使用しない AJAX サービス
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用して、構成設定を使用せずに基本的な ASP.NET AJAX \(Asynchronous JavaScript and XML\) サービス \(Web ブラウザー クライアントから JavaScript コードを使用してアクセスできるサービス\) を作成する方法を示します。  このサービスは .svc ファイルの特殊な構文を使用して AJAX エンドポイントを自動的に有効にします。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] での AJAX サポートは、`ScriptManager` コントロールを介して ASP.NET AJAX と共に使用できるように最適化されています。  ASP.NET AJAX と共に [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用する例については、「[Ajax Samples](http://msdn.microsoft.com/ja-jp/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e)」を参照してください。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルは、HTTP POST を使用した AJAX サービスに基づいています。  [基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md) サンプルで説明したように、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> を使用してサービスをホストします。  
  
```  
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
  
```  
  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> は、<xref:System.ServiceModel.Description.WebScriptEndpoint> をサービスに自動的に追加します。  エンドポイントに対する構成変更が不要な場合、\<system.ServiceModel\> セクションはサービスの Web.config ファイルから完全に削除できます。  Web.config ファイルには、ConfigFreeClientPage.aspx で使用される ASP.NET 設定がいくつか含まれます。  そうでない場合は、Web.config ファイル全体を削除できます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。  続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。  このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### サンプルをセットアップ、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」のセットアップ手順を実行します。  
  
2.  「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従って、ソリューション ConfigFreeAjaxService.sln をビルドします。  
  
3.  http:\/\/localhost\/ServiceModelSamples\/ConfigFreeClientPage.aspx に移動します \(プロジェクト ディレクトリからブラウザーで ConfigFreeClientPage.aspx を開かないでください\)。  
  
> [!NOTE]
>  このサンプルを実行する場合、IIS の ServiceModelSamples フォルダーで匿名認証と Windows 認証が同時に有効になっていないことを確認してください。  有効になっている場合は、Windows 認証を無効にしてください。  サンプルの実行が終了したら、Windows 認証を有効にし、"iisreset" を実行します。  
  
## 参照  
 [基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
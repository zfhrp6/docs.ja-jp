---
title: "方法 : Svcutil.exe を使用してコンパイル済みサービス コードを検証する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 方法 : Svcutil.exe を使用してコンパイル済みサービス コードを検証する
[ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を使用すると、サービスをホストせずにサービスの実装と構成でエラーを検出できます。  
  
### サービスを検証するには  
  
1.  サービスを実行可能ファイルおよび 1 つ以上の依存アセンブリにコンパイルします。  
  
2.  SDK コマンド プロンプトを開きます。  
  
3.  コマンド プロンプトで、次の形式を使用して Svcutil.exe ツールを起動します。  各パラメーターの詳細については、「[ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)」トピックの「サービスの検証」を参照してください。  
  
    ```  
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     `/serviceName` オプションを使用して、検証するサービスの構成名を指定する必要があります。  
  
     `assemblyPath` 引数には、検証対象のサービスの実行可能ファイルへのパス、およびサービス型を格納している 1 つ以上のアセンブリへのパスを指定します。  実行可能アセンブリに、サービス構成を提供する関連構成ファイルが存在している必要があります。  標準のコマンドライン ワイルドカードを使用して、複数のアセンブリを指定できます。  
  
## 使用例  
 次のコマンドでは、myServiceHost.exe 実行可能ファイルに実装されたサービス myServiceName を検証します。  サービスの構成ファイル \(myServiceHost.exe.config\) は自動的に読み込まれます。  
  
```  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## 参照  
 [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
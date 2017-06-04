---
title: "@ServiceHost | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# @ServiceHost
サービス ホストの生成に使用されるファクトリを、ホストされるサービスと、.svc ファイルで提供されるホスティング コードのアクセスとコンパイルに必要なその他のプログラミング部分に関連付けます。  
  
## 構文  
  
```  
  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## 属性  
  
#### サービス  
 ホストされるサービスの CLR 型名。  これは、1 つ以上のサービス コンタクトを実装する型の修飾名にする必要があります。  
  
#### ファクトリ  
 サービス ホストのインスタンス化に使用されるサービス ホスト ファクトリの CLR 型名。  この属性は省略できます。  未指定の場合は、<xref:System.ServiceModel.ServiceHost> のインスタンスを返す既定の <xref:System.ServiceModel.Activation.ServiceHostFactory> が使用されます。  
  
#### デバッグ  
 デバッグ シンボルを使用して [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] サービスをコンパイルするかどうかを示します。  デバッグ シンボルを含む [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスをコンパイルする場合は `true`、それ以外の場合は `false` を指定します。  
  
#### 言語  
 ファイル \(.svc\) 内のすべてのインライン コードをコンパイルするときに使用する言語を指定します。  値は、C\#、VB、JS \(それぞれ、C\#、Visual Basic .NET、および JScript .NET を示す\) など、.NET がサポートする任意の言語を表します。  この属性は省略できます。  
  
#### CodeBehind  
 XML Web サービスを実装するクラスが同じファイル内に存在せず、アセンブリとしてコンパイルされずに \\Bin ディレクトリに置かれているとき、XML Web サービスを実装するソース ファイルを指定します。  
  
## 解説  
 サービスのホストに使用される <xref:System.ServiceModel.ServiceHost> は、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] プログラミング モデル内の拡張ポイントです。  ファクトリ パターンは、ホスティング環境が直接インスタンス化できないポリモーフィック型の可能性があるため、<xref:System.ServiceModel.ServiceHost> のインスタンス化に使用されます。  
  
 既定の実装では <xref:System.ServiceModel.Activation.ServiceHostFactory> を使用して、<xref:System.ServiceModel.ServiceHost> のインスタンスを作成します。  ただし、ファクトリ実装の CLR 型名を [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) ディレクティブに指定して、独自のファクトリ \(派生ホストを返すファクトリ\) を提供できます。  
  
 既定のファクトリの代わりに独自のカスタム サービス ホスト ファクトリを使用するには、型名を [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) ディレクティブに次のように指定します。  
  
```  
<% @ServiceHost Factory=”DerivedFactory” Service=”MyService” %>  
```  
  
 ファクトリ実装はできるだけ軽量に保持してください。  多くのカスタム ロジックがある場合は、それらのロジックをファクトリ内部ではなくホスト内部に置くとコードがさらに再利用可能になります。  
  
 たとえば、`MyService` の AJAX 対応のエンドポイントを有効にするには、次の例に示す [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) ディレクティブで、`Factory` 属性の値に、既定の <xref:System.ServiceModel.Activation.ServiceHostFactory> の代わりに <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> を指定します。  
  
## 使用例  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## 参照  
 [カスタム サービス ホスト](../../../../../docs/framework/wcf/samples/custom-service-host.md)
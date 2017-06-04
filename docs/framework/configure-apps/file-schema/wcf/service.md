---
title: "&lt;service&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
caps.latest.revision: 27
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 27
---
# &lt;service&gt;
`service` 要素には Windows Communication Foundation \(WCF\) サービスの設定が含まれます。  また、サービスを公開するエンドポイントも含まれます。  
  
## 構文  
  
```  
  
<service behaviorConfiguration=String"  
        name="String"  
</service>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|behaviorConfiguration|サービスのインスタンス化に使用される動作の動作名を含む文字列。  動作名は、サービスが定義される時点でスコープ内にある必要があります。  既定値は空の文字列です。|  
|name|インスタンス化するサービスの型を指定する必須の文字列属性。  この設定は有効な型と同じでなければなりません。  形式は、`Namespace.Class` です。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<endpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|このサービスを公開する `endpoint` 要素のコレクション。|  
|[\<host\>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|このサービス インスタンスのホストを指定します。  この要素は <xref:System.ServiceModel.Configuration.HostElement> 型です。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<services\>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|すべての WCF 構成要素のルート要素です。|  
  
## 解説  
 サービスは、設定ファイルの `services` セクションで定義されます。  アセンブリには、任意の数のサービスを含めることができます。  各サービスには、独自の `service` 設定セクションがあります。  このセクションとその内容は、サービス コントラクト、動作、および特定のサービスのエンドポイントを定義します。  
  
 `behaviorConfiguration` 要素も省略可能です。  サービスが使用する動作を識別します。  この属性で指定された動作は、同じ設定ファイルの範囲にある動作にリンクしている必要があります。  
  
 各サービスでは、固有のアドレスとバインディングを持つ 1 つまたは複数のエンドポイントが公開されます。  構成ファイル内で使用されるすべてのバインディングは、そのファイルのスコープ内で定義される必要があります。  バインディングは、`name` 属性と `bindingConfiguration` 属性の組み合わせによってエンドポイントにリンクされます。  `name` 属性は、バインディングが定義されているセクションを示します。  `bindingConfiguration` 属性は、バインディング セクション内の使用される構成を定義します。  バインディング セクションでは、複数の設定を定義できます。  
  
## 使用例  
 これはサービスの構成の例です。  
  
```  
<service behaviorConfiguration="testChannelBehavior"   
     name="HelloWorld">  
     <endpoint   
        address="/HelloWorld2/"  
        name="test"  
        bindingNamespace="http://www.cohowinery.com/"  
        binding="basicHttpBinding"  
        contract="IHelloWorld" />  
</service>  
```  
  
## 参照  
 <xref:System.ServiceModel.Configuration.ServiceElement>   
 [サービスの構成](../../../../../docs/framework/wcf/configuring-services.md)
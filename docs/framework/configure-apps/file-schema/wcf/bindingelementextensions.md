---
title: "&lt;bindingElementExtensions&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;bindingElementExtensions&gt;
このセクションは、コンピューターまたはアプリケーションの構成ファイルからカスタム バインディング要素を使用できます。  このコレクションにカスタム バインディング要素を追加するには、`add` キーワードを使用し、要素の `type` 属性をバインディング要素拡張に設定して、`name` 属性をカスタム バインディング要素に設定します。  
  
 バインディングの拡張により、ユーザーは、カスタム バインディングの一部として使用するユーザー定義のバインディング要素を作成できます。  プログラムではバインディング拡張は、抽象クラス <xref:System.ServiceModel.Channels.BindingElement> を実装する型です。  構成ファイルでは、`bindingElementExtensions` セクションは、拡張要素を定義するために使用されます。  
  
 次の例は、`add` 要素と `name` 属性を使用して、構成ファイルの `bindingElementExtensions` セクションにバインディング拡張を追加します。  
  
```  
<system.serviceModel>  
    <extensions>  
        <bindingElementExtensions>  
           <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportSection, UdpTransport,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </bindingElementExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
 構成機能を要素に追加するには、ユーザーは `bindingElementExtensionSection` を記述して登録する必要があります。  詳細については、<xref:System.Configuration> を参照してください。  
  
 要素とその構成の型を定義したら、次の例に示すように拡張をカスタム バインディングの一部として使用できます。  
  
```  
<customBinding>  
     <binding name="test2">  
         <udpTransport />  
         <binaryMessageEncoding maxReadPoolSize="211" maxWritePoolSize="2132"  
             maxSessionSize="3141" />  
         </binding>  
</customBinding>  
```  
  
## 参照  
 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>   
 [バインディングの拡張](../../../../../docs/framework/wcf/extending/extending-bindings.md)
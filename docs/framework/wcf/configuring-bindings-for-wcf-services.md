---
title: "Windows Communication Foundation サービスのバインディングの構成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "バインディング構成 [WCF]"
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
caps.latest.revision: 36
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 36
---
# Windows Communication Foundation サービスのバインディングの構成
アプリケーションの作成では、アプリケーションの配置後は各種決定事項を管理者に任せる場合がよくあります。たとえば、どのサービス アドレス \(URI \(Uniform Resource Identifier\)\) を使用するかなどの情報は、多くの場合、前もって知る方法がありません。アドレスをハードコーディングする代わりに、サービスの作成後に管理者が指定する方が便利です。構成を活用することで、この柔軟性が得られます。  
  
> [!NOTE]
>  構成ファイルをすばやく作成するには、`/config` スイッチを指定して [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を使用します。  
  
## 主要なセクション  
 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 構成スキームは、3 つの主要なセクション \(`serviceModel`、`bindings`、および `services`\) で構成されます。  
  
```  
<configuration>  
    <system.serviceModel>  
        <bindings>  
        </bindings>  
        <services>  
        </services>  
        <behaviors>  
        </behaviors>  
    </system.serviceModel>  
</configuration>  
```  
  
### ServiceModel 要素  
 `system.ServiceModel` 要素によって囲まれたこのセクションを使用して、1 つ以上のエンドポイントを持つサービス型、およびサービスの設定を構成できます。各エンドポイントでは、アドレス、コントラクト、およびバインディングをそれぞれ 1 つずつ構成できます。エンドポイント[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[エンドポイントの作成の概要](../../../docs/framework/wcf/endpoint-creation-overview.md)」を参照してください。エンドポイントを指定しない場合、ランタイムは、既定のエンドポイントを追加します。既定のエンドポイント、バインディング、および動作[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[簡略化された構成](../../../docs/framework/wcf/simplified-configuration.md)」および「[WCF サービスの簡略化された構成](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)」を参照してください。  
  
 バインディングはトランスポート \(HTTP、TCP、パイプ、およびメッセージ キュー\) とプロトコル \(セキュリティ、信頼性、およびトランザクション フロー\) を指定し、バインディング要素で構成されます。各バインディング要素は、エンドポイントの通信方法のさまざまな側面を指定します。  
  
 たとえば、[\<basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) 要素を指定すると、エンドポイントのトランスポートとして HTTP が使用されます。このエンドポイントを使用するサービスが開かれる実行時に、エンドポイントとの接続に HTTP が使用されます。  
  
 バインディングには、定義済みバインディングとカスタム バインディングの 2 種類があります。定義済みバインディングには、一般的なシナリオで使用される要素の組み合わせが含まれています。[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] で提供される定義済みバインディングの種類の一覧については、「[システム標準のバインディング](../../../docs/framework/wcf/system-provided-bindings.md)」を参照してください。定義済みバインディング コレクションに、サービス アプリケーションに必要な正しい機能の組み合わせがないときは、カスタム バインディングを作成して、そのアプリケーションの要件を満たすことができます。カスタム バインディング[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[\<customBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)」を参照してください。  
  
 次の 4 つの例は、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスの設定に使用される最も一般的なバインディング構成を示しています。  
  
#### バインディングの種類を使用するエンドポイントの指定  
 最初の例は、アドレス、コントラクト、およびバインディングをそれぞれ 1 つずつ使用して構成されたエンドポイントを指定する方法を示しています。  
  
```  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!—- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />  
  </endpoint>  
</service>  
```  
  
 この例では、`name` 属性は、構成がどのサービス型に対するものであるかを示します。`HelloWorld` コントラクトを使用してコードでサービスを作成すると、そのサービスは、この例の構成に定義されているすべてのエンドポイントと共に初期化されます。アセンブリにサービス コントラクトが 1 つしか実装されない場合、サービスは使用可能なタイプだけを使用するため、`name` 属性を省略できます。この属性が受け取る文字列は、`Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null` の形式で指定される必要があります。  
  
 `address` 属性では、他のエンドポイントがこのサービスと通信するために使用する URI を指定します。この URI は、絶対パスでも相対パスでもかまいません。相対アドレスを指定すると、ホストは、そのバインディングで使用されるトランスポート スキームに適したベース アドレスを提供します。アドレスが構成されていない場合、ベース アドレスはそのエンドポイントのアドレスと見なされます。  
  
 `contract` 属性では、このエンドポイントが公開するコントラクトを指定します。サービス実装の型は、コントラクト型を実装する必要があります。サービス実装が単一のコントラクト型を実装する場合は、このプロパティを省略できます。  
  
 `binding` 属性では、この特定のエンドポイントに使用される定義済みバインディングまたはカスタム バインディングを選択します。バインディングが明示的に選択されていないエンドポイントでは、既定のバインディング選択 \(`BasicHttpBinding`\) を使用します。  
  
#### 定義済みバインディングの変更  
 次の例では、定義済みバインディングを変更します。これにより、サービスの任意のエンドポイントを構成するために使用できるようになります。バインディングの変更では、<xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> 値を 1 秒に設定します。このプロパティは、<xref:System.TimeSpan> オブジェクトを返します。  
  
 変更されたバインディングは、バインディング セクションにあります。この変更したバインディングは、`endpoint` 要素の `binding` 属性を設定することにより、任意のエンドポイントを作成するときに使用できます。  
  
> [!NOTE]
>  バインディングに特定の名前を付ける場合、サービス エンドポイントで指定した `bindingConfiguration` と同じ名前にする必要があります。  
  
```  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />  
  </endpoint>  
</service>  
<bindings>  
    <basicHttpBinding   
        receiveTimeout="00:00:01"  
    />  
</bindings>  
```  
  
## サービスに適用する動作の構成  
 次の例では、サービス型に対して、特定の動作を構成します。サービスに照会し、メタデータから Web サービス記述言語 \(WSDL: Web Services Description Language\) のドキュメントを生成するには、`ServiceMetadataBehavior` 要素を使用して [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を有効にします。  
  
> [!NOTE]
>  動作に特定の名前を付ける場合、サービスまたはエンドポイント セクションで指定した `behaviorConfiguration` と同じ名前にする必要があります。  
  
```  
<behaviors>  
    <behavior>  
        <ServiceMetadata httpGetEnabled="true" />   
    </behavior>  
</behaviors>  
<services>  
    <service   
       name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
       <endpoint   
          address="http://computer:8080/Hello"  
          contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
          binding="basicHttpBinding" />  
       </endpoint>  
    </service>  
</services>  
```  
  
 前の構成では、クライアントが "HelloWorld" の型指定されたサービスを呼び出してメタデータを取得できます。  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## 異なるバインディング値を使用する 2 つのエンドポイントを持つサービスの指定  
 この最後の例では、`HelloWorld` サービス型に 2 つのエンドポイントを構成します。各エンドポイントでは、同じバインディングの種類を使用しますが、カスタマイズした異なる  `bindingConfiguration` 属性を使用します \(それぞれで `basicHttpBinding` を変更\)。  
  
```  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
    <endpoint  
        address="http://computer:8080/Hello1"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="shortTimeout"  
    </endpoint>  
    <endpoint  
        address="http://computer:8080/Hello2"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="Secure"  
     </endpoint>  
</service>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure" />  
        <Security mode="Transport" />  
</bindings>  
```  
  
 次の例に示すように、`protocolMapping` セクションを追加してバインディングを構成することによって、既定の構成を使用する同じ動作を取得できます。  
  
```xml  
<protocolMapping>  
    <add scheme=”http” binding=”basicHttpBinding” bindingConfiguration=”shortTimeout” />  
    <add scheme=”https” binding=”basicHttpBinding” bindingConfiguration=”Secure” />  
</protocolMapping>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure" />  
        <Security mode="Transport" />  
</bindings>  
```  
  
## 参照  
 [簡略化された構成](../../../docs/framework/wcf/simplified-configuration.md)   
 [システム標準のバインディング](../../../docs/framework/wcf/system-provided-bindings.md)   
 [エンドポイントの作成の概要](../../../docs/framework/wcf/endpoint-creation-overview.md)   
 [サービスとクライアントを構成するためのバインディングの使用](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
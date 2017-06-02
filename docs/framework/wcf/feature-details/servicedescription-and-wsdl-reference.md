---
title: "ServiceDescription と WSDL 参照 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eedc025d-abd9-46b1-bf3b-61d2d5c95fd6
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# ServiceDescription と WSDL 参照
ここでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] で行われる Web サービス記述言語 \(WSDL\) ドキュメントと <xref:System.ServiceModel.Description.ServiceDescription> インスタンスの間のマッピングについて説明します。  
  
## ServiceDescription から WSDL 1.1 へのマッピング  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用して、サービスの <xref:System.ServiceModel.Description.ServiceDescription> インスタンスから WSDL ドキュメントをエクスポートできます。  WSDL ドキュメントは、メタデータ エンドポイントを公開したときに自動的にサービスに対して生成されます。  
  
 また、`WsdlImporter` 型を使用して、WSDL ドキュメントから <xref:System.ServiceModel.Description.ServiceEndpoint> インスタンス、<xref:System.ServiceModel.Description.ContractDescription> インスタンス、および <xref:System.ServiceModel.Channels.Binding> インスタンスをインポートできます。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によってエクスポートされる WSDL ドキュメントは、外部の XML スキーマ ドキュメントから使用する XML スキーマ定義をインポートします。  データ型がサービスで使用するターゲット名前空間ごとに、個別の XML スキーマ ドキュメントがエクスポートされます。  同様に、サービス コントラクトが使用するターゲット名前空間ごとに、個別の WSDL ドキュメントがエクスポートされます。  
  
### ServiceDescription  
 <xref:System.ServiceModel.Description.ServiceDescription> インスタンスは `wsdl:service` 要素にマップされます。  <xref:System.ServiceModel.Description.ServiceDescription> インスタンスは、それぞれが個別の `wsdl:port` 要素にマップされる <xref:System.ServiceModel.Description.ServiceEndpoint> インスタンスのコレクションを格納します。  
  
|プロパティ|WSDL マッピング|  
|-----------|----------------|  
|`Name`|サービスの `wsdl:service`\/@name 値|  
|`Namespace`|サービスの `wsdl:service` 定義の targetNamespace|  
|`Endpoints`|サービスの `wsdl:port` 定義|  
  
### ServiceEndpoint  
 <xref:System.ServiceModel.Description.ServiceEndpoint> インスタンスは `wsdl:port` 要素にマップされます。  <xref:System.ServiceModel.Description.ServiceEndpoint> インスタンスは、アドレス、バインディング、およびコントラクトを格納します。  
  
 <xref:System.ServiceModel.Description.IWsdlExportExtension> インターフェイスを実装するエンドポイント動作は、その動作が関連付けられているエンドポイントの `wsdl:port` 要素を変更できます。  
  
|プロパティ|WSDL マッピング|  
|-----------|----------------|  
|`Name`|エンドポイントの `wsdl:port`\/@name 値およびエンドポイント バインディングの `wsdl:binding`\/@name 値|  
|`Address`|エンドポイントの `wsdl:port` 定義のアドレス<br /><br /> アドレスの形式は、エンドポイントのトランスポートによって決まります。  たとえば、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でサポートされるトランスポートの場合、SOAP アドレスまたはエンドポイント参照になります。|  
|`Binding`|エンドポイントの `wsdl:binding` 定義<br /><br /> `wsdl:binding` 定義とは異なり、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のバインディングはどのコントラクトにも関連付けられません。|  
|`Contract`|エンドポイントの `wsdl:portType` 定義|  
|`Behaviors`|<xref:System.ServiceModel.Description.IWsdlExportExtension> インターフェイスを実装するエンドポイント動作は、エンドポイントの `wsdl:port` を変更できます。|  
  
### バインディング  
 `ServiceEndpoint` インスタンスのバインディング インスタンスは、`wsdl:binding` 定義にマップされます。  特定の `wsdl:portType` 定義に関連付ける必要がある `wsdl:binding` 定義とは異なり、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のバインディングは、どのコントラクトにも依存しません。  
  
 バインディングは、バインド要素のコレクションで構成されます。  各要素は、エンドポイントがクライアントと通信する方法の一部分を記述します。  また、バインディングには、エンドポイントの <xref:System.ServiceModel.EnvelopeVersion> と <xref:System.ServiceModel.Channels.AddressingVersion> を示すための <xref:System.ServiceModel.Channels.MessageVersion> があります。  
  
|プロパティ|WSDL マッピング|  
|-----------|----------------|  
|`Name`|エンドポイントの既定の名前で使用されます。この名前は、バインディング名にコントラクト名を追加し、アンダースコアで区切った形で表記されます。|  
|`Namespace`|`wsdl:binding` 定義の `targetNamespace`。<br /><br /> インポートでは、WSDL ポートに関連付けられたポリシーがある場合、インポートされたバインディング名前空間は、`wsdl:port` 定義の `targetNamespace` にマップされます。|  
|`BindingElementCollection` \(`CreateBindingElements`\(\) メソッドによって返されるプロパティとして\)|`wsdl:binding` 定義に対するさまざまなドメイン固有の拡張。通常は、ポリシー アサーション。|  
|`MessageVersion`|エンドポイントの `EnvelopeVersion` および `AddressingVersion`。<br /><br /> `MessageVersion.None` が指定されている場合、WSDL バインディングは SOAP バインディングを格納せず、WSDL ポートは WS\-Addressing コンテンツを含みません。  この設定は、通常、Plain Old XML \(POX\) エンドポイントに対して使用されます。|  
  
#### BindingElements  
 エンドポイント バインディングのバインド要素は、ポリシー アサーションなど、`wsdl:binding` のさまざまな WSDL 拡張にマップされます。  
  
 SOAP バインディングのトランスポート URI \(Uniform Resource Identifier\) は、バインディングの <xref:System.ServiceModel.Channels.TransportBindingElement> によって決まります。  
  
#### AddressingVersion  
 バインディングの `AddressingVersion` は、`wsd:port` で使用されるアドレス指定のバージョンにマップされます。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、SOAP 1.1 と SOAP 1.2 のアドレスおよび WS\-Addressing 08\/2004 と WS\-Addressing 1.0 のエンドポイント参照をサポートします。  
  
#### EnvelopeVersion  
 バインディングの `EnvelopeVersion` は、`wsdl:binding` で使用される SOAP のバージョンにマップされます。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、SOAP 1.1 と SOAP 1.2 のバインディングをサポートします。  
  
### コントラクト  
 `ServiceEndpoint` インスタンスの <xref:System.ServiceModel.Description.ContractDescription> インスタンスは、`wsdl:portType` にマップされます。  `ContractDescription` インスタンスは、特定のコントラクトのすべての操作を記述します。  
  
|プロパティ|WSDL マッピング|  
|-----------|----------------|  
|`Name`|コントラクトの `wsdl:portType`\/@name 値|  
|`Namespace`|`wsdl:portType` 定義の targetNamespace|  
|`SessionMode`|コントラクトの `wsdl:portType`\/@msc:usingSession 値。  この属性は、WSDL 1.1 用の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 拡張です。|  
|`Operations`|コントラクトの `wsdl:operation` 定義|  
  
### 操作  
 <xref:System.ServiceModel.Description.OperationDescription> インスタンスは、`wsdl:portType`\/`wsdl:operation` にマップされます。  `OperationDescription` は、操作のメッセージを記述する `MessageDescription` インスタンスのコレクションを格納します。  
  
 主に、2 つの操作動作 `DataContractSerializerOperationBehavior` および `XmlSerializerOperationBehavior` が、`OperationDescription` を WSDL ドキュメントにマップする方法に関与しています。  
  
|プロパティ|WSDL マッピング|  
|-----------|----------------|  
|`Name`|操作の `wsdl:portType`\/`wsdl:operation`\/@name 値|  
|`ProtectionLevel`|この操作の `wsdl:binding/wsdl:operation` メッセージに関連付けられたセキュリティ ポリシーの保護アサーション|  
|`IsInitiating`|操作の `wsdl:portType`\/`wsdl:operation`\/@msc:isInitiating 値。  この属性は、WSDL 1.1 用の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 拡張です。|  
|`IsTerminating`|操作の `wsdl:portType`\/`wsdl:operation`\/@msc:isTerminating 値。  この属性は、WSDL 1.1 用の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 拡張です。|  
|`Messages`|操作の `wsdl:portType`\/`wsdl:operation`\/`wsdl:input` メッセージおよび `wsdl:portType`\/`wsdl:operation`\/`wsdl:output` メッセージ|  
|`Faults`|操作の `wsdl:portType`\/`wsdl:operation`\/`wsdl:fault` 定義|  
|`Behaviors`|`DataContractSerializerOperationBehavior` および `XmlSerializerOperationBehavior` は、操作バインディングおよび操作メッセージを扱います。|  
  
#### DataContractSerializerOperationBehavior  
 操作の `DataContractSerializerOperationBehavior` は、その操作の WSDL メッセージとバインディングをエクスポートする `IWsdlExportExtension` の実装です。  XML スキーマ型は、`XsdDataContractExporter` を使用してエクスポートされます。  また、`DataContractSerializerOperationBehavior` では、その操作に使用する使用方法、スタイル、およびスキーマ エクスポーターとインポーターを決定します。  
  
|プロパティ|WSDL マッピング|  
|-----------|----------------|  
|`DataContractFormatAttribute`|この属性の `Style` プロパティは、操作の `wsdl:binding`\/`wsdl:operation`\/`soap:operation`\/@style 値にマップされます。<br /><br /> `DataContractSerializerOperationBehavior` は、WSDL のスキーマ型のリテラル使用だけをサポートします。|  
  
#### XmlSerializerOperationBehavior  
 操作の `XmlSerializerOperationBehavior` は、その操作の WSDL メッセージとバインディングをエクスポートする `IWsdlExportExtension` の実装です。  XML スキーマ型は、`XmlSchemaExporter` を使用してエクスポートされます。  また、`XmlSerializerOperationBehavior` では、その操作に使用する使用方法、スタイル、およびスキーマ エクスポーターとインポーターを決定します。  
  
|プロパティ|WSDL マッピング|  
|-----------|----------------|  
|`XmlSerializerFormatAttribute`|この属性の `Style` プロパティは、操作の `wsdl:binding`\/`wsdl:operation`\/`soap:operation`\/@style 値にマップされます。<br /><br /> この属性の `Use` プロパティは、操作のすべてのメッセージについて、`wsdl:binding`\/`wsdl:operation`\/`soap:operation`\/\*\/@use 値にマップされます。|  
  
### \[メッセージ\]  
 `MessageDescription` インスタンスは、操作の `wsdl:portType`\/`wsdl:operation`\/`wsdl:input` メッセージまたは `wsdl:portType`\/`wsdl:operation`\/`wsdl:output` メッセージによって参照される `wsdl:message` にマップされます。  `MessageDescription` には、本文とヘッダーがあります。  
  
|プロパティ|WSDL マッピング|  
|-----------|----------------|  
|`Action`|メッセージの SOAP アクションまたは WS\-Addressing アクション。<br /><br /> Action 文字列 "\*" を使用する操作は、WSDL では表示されません。|  
|`Direction`|`MessageDirection.Input` は `wsdl:input` にマップされます。<br /><br /> `MessageDirection.Output` は `wsdl:output` にマップされます。|  
|`ProtectionLevel`|このメッセージの `wsdl:message` 定義に関連付けられたセキュリティ ポリシーの保護アサーション|  
|`Body`|メッセージのメッセージ本文|  
|`Headers`|メッセージのヘッダー|  
|`ContractDescription.Name`, `OperationContract.Name`|エクスポートするときに、`wsdl:message`\/@name 値を派生するために使用されます。|  
  
#### メッセージ本文  
 `MessageBodyDescription` インスタンスは、メッセージ本文の `wsdl:message`\/`wsdl:part` 定義にマップされます。  メッセージ本文は、ラップされている場合とベアの場合があります。  
  
|プロパティ|WSDL マッピング|  
|-----------|----------------|  
|`WrapperName`|スタイルが RPC 以外の場合、`WrapperName` は、@name が "parameters" に設定された `wsdl:message`\/`wsdl:part` によって参照される要素名にマップされます。|  
|`WrapperNamespace`|スタイルが RPC 以外の場合、`WrapperNamespace` は、@name が "parameters" に設定された `wsdl:message`\/`wsdl:part` の要素の名前空間にマップされます。|  
|`Parts`|このメッセージ本文のメッセージ部分|  
|`ReturnValue`|ラッパー要素が存在する場合 \(ドキュメント ラップ スタイルまたは RPC スタイル\)、そのラッパー要素の子要素。存在しない場合、メッセージに最初に現れる `wsdl:message`\/`wsdl:part`。|  
  
#### メッセージ部分  
 `MessagePartDescription` インスタンスは、`wsdl:message`\/`wsdl:part` およびメッセージ部分が指す XML スキーマ型または要素にマップされます。  
  
|プロパティ|WSDL マッピング|  
|-----------|----------------|  
|`Name`|メッセージ部分の `wsd:message`\/`wsdl:part`\/@name 値およびメッセージ部分が指す要素の名前|  
|`Namespace`|メッセージ部分が指す要素の名前空間|  
|`Index`|メッセージの `wsdl:message`\/`wsdl:part` のインデックス|  
|`ProtectionLevel`|このメッセージ部分の `wsdl:message` 定義に関連付けられたセキュリティ ポリシーの保護アサーション。  ポリシーは、特定のメッセージ部分を指すためにパラメーター化されます。|  
|`MessageType`|メッセージ部分が指す要素の XML スキーマ型|  
  
#### メッセージ ヘッダー  
 `MessageHeaderDescription` インスタンスは、メッセージ部分の `soap:header` バインディングにもマップされるメッセージ部分です。  
  
### エラー  
 `FaultDescription` インスタンスは、`wsdl:portType`\/`wsdl:operation`\/`wsdl:fault` 定義およびその関連する `wsdl:message` 定義にマップされます。  `wsdl:message` は、関連する WSDL ポートの種類と同じターゲット名前空間に追加されます。  `wsdl:message` には、`FaultDescription` インスタンスの `DefaultType` プロパティ値に相当する XML スキーマ要素を指す、"detail" という名前の 1 つのメッセージ部分があります。  
  
|プロパティ|WSDL マッピング|  
|-----------|----------------|  
|`Name`|エラーの `wsdl:portType`\/`wsdl:operation`\/`wsdl:fault`\/@name 値|  
|`Namespace`|エラー詳細メッセージ部分が指す XML スキーマ要素の名前空間|  
|`Action`|エラーの SOAP アクションまたは WS\-Addressing アクション|  
|`ProtectionLevel`|このエラーの `wsdl:message` 定義に関連付けられたセキュリティ ポリシーの保護アサーション|  
|`DetailType`|詳細メッセージ部分が指す要素の XML スキーマ型|  
|`Name, ContractDescription.Name, OperationDescription.Name,`|エラー メッセージの `wsdl:message`\/@name 値を派生するために使用されます。|  
  
## 参照  
 <xref:System.ServiceModel.Description>
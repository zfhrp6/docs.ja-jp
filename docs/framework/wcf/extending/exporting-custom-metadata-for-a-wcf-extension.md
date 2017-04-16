---
title: "WCF 拡張に対するカスタム メタデータのエクスポート | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 53c93882-f8ba-4192-965b-787b5e3f09c0
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# WCF 拡張に対するカスタム メタデータのエクスポート
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、メタデータのエクスポートは、サービス エンドポイントを説明したり、それらを並行して計画したりするプロセスで、クライアントがサービスの使用方法を理解する標準化表現です。カスタム メタデータは、システム指定のメタデータ エクスポーターでエクスポートできない XML 要素で構成されます。通常、これは、ユーザー定義動作のカスタム WSDL 要素とバインド要素、およびバインディングとコントラクトの機能と要件に関するポリシー アサーションを含みます。  
  
 ここでは、カスタム WSDL またはポリシー アサーションのエクスポートについて説明し、エクスポート プロセス自体には重点を置きません。メタデータがカスタムであるか、システムによって作成されたかに関係なく、メタデータをエクスポートおよびインポートする型の使用方法の詳細については、「[メタデータのエクスポートとインポート](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)」を参照してください。  
  
## 概要  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName> を使用してメタデータを公開すると、システム指定の属性とバインディングを使用して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] がサポートできるすべてのコントラクトとバインディングについて、<xref:System.ServiceModel.Description.ServiceDescription?displayProperty=fullName> が検査され、XSD と WSDL \(ポリシー アサーションを含む\) が生成されます。ただし、カスタム動作属性やバインド要素を適切にエクスポートするには、あらかじめサポートしておく必要があります。  
  
 ここでは、次の内容について説明します。  
  
1.  WSDL を発行する前に WSDL の生成データを公開する <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=fullName> インターフェイスを実装して使用する方法。  
  
2.  WSDL データに含まれるポリシー アサーションをエクスポートする前にポリシー データを公開する <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=fullName> インターフェイスを実装して使用する方法。  
  
 カスタム WSDL とポリシー アサーションのインポートの詳細については、「[WCF 拡張に対するカスタム メタデータのインポート](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)」を参照してください。  
  
## カスタム WSDL 要素のエクスポート  
 操作の動作、コントラクトの動作、エンドポイントの動作、またはバインド要素 <xref:System.ServiceModel.Description.IWsdlExportExtension> \(それぞれ <xref:System.ServiceModel.Description.IOperationBehavior>、<xref:System.ServiceModel.Description.IContractBehavior>、<xref:System.ServiceModel.Description.IEndpointBehavior>、<xref:System.ServiceModel.Channels.BindingElement?displayProperty=fullName>\) を実装し、エクスポートしようとしているサービスの説明に動作またはバインド要素を挿入します \(動作の挿入の詳細については、「[動作を使用したランタイムの構成と拡張](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)」を参照してください\)。<xref:System.ServiceModel.Description.IWsdlExportExtension> はエンドポイントごとに呼び出され、コントラクトがエクスポートされていない場合は、各エンドポイントによって最初にコントラクトがエクスポートされます。必要に応じて、次のいずれかのエクスポート プロセスに参加できます。  
  
-   <xref:System.ServiceModel.Description.WsdlContractConversionContext> を使用して、エクスポートされたメタデータを <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> メソッドで変更する。  
  
-   <xref:System.ServiceModel.Description.WsdlEndpointConversionContext> を使用して、エンドポイントに対してエクスポートされたメタデータを <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> メソッドで変更する。  
  
 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> メソッドは、エクスポートされる <xref:System.ServiceModel.Description.ContractDescription?displayProperty=fullName> インスタンスに含まれるすべての <xref:System.ServiceModel.Description.IWsdlExportExtension> 実装で呼び出されます。<xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> メソッドは、エクスポートされる <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=fullName> インスタンスを持つすべての <xref:System.ServiceModel.Description.IWsdlExportExtension> 実装で呼び出されます。  
  
 詳細については、「[方法 : カスタム WSDL をエクスポートする](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)」および「[カスタム WSDL パブリケーション](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)」のサンプルを参照してください。  
  
## カスタム ポリシー アサーションのエクスポート  
 <xref:System.ServiceModel.Channels.BindingElement> に <xref:System.ServiceModel.Description.IPolicyExportExtension> を実装し、バインド要素をバインディングに追加して、バインディングのサポートとコントラクトの機能に関するカスタム ポリシー アサーションを WSDL に書き込みます。バインディングに実装されたバインド要素をエクスポートすると、<xref:System.ServiceModel.Description.IPolicyExportExtension> が 1 回呼び出され、<xref:System.ServiceModel.Description.PolicyConversionContext> を <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> メソッドに渡します。<xref:System.ServiceModel.Description.PolicyConversionContext> インスタンスに対してこのメソッドを使用すると、メッセージ、操作、またはエンドポイント サブジェクトで WSDL バインディングに結び付けられているポリシー アサーションを追加できます。  
  
 詳細については、「[方法 : カスタム ポリシー アサーションをエクスポートする](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md)」を参照してください。  
  
## 参照  
 [方法 : カスタム WSDL をエクスポートする](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)   
 [方法 : カスタム ポリシー アサーションをエクスポートする](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md)   
 [WCF 拡張に対するカスタム メタデータのインポート](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
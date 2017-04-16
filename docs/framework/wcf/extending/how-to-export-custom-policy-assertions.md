---
title: "方法 : カスタム ポリシー アサーションをエクスポートする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 方法 : カスタム ポリシー アサーションをエクスポートする
ポリシー アサーションはサービス エンドポイントの機能と要件を説明します。サービス アプリケーションは、サービス メタデータに含まれるカスタム ポリシー アサーションを使用して、エンドポイントのバインディングまたはコントラクトのカスタマイズ情報をクライアント アプリケーションに伝達します。[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用すると、伝達している機能または要件に応じて、エンドポイント、操作、またはメッセージ サブジェクトで WSDL バインディングに結び付けられているポリシー表現のアサーションをエクスポートできます。  
  
 カスタム ポリシー アサーションは、<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=fullName> インターフェイスを <xref:System.ServiceModel.Channels.BindingElement?displayProperty=fullName> に実装して、サービス エンドポイントのバインディングにバインド要素を直接挿入するか、またはアプリケーション構成ファイルにバインド要素を登録することによってエクスポートされます。ポリシーのエクスポートの実装では、<xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> メソッドに渡された <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=fullName> の適切な <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=fullName> に、<xref:System.Xml.XmlElement?displayProperty=fullName> インスタンスとしてカスタム ポリシー アサーションを追加する必要があります。  
  
 また、<xref:System.ServiceModel.Description.WsdlExporter> クラスの <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> プロパティをチェックし、入れ子になったポリシー表現およびポリシー フレームワーク属性を、指定されたポリシー バージョンに基づいた正しい名前空間にエクスポートする必要もあります。  
  
 カスタム ポリシー アサーションをインポートする方法については、「<xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=fullName>」および「[方法 : カスタム ポリシー アサーションをインポートする](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)」を参照してください。  
  
### カスタム ポリシー アサーションをエクスポートするには  
  
1.  <xref:System.ServiceModel.Channels.BindingElement?displayProperty=fullName> に <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=fullName> インターフェイスを実装します。バインディング レベルでのカスタム ポリシー アサーションの実装を次のコード例に示します。  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2.  プログラムまたはアプリケーション構成ファイルを使用して、エンドポイントのバインディングにバインド要素を挿入します。次の手順を参照してください。  
  
### アプリケーション構成ファイルを使用してバインディングを挿入するには  
  
1.  カスタム ポリシー アサーション バインド要素の <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=fullName> を実装します。  
  
2.  [\<bindingElementExtensions\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md) 要素を使用して、そのバインド要素拡張を構成ファイルに追加します。  
  
3.  <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=fullName> を使用してカスタム バインディングを作成します。  
  
### プログラムでバインド要素を挿入するには  
  
1.  新しい <xref:System.ServiceModel.Channels.BindingElement?displayProperty=fullName> を作成して <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=fullName> に追加します。  
  
2.  手順 1. のカスタム バインディングを新しいエンドポイントに追加し、<xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> メソッドを呼び出してその新しいサービス エンドポイントを <xref:System.ServiceModel.ServiceHost?displayProperty=fullName> に追加します。  
  
3.  <xref:System.ServiceModel.ServiceHost> を開きます。カスタム バインディングの作成と、プログラムによるバインド要素の挿入を次のコード例に示します。  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## 参照  
 <xref:System.ServiceModel.Description.IPolicyImportExtension>   
 <xref:System.ServiceModel.Description.IPolicyExportExtension>   
 [方法 : カスタム ポリシー アサーションをインポートする](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)
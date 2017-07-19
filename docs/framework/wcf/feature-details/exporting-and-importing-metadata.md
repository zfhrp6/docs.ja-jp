---
title: "メタデータのエクスポートとインポート | Microsoft Docs"
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
  - "メタデータ [WCF], エクスポートとインポート"
ms.assetid: 614a75bb-e0b0-4c95-b6d8-02cb5e5ddb38
caps.latest.revision: 19
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 19
---
# メタデータのエクスポートとインポート
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、メタデータのエクスポートは、サービス エンドポイントを説明したり、クライアントがサービスの使用方法を理解するために使用できる、対応した標準的な表現にメタデータを移し替えたりするプロセスです。サービス メタデータのインポートは <xref:System.ServiceModel.Description.ServiceEndpoint> インスタンス、またはサービス メタデータの一部を生成するプロセスです。  
  
## メタデータのエクスポート  
 メタデータを <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=fullName> インスタンスからエクスポートするには、<xref:System.ServiceModel.Description.MetadataExporter> 抽象クラスの実装を使用します。<xref:System.ServiceModel.Description.WsdlExporter> 型は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に含まれる <xref:System.ServiceModel.Description.MetadataExporter> 抽象クラスの実装です。  
  
 <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=fullName> 型は Web サービス記述言語 \(WSDL: Web Services Description Language\) メタデータを生成します。このメタデータには、<xref:System.ServiceModel.Description.MetadataSet> インスタンス内にカプセル化されたポリシー表現が関連付けられています。<xref:System.ServiceModel.Description.WsdlExporter?displayProperty=fullName> インスタンスを使用すると、<xref:System.ServiceModel.Description.ContractDescription> オブジェクトと <xref:System.ServiceModel.Description.ServiceEndpoint> オブジェクトのメタデータを反復してエクスポートできます。<xref:System.ServiceModel.Description.ServiceEndpoint> オブジェクトのコレクションをエクスポートして、特定のサービス名に関連付けることもできます。  
  
> [!NOTE]
>  `WsdlExporter` は、`ContractDescription.GetContract` メソッドを使用するか、`ServiceHost` インスタンスの `ServiceDescription` の一部として作成された `ContractDescription` インスタンスなど、共通言語ランタイム \(CLR\) の型情報を含む `ContractDescription` インスタンスからメタデータをエクスポートする場合にのみ使用できます。サービス メタデータからインポートした `ContractDescription` インスタンスや、型情報を使用せずに作成したインスタンスからは、`WsdlExporter` を使用してメタデータをエクスポートできません。  
  
## メタデータのインポート  
  
### WSDL ドキュメントのインポート  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のサービス メタデータをインポートするには、<xref:System.ServiceModel.Description.MetadataImporter> 抽象クラスの実装を使用します。<xref:System.ServiceModel.Description.WsdlImporter?displayProperty=fullName> 型は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に含まれる <xref:System.ServiceModel.Description.MetadataImporter> 抽象クラスの実装です。<xref:System.ServiceModel.Description.WsdlImporter> 型は、<xref:System.ServiceModel.Description.MetadataSet> オブジェクトにまとめられた、結び付けられているポリシーを使用して WSDL メタデータをインポートします。  
  
 <xref:System.ServiceModel.Description.WsdlImporter> 型を使用すると、メタデータをインポートする方法を制御できます。すべてのエンドポイント、すべてのバインディング、またはすべてのコントラクトをインポートできます。特定の WSDL サービス、バインディング、またはポートの種類に関連付けられたすべてのエンドポイントをインポートすることもできます。また、特定の WSDL ポートのエンドポイント、特定の WSDL バインディングのバインディング、または特定の WSDL ポートの種類のコントラクトをインポートすることもできます。  
  
 また、<xref:System.ServiceModel.Description.WsdlImporter> では、インポートする必要がないコントラクトのセットを指定できるようにする <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> プロパティが公開されています。この場合、<xref:System.ServiceModel.Description.WsdlImporter> は、同じ修飾名を持つコントラクトをメタデータからインポートする代わりに、<xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> プロパティのコントラクトを使用します。  
  
### ポリシーのインポート  
 <xref:System.ServiceModel.Description.WsdlImporter> 型は、メッセージ、操作、およびエンドポイントのポリシー サブジェクトに関連付けられたポリシー表現を収集した後で、<xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> コレクションの <xref:System.ServiceModel.Description.IPolicyImportExtension> 実装を使用してポリシー表現をインポートします。  
  
 ポリシーのインポート ロジックは、同じ WSDL ドキュメント内のポリシー表現へのポリシーの参照を自動的に処理します。インポート ロジックは `wsu:Id` 属性または `xml:id` 属性で識別されます。ポリシーのインポート ロジックは、アプリケーションでポリシーの循環参照が発生しないようにポリシー表現のサイズを 4096 ノードに制限します。ノードとは、`wsp:Policy`、`wsp:All`、`wsp:ExactlyOne`、または `wsp:policyReference` 要素です。  
  
 また、ポリシーのインポート ロジックは、ポリシー表現を自動的に正規化します。入れ子になったポリシー表現や `wsp:Optional` 属性は正規化されません。実行される正規化処理の量は 4096 ステップに制限されます。各ステップでは、ポリシー アサーション、または `wsp:ExactlyOne` 要素の子要素が生成されます。  
  
 <xref:System.ServiceModel.Description.WsdlImporter> 型は、異なる WSDL ポリシー サブジェクトに結び付けられているポリシー代替手段の組み合わせを最大で 32 組まで試行します。どの組み合わせを使用しても完全にインポートできない場合は、最初の組み合わせを使用して部分カスタム バインディングが作成されます。  
  
## エラー処理  
 <xref:System.ServiceModel.Description.MetadataExporter> 型や <xref:System.ServiceModel.Description.MetadataImporter> 型は、どちらも `Errors` プロパティを公開します。このプロパティには、エクスポート プロセスおよびインポート プロセスで発生したエラー メッセージおよび警告メッセージのコレクションを格納でき、ツールの実装時に使用できます。  
  
 <xref:System.ServiceModel.Description.WsdlImporter> 型は、通常、インポート プロセスでキャッチされた例外に対して例外をスローし、対応するエラーをその `Errors` プロパティに追加します。ただし、<xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>、<xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>、<xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A>、および <xref:System.ServiceModel.Description.WsdlImporter.ImportEndpoints%2A> の各メソッドはこうした例外をスローしないため、`Errors` プロパティを調べて、これらのメソッドの呼び出し時に問題が発生したかどうかを確認する必要があります。  
  
 <xref:System.ServiceModel.Description.WsdlExporter> 型は、エクスポート プロセスでキャッチされたすべての例外を再スローします。`Errors` プロパティでは、この例外はエラーとしてキャプチャされません。<xref:System.ServiceModel.Description.WsdlExporter> は、例外をスローするとエラー状態になるため、再使用できません。ワイルドカード アクションを使用しているために操作をエクスポートできない場合や、重複したバインディング名を検出した場合、<xref:System.ServiceModel.Description.WsdlExporter> はその `Errors` プロパティに警告を追加します。  
  
## このセクションの内容  
 [方法 : メタデータをサービス エンドポイントにインポートする](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md)  
 ダウンロードされたメタデータを説明オブジェクトにインポートする方法について説明します。  
  
 [方法 : メタデータをサービス エンドポイントからエクスポートする](../../../../docs/framework/wcf/feature-details/how-to-export-metadata-from-service-endpoints.md)  
 説明オブジェクトをメタデータにエクスポートする方法について説明します。  
  
 [ServiceDescription と WSDL 参照](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)  
 説明オブジェクトと WSDL の間のマッピングについて説明します。  
  
 [方法 : Svcutil.exe を使用してコンパイル済みのサービス コードからメタデータをエクスポートする](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)  
 Svcutil.exe を使用して、コンパイル済みアセンブリのサービス型、コントラクト型、およびデータ型のメタデータをエクスポートする方法について説明します。  
  
 [データ コントラクト スキーマの参照](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)  
 XML シリアル化用の共通言語ランタイム \(CLR\) 型を表すために <xref:System.Runtime.Serialization.DataContractSerializer> が使用する XML スキーマ \(XSD\) のサブセットについて説明します。  
  
## リファレンス  
 <xref:System.ServiceModel.Description.WsdlExporter>  
  
 <xref:System.ServiceModel.Description.WsdlImporter>  
  
## 参照  
 [WCF 拡張に対するカスタム メタデータのエクスポート](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)   
 [WCF 拡張に対するカスタム メタデータのインポート](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
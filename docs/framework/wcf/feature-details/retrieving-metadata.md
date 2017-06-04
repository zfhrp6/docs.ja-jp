---
title: "メタデータを取得する | Microsoft Docs"
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
  - "メタデータ [WCF], 取得"
ms.assetid: 18d8ba4c-af0f-4827-a50b-4202d767bacc
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# メタデータを取得する
メタデータの取得は、WS\-MetadataExchange \(MEX\) メタデータ エンドポイントや HTTP\/GET メタデータ エンドポイントなどのメタデータ エンドポイントに対してメタデータを要求して取得する処理です。  
  
## Svcutil.exe を使用した、コマンドラインからのメタデータの取得  
 [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ツールを使用して、`/target:metadata` スイッチとアドレスを渡すことにより、WS\-MetadataExchange 要求または HTTP\/GET 要求を使用してサービス メタデータを取得できます。Svcutil.exe は指定したアドレスでメタデータをダウンロードし、ディスクにファイルを保存します。Svcutil.exe は内部的に <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> インスタンスを使用し、構成 \(Svcutil.exe に入力として渡されたアドレスのスキーマに一致する名前の <xref:System.ServiceModel.Description.IMetadataExchange> エンドポイント構成\) から読み込まれます。  
  
## MetadataExchangeClient を使用した、プログラムによるメタデータの取得  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、WS\-MetadataExchange 要求や HTTP\/GET 要求などの標準化プロトコルを使用してサービス メタデータを取得できます。これらのプロトコルはいずれも、<xref:System.ServiceModel.Description.MetadataExchangeClient> 型でサポートされます。メタデータ エンドポイントのアドレスとオプションのバインディングを指定することにより、<xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> 型を使用してサービス メタデータを取得します。<xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> インスタンスで使用するバインディングは、<xref:System.ServiceModel.Description.MetadataExchangeBindings> 静的クラスの既定のバインディング、ユーザー指定のバインディング、`IMetadataExchange` コントラクト用のエンドポイント構成から読み込まれたバインディングのいずれかです。<xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> は同様に、<xref:System.Net.HttpWebRequest> 型を使用して、メタデータへの HTTP URL 参照を解決できます。  
  
 既定では、<xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> インスタンスは、1 つの <xref:System.ServiceModel.ChannelFactory> インスタンスに結び付けられています。<xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> によって使用される <xref:System.ServiceModel.ChannelFactory?displayProperty=fullName> インスタンスは、<xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> 仮想メソッドを上書きすることによって変更または置換することができます。同様に、<xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=fullName> 仮想メソッドをオーバーライドすることによって、HTTP\/GET 要求を行うために <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> が使用する <xref:System.Net.HttpWebRequest> インスタンスを変更または置換できます。  
  
## このセクションの内容  
 [方法 : Svcutil.exe を使用してメタデータ ドキュメントをダウンロードする](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)  
 Svcutil.exe を使用して、メタデータ ドキュメントをダウンロードする方法を示します。  
  
 [方法 : MetadataResolver を使用してバインディング メタデータを動的に取得する](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)  
 <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=fullName> を使用して、実行時に動的にバインディング メタデータを取得する方法を示します。  
  
 [方法 : MetadataExchangeClient を使用してメタデータを取得する](../../../../docs/framework/wcf/feature-details/how-to-use-metadataexchangeclient-to-retrieve-metadata.md)  
 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> クラスを使用して、<xref:System.ServiceModel.Description.MetadataSection?displayProperty=fullName> オブジェクトを含む <xref:System.ServiceModel.Description.MetadataSet?displayProperty=fullName> オブジェクトにメタデータ ファイルをダウンロードし、ファイルに書き込んだり、他の目的に使用したりする方法を示します。  
  
## 参照  
 <xref:System.ServiceModel.Description.MetadataExchangeClient>
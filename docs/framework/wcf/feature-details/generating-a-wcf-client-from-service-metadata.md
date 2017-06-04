---
title: "サービス メタデータからの WCF クライアントの生成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27f8f545-cc44-412a-b104-617e0781b803
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# サービス メタデータからの WCF クライアントの生成
ここでは、Svcutil.exe の各種のスイッチを使用して、メタデータ ドキュメントからクライアントを生成する方法を説明します。  
  
 メタデータ ドキュメントは、永続ストレージに保存したり、オンラインで取得したりできます。オンライン取得では、WS\-MetadataExchange プロトコルまたは DISCO \(Microsoft Discovery\) プロトコルに従います。Svcutil.exe は、メタデータを取得するために次のメタデータ要求を同時に発行します。  
  
-   指定されたアドレスへの WS\-MetadataExchange \(MEX\) 要求  
  
-   指定された `/mex` 付きアドレスへの MEX 要求  
  
-   指定されたアドレスへの DISCO 要求 \(ASP.NET Web サービス の [DiscoveryClientProtocol クラス](http://go.microsoft.com/fwlink/?LinkId=94777) を使用\)  
  
 Svcutil.exe は、Web サービス記述言語 \(WSDL: Web Services Description Language\) ファイル、またはサービスから受け取ったポリシー ファイルに基づいてクライアントを生成します。ユーザー プリンシパル名 \(UPN\) は、ユーザー名、"@"、完全修飾ドメイン名 \(FQDN\) を順に連結して生成されます。ただし、Active Directory に登録されているユーザーの場合、この形式は無効であり、ツールが生成する UPN を使用すると、Kerberos 認証でエラーが発生し、エラー メッセージ **\[ログインに失敗しました\]** が表示されます。この問題を解決するには、このツールが生成するクライアント ファイルを手動で修正する必要があります。  
  
```  
svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>  
```  
  
## 型の参照と共有  
  
|オプション|説明|  
|-----------|--------|  
|**\/reference:\<file path\>**|指定されたアセンブリの型を参照します。クライアントの生成時に、このオプションを使用して、インポートするメタデータを表す型を含むアセンブリを指定します。<br /><br /> 短縮形: `/r`|  
|**\/excludeType:\<type\>**|参照されるコントラクト型から除外する完全修飾またはアセンブリ修飾の型名を指定します。<br /><br /> 短縮形: `/et`|  
  
## シリアライザーの選択  
  
|オプション|説明|  
|-----------|--------|  
|**\/serializer:Auto**|シリアライザーを自動的に選択します。これは、`DataContract` シリアライザーを使用します。この処理が失敗すると、`XmlSerializer` が使用されます。<br /><br /> 短縮形: `/ser:Auto`|  
|**\/serializer:DataContractSerializer**|シリアル化と逆シリアル化に `DataContract` シリアライザーを使用するデータ型を生成します。<br /><br /> 短縮形: `/ser:DataContractSerializer`|  
|**\/serializer:XmlSerializer**|シリアル化と逆シリアル化に `XmlSerializer` を使用するデータ型を生成します。<br /><br /> 短縮形: `/ser:XmlSerializer`|  
|**\/importXmlTypes**|`IXmlSerializable` 型として非 `DataContract` 型をインポートする `DataContract` シリアライザーを構成します。<br /><br /> 短縮形: `/ixt`|  
|**\/dataContractOnly**|`DataContract` 型に対してのみコードを生成します。`ServiceContract` 型が生成されます。<br /><br /> このオプションにはローカル メタデータ ファイルだけを指定する必要があります。<br /><br /> 短縮形: `/dconly`|  
  
## クライアントの言語の選択  
  
|オプション|説明|  
|-----------|--------|  
|**\/language:\<language\>**|コード生成に使用するプログラミング言語を指定します。Machine.config ファイルに登録された言語名か、<xref:System.CodeDom.Compiler.CodeDomProvider> から継承するクラスの完全修飾名のいずれかを指定します。<br /><br /> 値は、c\#、cs、csharp、vb、vbs、visualbasic、vbscript、javascript、c\+\+、mc、cpp になります。<br /><br /> 既定値 : csharp<br /><br /> 短縮形 : `/l`<br /><br /> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]「[CodeDomProvider クラス](http://go.microsoft.com/fwlink/?LinkId=94778)」を参照してください。|  
  
## クライアントの名前空間の選択  
  
|オプション|説明|  
|-----------|--------|  
|**\/namespace:\<string,string\>**|WSDL または XML スキーマの `targetNamespace` から共通言語ランタイム \(CLR: Common Language Runtime\) 名前空間へのマッピングを指定します。`targetNamespace` にワイルドカード \(\*\) を使用すると、マッピングを明示的に指定せずにすべての `targetNamespaces` がその CLR 名前空間にマップされます。<br /><br /> メッセージ コントラクト名が操作名と競合しないようにするには、型参照を 2 つのコロン `::` で修飾するか、名前を一意にします。<br /><br /> 既定 : `DataContracts` のスキーマ ドキュメントのターゲット名前空間から派生します。既定の名前空間は、生成される他のすべての型に使用されます。<br /><br /> 短縮形: `/n`|  
  
## データ バインディングの選択  
  
|オプション|説明|  
|-----------|--------|  
|**\/enableDataBinding**|データ バインディングを有効にするために、すべての `DataContract` 型に <xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスを実装します。<br /><br /> 短縮形: `/edb`|  
  
## 構成ファイルの生成  
  
|オプション|説明|  
|-----------|--------|  
|**\/config:\<configFile\>**|生成される構成ファイルの名前を指定します。<br /><br /> 既定値: output.config|  
|**\/mergeConfig**|既存のファイルを上書きする代わりに、生成される構成ファイルを既存のファイルにマージします。|  
|**\/noConfig**|構成ファイルを生成しません。|  
  
## 参照  
 [メタデータを使用する](../../../../docs/framework/wcf/feature-details/using-metadata.md)   
 [メタデータ アーキテクチャの概要](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
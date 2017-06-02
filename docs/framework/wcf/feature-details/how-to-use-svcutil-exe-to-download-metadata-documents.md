---
title: "方法 : Svcutil.exe を使用してメタデータ ドキュメントをダウンロードする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 方法 : Svcutil.exe を使用してメタデータ ドキュメントをダウンロードする
Svcutil.exe を使用すると、実行中のサービスからメタデータをダウンロードして、ローカル ファイルに保存できます。URL スキームが HTTP および HTTPS の場合、Svcutil.exe はメタデータの抽出に WS\-MetadataExchange および [XML Web サービス検索](http://go.microsoft.com/fwlink/?LinkId=94950)を使用します。その他の URL スキームの場合、Svcutil.exe は WS\-MetadataExchange のみを使用します。  
  
 既定で、Svcutil.exe は <xref:System.ServiceModel.Description.MetadataExchangeBindings> クラスに定義されているバインディングを使用します。WS\-MetadataExchange で使用するバインディングを構成するには、Svcutil.exe の構成ファイル \(svcutil.exe.config\) でクライアント エンドポイントを定義する必要があります。このとき、クライアント エンドポイントが `IMetadataExchange` コントラクトを使用し、メタデータ エンドポイントのアドレスの URI \(Uniform Resource Identifier\) スキームと同じ名前を持つように定義します。  
  
> [!CAUTION]
>  Svcutil.exe を実行して、それぞれに同じ名前の操作が含まれる 2 つの異なるサービス コントラクトを公開するサービスのメタデータを取得する場合、Svcutil.exe は、「.... からメタデータを取得できません」というエラーを表示します。たとえば、Get\(Car c\) 操作を含む ICarService という名前のサービス コントラクトを公開するサービスがあり、その同じサービスが Get\(Book b\) 操作を含む IBookService という名前のサービス コントラクトを公開する場合です。この問題を回避するには、次のいずれかの操作を実行します。  
>   
>  -   操作の名前を変更する。  
> -   <xref:System.ServiceModel.OperationContractAttribute.Name%2A> を別の名前に設定する。  
> -   <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> プロパティを使用して、操作の名前空間のいずれかを別の名前空間に設定する。  
  
### Svcutil.exe を使用してメタデータをダウンロードするには  
  
1.  次の場所で Svcutil.exe ツールを検索します。  
  
     C:\\Program Files\\Microsoft SDKs\\Windows\\v1.0.\\bin  
  
2.  コマンド プロンプトで、次の形式を使用してツールを起動します。  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     メタデータをダウンロードするには `/t:metadata` オプションを指定する必要があります。このオプションを指定しないと、クライアントのコードと構成が生成されます。  
  
3.  \<`url`\> 引数は、メタデータを提供するサービス エンドポイントの URL またはオンラインになっているメタデータ ドキュメントの URL を指定します。\<`epr`\> 引数では、WS\-MetadataExchange をサポートするサービス エンドポイント用の WS\-Addressing `EndpointAddress` が含まれる XML ファイルへのパスを指定します。  
  
 このツールを使用してメタデータをダウンロードするときのその他のオプションについては、「[ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)」を参照してください。  
  
## 使用例  
 次のコマンドにより、実行中のサービスからメタデータ ドキュメントがダウンロードされます。  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## 参照  
 [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
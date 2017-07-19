---
title: "WCF Data Service クライアント ユーティリティ (DataSvcUtil.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF Data Services, クライアント ライブラリ"
  - "WCF Data Services, 利用"
  - "WCF Data Services, クライアント データ クラスの生成"
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# WCF Data Service クライアント ユーティリティ (DataSvcUtil.exe)
DataSvcUtil.exe は、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] に付属するコマンドライン ツールです。このツールは、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] フィードを使用して、.NET Framework クライアント アプリケーションのデータ サービスにアクセスするために必要なクライアント データ サービス クラスを生成します。  このユーティリティでは、以下のメタデータ ソースを使用してデータ クラスを生成できます。  
  
-   データ サービスのルート URI。  ユーティリティは、データ サービスによって公開されるデータ モデルが記述されたサービス メタデータ ドキュメントを要求します。  詳細については、[OData: サービス メタデータ ドキュメント](http://go.microsoft.com/fwlink/?LinkId=186070)」を参照してください。  
  
-   [\[MC\-CSDL\]: 概念スキーマ定義ファイル形式](http://go.microsoft.com/fwlink/?LinkID=159072)の仕様で定義されているように、概念スキーマ定義言語 \(CSDL\) を使用して定義されるデータ モデル ファイル \(.csdl\)。  
  
-   Entity Framework に付属する Entity Data Model ツールを使用して作成された .edmx ファイル。  詳細については、「[\[MC\-EDMX\]: データ サービスのパッケージ形式のエンティティ データ モデル](http://go.microsoft.com/fwlink/?LinkID=178833)」の仕様を参照してください。  
  
 詳細については、「[方法: クライアント データ サービス クラスを手動で生成する](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)」を参照してください。  
  
 DataSvcUtil.exe ツールは [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ディレクトリにインストールされます。  多くの場合、C:\\Windows\\Microsoft.NET\\Framework\\v4.0 にあります。  64 ビット システムの場合は、C:\\Windows\\Microsoft.NET\\Framework64\\v4.0 にあります。  Visual Studio のコマンド プロンプトから DataSvcUtil.exe ツールにアクセスすることもできます \(**\[スタート\]** ボタンをクリックし、**\[すべてのプログラム\]**、**\[Microsoft Visual Studio 2010\]**、**\[Visual Studio ツール\]** の順にポイントして、**\[Visual Studio 2010 コマンド プロンプト\]** をクリックします\)。  
  
## 構文  
  
```  
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]  
```  
  
#### パラメーター  
  
|オプション|説明|  
|-----------|--------|  
|`/dataservicecollection`|オブジェクトをコントロールにバインドするために必要なコードも生成することを指定します。|  
|`/help`<br /><br /> または<br /><br /> `/?`|このツールのコマンド構文とオプションを表示します。|  
|`/in:` *\<file\>*|.csdl ファイルまたは .edmx ファイル、またはファイルがあるディレクトリを指定します。|  
|`/language:`\[VB&#124;CSharp\]|生成されるソース コード ファイルの言語を指定します。  既定の言語は C\# です。|  
|`/nologo`|著作権メッセージが表示されないようにします。|  
|`/out:` *\<file\>*|生成されたクライアント データ サービス クラスを含むソース コード ファイルの名前を指定します。|  
|`/uri:` *\<string\>*|[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードの URI。|  
|`/version:`\[1.0&#124;2.0\]|許容される [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] の最上位バージョンを指定します。  バージョンは、返されるデータ サービス メタデータに含まれる DataService 要素の `DataServiceVersion` 属性に基づいて決定されます。  詳細については、「[データ サービスのバージョン管理](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)」を参照してください。  `/dataservicecollection` パラメーターを指定する場合は、`/version:2.0` も指定してデータ バインディングを有効にする必要があります。|  
  
## 参照  
 [データ サービス クライアント ライブラリの生成](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)   
 [方法: データ サービス参照を追加する](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
---
title: "クライアント アプリケーションでのデータ サービスの使用 (WCF Data Services) | Microsoft Docs"
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
  - "WCF Data Services, 概要"
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# クライアント アプリケーションでのデータ サービスの使用 (WCF Data Services)
Web ブラウザーに URI を入力することで、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] フィードを公開するサービスにアクセスできます。  URI はリソースのアドレスを提供し、要求メッセージがこれらのアドレスに送信されてリソースが表す基になるデータのアクセスまたは変更を行います。  ブラウザーは HTTP GET コマンドを発行して、要求されたリソースを [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードとして返します。  詳細については、「[Web ブラウザーからサービスへのアクセス](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)」を参照してください。  
  
 Web ブラウザーは [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスが予期されたデータを返すかどうかをテストするために便利ですが、データの作成、更新、および削除も行うことができる運用 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスは、一般的にアプリケーション コードや Web ページのスクリプト言語を使用してアクセスします。  このトピックでは、クライアント アプリケーションから [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードにアクセスする方法の概要について説明します。  
  
## REST セマンティクスを使用したデータのアクセスおよび変更  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] は、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを公開するサービスと、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを使用するアプリケーションの間の相互運用性を保証するのに役立ちます。アプリケーションは、特定の HTTP アクションの要求メッセージ、およびアクションを実行するエンティティ リソースのアドレスを指定する URI を送信して、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ベースのサービス内のデータのアクセスおよび変更を行います。  エンティティ データを指定する必要がある場合、メッセージの本文に、エンコードされたペイロードとして明示的に指定します。  
  
### HTTP アクション  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] は、アドレス指定されたリソースが表すエンティティ データに対する操作の作成、読み取り、更新、および削除を実行する次の HTTP アクションをサポートします。  
  
-   **HTTP GET** \- これは、ブラウザーからリソースにアクセスするときの既定のアクションです。  要求メッセージではペイロードは指定されず、要求されたデータを含むペイロードを含む応答メソッドが返されます。  
  
-   **HTTP POST** \- 新しいエンティティ データを指定されたリソースに挿入します。  挿入するデータは、要求メッセージのペイロードで指定されます。  応答メッセージのペイロードには、新しく作成されたエンティティのデータが含まれます。  これには自動生成されたキー値が含まれます。  ヘッダーには、新しいエンティティ リソースのアドレスを指定する URI も含まれます。  
  
-   **HTTP DELETE** \- 指定したリソースが表すエンティティ データを削除します。  ペイロードは要求メッセージおよび応答メッセージ内に存在しません。  
  
-   **HTTP PUT** \- 要求されたリソースの既存のエンティティ データを、要求メッセージのペイロードで指定された新しいデータで置き換えます。  
  
-   **HTTP MERGE** \- エンティティ データを変更するためだけに削除を実行した後にデータ ソースへの挿入を実行する非効率性を考慮して、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] では新しい HTTP MERGE アクションが導入されています。  要求メッセージのペイロードには、アドレス指定されたエンティティ リソースで変更する必要のあるプロパティが含まれます。  HTTP MERGE は HTTP 仕様で定義されていないので、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 対応のサーバー以外で HTTP MERGE 要求をルーティングするには追加の処理が必要になる場合があります。  
  
 詳細については、「[OData: 操作](http://go.microsoft.com/fwlink/?LinkId=185792)」を参照してください。  
  
### ペイロード形式  
 HTTP PUT、HTTP POST、または HTTP MERGE 要求の場合、要求メッセージのペイロードは、データ サービスに送信するエンティティ データを含んでいます。  ペイロードのコンテンツは、メッセージのデータ形式によって異なります。  そのようなペイロードは、DELETE 以外のすべてのアクションに対する HTTP 応答にも含まれます。  [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] は、サービスでのデータのアクセスおよび変更を行うために次のペイロード形式をサポートします。  
  
-   **Atom** \- Web フィード、ポッドキャスト、Wiki、および XML ベースのインターネット機能用に HTTP を介したデータ交換を有効にするために Atom 公開プロトコル \(AtomPub\) の拡張として [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] で定義されている XML ベースのメッセージ エンコーディング。  詳細については、「[OData: Atom 形式](http://go.microsoft.com/fwlink/?LinkId=185794)」を参照してください。  
  
-   **JSON** \- JSON \(JavaScript Object Notation\) は、JavaScript プログラミング言語のサブセットに基づく軽量のデータ交換形式です。  詳細については、「[OData: JSON 形式](http://go.microsoft.com/fwlink/?LinkId=185795)」を参照してください。  
  
 ペイロードのメッセージ形式は、HTTP 要求メッセージのヘッダーで要求されます。  詳細については、「[OData: 操作](http://go.microsoft.com/fwlink/?LinkID=185792)」を参照してください。  
  
## クライアント ライブラリを使用したデータのアクセスおよび変更  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] には、.NET Framework ベースのクライアント アプリケーションおよび Silverlight ベースのクライアント アプリケーションから [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを簡単に使用できるクライアント ライブラリが含まれています。  これらのライブラリは、HTTP メッセージの送受信を簡略化します。  また、メッセージ ペイロードをエンティティ データを表す CLR オブジェクトに変換します。  クライアント ライブラリには、<xref:System.Data.Services.Client.DataServiceContext> および <xref:System.Data.Services.Client.DataServiceQuery%601> という 2 つのコア クラスがあります。  これらのクラスを使用すると、データ サービスをクエリして、返されるエンティティ データを CLR オブジェクトとして処理できます。  詳細については、「[WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)」および「[WCF Data Services \(Silverlight\)](http://msdn.microsoft.com/ja-jp/c0cd9f4b-1372-48e4-9935-c8421239da30)」を参照してください。  
  
 Visual Studio の **\[サービス参照の追加\]** ダイアログを使用して、参照をデータ サービスに追加できます。  このツールは、参照されたデータ サービスからサービス メタデータを要求し、データ サービスを表す <xref:System.Data.Services.Client.DataServiceContext> を生成します。また、エンティティを表すクライアント データ サービス クラスも生成します。  詳細については、「[データ サービス クライアント ライブラリの生成](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)」を参照してください。  
  
 その他の種類のクライアント アプリケーションで [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを使用するためのプログラミング ライブラリを利用できます。  詳細については、「[OData SDK](http://go.microsoft.com/fwlink/?LinkId=185796)」を参照してください。  
  
## 参照  
 [データ サービス リソースへのアクセス](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)   
 [クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
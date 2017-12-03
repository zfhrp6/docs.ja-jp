---
title: "クライアント アプリケーションでのデータ サービスの使用 (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, getting started
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 79c4f7e066f4961caa66d3fd19dee9eb0f21ada4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="using-a-data-service-in-a-client-application-wcf-data-services"></a>クライアント アプリケーションでのデータ サービスの使用 (WCF Data Services)
公開するサービスにアクセスすることができます、 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Web ブラウザーに URI を指定することによってフィードします。 URI はリソースのアドレスを提供し、要求メッセージがこれらのアドレスに送信されてリソースが表す基になるデータのアクセスまたは変更を行います。 ブラウザーは HTTP GET コマンドを発行して、要求されたリソースを [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードとして返します。 詳細については、次を参照してください。 [Web ブラウザーからサービスにアクセスする](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)です。  
  
 Web ブラウザーは [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスが予期されたデータを返すかどうかをテストするために便利ですが、データの作成、更新、および削除も行うことができる運用 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスは、一般的にアプリケーション コードや Web ページのスクリプト言語を使用してアクセスします。 このトピックにアクセスする方法の概要を説明する[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]クライアント アプリケーションからフィードします。  
  
## <a name="accessing-and-changing-data-using-rest-semantics"></a>REST セマンティクスを使用したデータのアクセスおよび変更  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]公開するサービスの間の相互運用性を保証するのに役立ちます[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィードおよび使用するアプリケーション[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィードします。 アプリケーションへのアクセスし、データの変更、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]のベース URI、アクションの対象となるエンティティ リソースのアドレスを持つ特定の HTTP アクションの要求メッセージを送信することによってサービス。 エンティティ データを指定する必要がある場合、メッセージの本文に、エンコードされたペイロードとして明示的に指定します。  
  
### <a name="http-actions"></a>HTTP アクション  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] は、アドレス指定されたリソースが表すエンティティ データに対する操作の作成、読み取り、更新、および削除を実行する次の HTTP アクションをサポートします。  
  
-   **HTTP GET** -これは、ブラウザーからリソースにアクセスする場合の既定のアクション。 要求メッセージではペイロードは指定されず、要求されたデータを含むペイロードを含む応答メソッドが返されます。  
  
-   **HTTP POST** -指定されたリソースに新しいエンティティ データを挿入します。 挿入するデータは、要求メッセージのペイロードで指定されます。 応答メッセージのペイロードには、新しく作成されたエンティティのデータが含まれます。 これには自動生成されたキー値が含まれます。 ヘッダーには、新しいエンティティ リソースのアドレスを指定する URI も含まれます。  
  
-   **HTTP DELETE** -指定したリソースを表すエンティティ データを削除します。 ペイロードは要求メッセージおよび応答メッセージ内に存在しません。  
  
-   **HTTP PUT** - 既存のエンティティのデータを要求されたリソースを要求メッセージのペイロードで指定されている新しいデータで置き換えます。  
  
-   **HTTP MERGE** - エンティティ データを変更するだけのデータ ソースへの挿入後に削除を実行する非効率[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]新しい HTTP MERGE アクションが導入されています。 要求メッセージのペイロードには、アドレス指定されたエンティティ リソースで変更する必要のあるプロパティが含まれます。 HTTP MERGE は HTTP 仕様で定義されていないので、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 対応のサーバー以外で HTTP MERGE 要求をルーティングするには追加の処理が必要になる場合があります。  
  
 詳細については、次を参照してください。 [OData: 操作](http://go.microsoft.com/fwlink/?LinkId=185792)です。  
  
### <a name="payload-formats"></a>ペイロード形式  
 HTTP PUT、HTTP POST、または HTTP MERGE 要求の場合、要求メッセージのペイロードは、データ サービスに送信するエンティティ データを含んでいます。 ペイロードのコンテンツは、メッセージのデータ形式によって異なります。 そのようなペイロードは、DELETE 以外のすべてのアクションに対する HTTP 応答にも含まれます。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]アクセスして、サービスを使用してデータを変更するためには、次のペイロード形式をサポートします。  
  
-   **Atom** -によって定義されている XML ベースのメッセージ エンコーディング[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]Atom Publishing Protocol (AtomPub) の Web フィード、ポッド キャスト、wiki、HTTP 経由でデータ交換を有効にして XML ベースのインターネット機能を拡張として。 詳細については、次を参照してください。 [OData: Atom 形式](http://go.microsoft.com/fwlink/?LinkId=185794)です。  
  
-   **JSON** -JavaScript Object Notation (JSON) は、JavaScript のプログラミング言語のサブセットに基づく軽量のデータ交換形式です。 詳細については、次を参照してください。 [OData: JSON 形式](http://go.microsoft.com/fwlink/?LinkId=185795)です。  
  
 ペイロードのメッセージ形式は、HTTP 要求メッセージのヘッダーで要求されます。 詳細については、次を参照してください。 [OData: 操作](http://go.microsoft.com/fwlink/?LinkID=185792)です。  
  
## <a name="accessing-and-changing-data-using-client-libraries"></a>クライアント ライブラリを使用したデータのアクセスおよび変更  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]簡単に使用できるようにするクライアント ライブラリが含まれています、 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] .NET Framework および Silverlight ベースのクライアント アプリケーションからフィードします。 これらのライブラリは、HTTP メッセージの送受信を簡略化します。 また、メッセージ ペイロードをエンティティ データを表す CLR オブジェクトに変換します。 クライアント ライブラリには、 <xref:System.Data.Services.Client.DataServiceContext> および <xref:System.Data.Services.Client.DataServiceQuery%601>という 2 つのコア クラスがあります。 これらのクラスを使用すると、データ サービスをクエリして、返されるエンティティ データを CLR オブジェクトとして処理できます。 詳細については、次を参照してください。 [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)と[WCF Data Services (Silverlight)](http://msdn.microsoft.com/en-us/c0cd9f4b-1372-48e4-9935-c8421239da30)です。  
  
 使用することができます、**サービス参照の追加**データ サービスへの参照を追加する Visual Studio でのダイアログ。 このツールは、参照されたデータ サービスからサービス メタデータを要求し、データ サービスを表す <xref:System.Data.Services.Client.DataServiceContext> を生成します。また、エンティティを表すクライアント データ サービス クラスも生成します。 詳細については、次を参照してください。[データ サービス クライアント ライブラリを生成する](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)です。  
  
 プログラミング ライブラリを利用することができますを使用するが、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]他の種類のクライアント アプリケーションでのフィードです。 詳細については、次を参照してください。、 [OData SDK](http://go.microsoft.com/fwlink/?LinkId=185796)です。  
  
## <a name="see-also"></a>関連項目  
 [データ サービス リソースへのアクセス](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)  
 [クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

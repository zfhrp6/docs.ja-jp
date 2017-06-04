---
title: "WCF Data Services の概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "HTML"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "WCF Data Services"
  - "WCF Data Services, 説明"
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# WCF Data Services の概要
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] を使用して、Web またはイントラネット用のデータ サービスを作成し、それらを使用することができます。  [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] を使用すると、URI でアドレス指定できるリソースとしてデータを公開できます。  したがって、Representational State Transfer \(REST\) のセマンティクス \(標準的な HTTP 動詞 GET、PUT、POST、DELETE\) を使用してデータにアクセスし、そのデータを変更できます。このトピックでは、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] で定義されるパターンとプラクティスの両方の概要について説明します。また、.NET Framework ベースのアプリケーションで [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] を利用するために [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] で提供される機能についても説明します。  
  
## リソースとしてのデータのアドレス指定  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] は、URI でアドレス指定できるリソースとしてデータを公開します。リソース パスは、Entity Data Model のエンティティとリレーションシップの規則に基づいて構築されます。  このモデルでは、エンティティはアプリケーション ドメイン内のデータの操作単位を表します \(顧客、注文、項目、製品など\)。  詳細については、「[Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)」を参照してください。  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] では、エンティティ型のインスタンスを含むエンティティ セットとしてエンティティ リソースのアドレスを指定します。  たとえば、`http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders` という URI を指定すると、`Northwind` データ サービスにアクセスして、`CustomerID` 値が `ALFKI` である顧客のすべての注文を取得できます。  
  
 クエリ式を使用して、リソースに対して従来のクエリ操作 \(フィルターの適用、並べ替え、ページングなど\) を実行できます。  たとえば、`http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=Freight gt 50` という URI は、リソースをフィルターして、$50 以上の運賃の注文だけを返します。  詳細については、「[データ サービス リソースへのアクセス](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)」を参照してください。  
  
## 相互運用可能なデータ アクセス  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] では標準的なインターネット プロトコルに基づいてデータ サービスを作成するので、.NET Framework 対応でないアプリケーションとも相互運用が可能です。  標準的な URI を使用してデータのアドレスを指定できるので、アプリケーションは Representational State Transfer \(REST\) のセマンティクス \(特に GET、PUT、POST、および DELETE の HTTP 動詞\) を使用してデータにアクセスして変更できます。  そのため、標準的な HTTP プロトコルを介して転送されるデータの解析、およびこれらのデータへのアクセスを行うことができる任意のクライアントからこれらのサービスにアクセスできます。  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] は Atom 公開プロトコル \(AtomPub\) に対する一連の拡張を定義しています。さまざまなクライアント アプリケーションおよびプラットフォームに対応するために、複数のデータ形式による HTTP 要求と応答をサポートしています。  [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードは、Atom、JavaScript Object Notation \(JSON\)、および通常の XML でデータを表現できます。  Atom が既定の形式ですが、フィードの形式は HTTP 要求のヘッダーで指定されます。  詳細については、「[OData: Atom 形式](http://go.microsoft.com/fwlink/?LinkID=185794)」および「[OData: JSON 形式](http://go.microsoft.com/fwlink/?LinkID=185795)」を参照してください。  
  
 データを [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードとして公開する場合、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] はその他の既存のインターネット機能をキャッシュや認証などの操作で使用します。  これを可能にするために、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は ASP.NET、Windows Communication Foundation \(WCF\)、インターネット インフォメーション サービス \(IIS\) などの既存のホスト アプリケーションおよびサービスと統合されています。  
  
## ストレージの独立性  
 リソースはエンティティ リレーションシップ モデルに基づいてアドレス指定されますが、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は、基になるデータ ソースとは関係なく [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを公開します。URI で指定されたリソースへの HTTP 要求を [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] が受け取ると、その要求は逆シリアル化され、その要求の表現が [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] プロバイダーに渡されます。  このプロバイダーは、要求をデータ ソース固有の形式に変換し、基になるデータ ソースで要求を実行します。[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] で規定されるリソースをアドレス指定する概念モデルと、基になるデータ ソースのスキーマとを分離することによってストレージの独立性を実現します。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] と ADO.NET Entity Framework の組み合わせにより、リレーショナル データを公開するデータ サービスを作成できます。  Entity Data Model ツールを使用して、エンティティとしてアドレス指定可能なリソースを含むデータ モデルを作成すると同時に、このモデルと基になるデータベースのテーブルの間のマッピングを定義できます。  詳細については、「[Entity Framework プロバイダー](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)」を参照してください。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、<xref:System.Linq.IQueryable%601> インターフェイスの実装を返すデータ構造を公開するデータ サービスを作成することもできます。  そのため、.NET Framework 型からデータを公開するデータ サービスを作成できます。  <xref:System.Data.Services.IUpdatable> インターフェイスも実装すると、作成、更新、および削除操作がサポートされます。  詳細については、「[リフレクション プロバイダー](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)」を参照してください。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] をこれらのデータ プロバイダーと統合する方法については、このトピックの最後にあるアーキテクチャの図を参照してください。  
  
## カスタム ビジネス ロジック  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] を使用すると、サービス操作およびインターセプターを介してデータ サービスにカスタム ビジネス ロジックを簡単に追加できます。  サービス操作とは、データ リソースと同じ形態の URI によるアドレス指定が可能な、サーバーで定義されるメソッドです。  サービス操作では、クエリ式構文を使用して、操作によって返されるデータのフィルター、並べ替え、およびページングを行うこともできます。たとえば、`http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10` という URI は、ロンドン \(London\) の顧客の注文を Northwind データ サービスから返し、ページングされた結果を `OrderDate` で並べ替える `GetOrdersByCity` というサービス操作への呼び出しを表します。  詳細については、「[サービス操作](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)」を参照してください。  
  
 インターセプターを使用すると、カスタム アプリケーション ロジックをデータ サービスによる要求メッセージまたは応答メッセージの処理に統合できます。  インターセプターは、指定されたエンティティ セットに対してクエリ、挿入、更新、または削除の各操作が行われたときに呼び出されます。  インターセプターは、その後データの変更や承認ポリシーの強制を行うか、さらには操作を終了することもあります。  インターセプターのメソッドは、データ サービスによって公開される何らかのエンティティ セットに明示的に登録されている必要があります。  詳細については、「[インターセプター](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)」を参照してください。  
  
## クライアント ライブラリ  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] は、データ サービスと対話する統一パターンのセットを定義します。  その結果、これらのサービスに基づいて再使用可能なコンポーネントを作成できます \(データ サービスの使用を簡略化するクライアント側ライブラリなど\)。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] には、.NET Framework ベースのクライアント アプリケーションと Silverlight ベースのクライアント アプリケーションの両方のクライアント ライブラリが含まれます。  これらのクライアント ライブラリでは、.NET Framework オブジェクトを使用してデータ サービスと対話できます。  また、オブジェクト ベースのクエリと LINQ クエリ、関連オブジェクトの読み込み、変更の追跡、および ID 解決もサポートしています。詳細については、「[WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)」を参照してください。  
  
 .NET Framework および Silverlight に含まれる [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] クライアント ライブラリのほかに、PHP、AJAX、Java アプリケーションなどのクライアント アプリケーションで [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを使用できるようにするクライアント ライブラリがあります。  詳細については、「[OData SDK](http://go.microsoft.com/fwlink/?LinkID=185796)」を参照してください。  
  
## アーキテクチャの概要  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを公開し、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 対応クライアント ライブラリでこれらのフィードを使用するための [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] アーキテクチャを次の図に示します。  
  
 ![WCF Data Services アーキテクチャ ダイアグラム](../../../../docs/framework/data/wcf/media/astoriaservicearch.gif "AstoriaServiceArch")  
  
## 参照  
 [WCF Data Services 4.5](../../../../docs/framework/data/wcf/index.md)   
 [概要](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)   
 [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)   
 [Accessing a Data Service \(WCF Data Services\)](http://msdn.microsoft.com/ja-jp/1e54a2b9-2ec6-4002-b8f8-c1d8df37c350)   
 [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)   
 [Representational State Transfer \(REST\)](http://go.microsoft.com/fwlink/?LinkId=113919)
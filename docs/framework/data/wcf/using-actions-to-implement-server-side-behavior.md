---
title: "アクションを使用してサーバー側の動作を実装する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 11a372db-7168-498b-80d2-9419ff557ba5
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# アクションを使用してサーバー側の動作を実装する
OData アクションを使用すると、OData サービスから取得したリソースに対する動作を実装できます。  たとえば、リソースとしてデジタル ムービーについて考えてみましょう。デジタル ムービーについては、チェックアウト、評価やコメント、チェックインなど、多様な操作が考えられます。  これらはすべて、デジタル ムービーを管理するために WCF Data Services で実装できるアクションの例です。  アクションは、そのアクションを呼び出すことのできる対象のリソースが含まれている OData 応答に記述します。  ユーザーが、デジタル ムービーを表すリソースを要求した場合、WCF Data Services から返される応答には、そのリソースに使用できるアクションに関する情報が含まれています。  アクションを使用できるかどうかは、データ サービスまたはリソースの状態によって変わる場合があります。  たとえば、デジタル ムービーがチェックアウトされている場合、それを別のユーザーがチェックアウトすることはできません。  クライアントは、URL を指定するだけでアクションを呼び出すことができます。  たとえば、「http:\/\/MyServer\/MovieService.svc\/Movies\(6\)」と指定すると特定のデジタル ムービーが示され、「http:\/\/MyServer\/MovieService.svc\/Movies\(6\)\/Checkout」と指定すると特定のムービーに対するアクションが呼び出されます。  アクションを使用すると、データ モデルを公開することなくサービス モデルを公開することができます。  先ほどのムービー サービスを例とすると、評価データをリソースとして直接公開せずにムービーをユーザーが評価できるようにするというケースが考えられます。  そこで、たとえば Rate \(評価\) アクションを実装することにより、リソースとして評価データに直接アクセスせずに、ムービーをユーザーが評価できるようにすることができます。  
  
 WCF Data Services アクションの実装の完全な例については、[「Entity Framework 用 WCF Data Services アクション プロバイダー](http://efactionprovider.codeplex.com/)」を参照してください。  
  
## アクションの実装  
 サービス アクションを実装するには、<xref:System.IServiceProvider> インターフェイス、<xref:System.Data.Services.Providers.IDataServiceActionProvider> インターフェイス、および <xref:System.Data.Services.Providers.IDataServiceInvokable> インターフェイスを実装する必要があります。  <xref:System.IServiceProvider> を使用すると WCF Data Services は、<xref:System.Data.Services.Providers.IDataServiceActionProvider> の実装を取得できます。  <xref:System.Data.Services.Providers.IDataServiceActionProvider> を使用すると WCF Data Services は、サービス アクションの作成、検出、記述、および呼び出しを行うことができます。  <xref:System.Data.Services.Providers.IDataServiceInvokable> を使用すると、サービス アクションの動作を実装して結果 \(ある場合\) を取得するコードを呼び出すことができます。  WCF Data Services は呼び出しごとの WCF サービスであり、サービスの新しいインスタンスは、サービスが呼び出されるごとに作成されます。  サービスの作成時に、不要な作業が行われないよう注意してください。  
  
### IServiceProvider  
 <xref:System.IServiceProvider> には、<xref:System.IServiceProvider.GetService%2A> というメソッドが含まれています。  このメソッドは、メタデータ サービス プロバイダーやデータ サービス アクション プロバイダーなど、いくつかのサービス プロバイダーを取得するために、WCF Data Services によって呼び出されます。  データ サービス アクション プロバイダーを求められた場合は、<xref:System.Data.Services.Providers.IDataServiceActionProvider> 実装を返します。  
  
### IDataServiceActionProvider  
 <xref:System.Data.Services.Providers.IDataServiceActionProvider> には、使用可能なアクションに関する情報を取得するためのメソッドが含まれています。  <xref:System.Data.Services.Providers.IDataServiceActionProvider> を実装すると、サービスの <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> 実装で定義されるサービスのメタデータにアクションが追加され、必要に応じてアクションへのディスパッチが処理されます。  
  
#### AdvertiseServiceAction  
 <xref:System.Data.Services.Providers.IDataServiceActionProvider.AdvertiseServiceAction%2A> は、指定されたリソースに対して使用できるアクションを判断するために呼び出されます。  このメソッドは、常時使用可能ではないアクションについてのみ呼び出されます。  このメソッドの用途は、要求されているリソースの状態またはサービスの状態に基づいて、アクションを OData 応答に含めるかどうかを確認することです。  この確認をどのように行うかは、開発者が指定する必要があります。  使用可能かどうかを計算する処理の負荷が高く、現在のリソースがフィード内にある場合は、確認をスキップしてアクションの情報提供を行うこともできます。  返される現在のリソースがフィードの一部である場合は、`inFeed` パラメーターが `true` に設定されます。  
  
#### CreateInvokable  
 [M:System.Data.Services.Providers.IDataServiceActionProvider.CreateInvokable\(System.Data.Services.DataServiceOperationContext,System.Data.Services.Providers.ServiceAction,System.Object\<xref:System.Data.Services.Providers.IDataServiceActionProvider.CreateInvokable%2A> は、アクションの動作が実装されたコードをカプセル化するデリゲートが含まれた <xref:System.Data.Services.Providers.IDataServiceInvokable> を作成する場合に呼び出します。  これにより <xref:System.Data.Services.Providers.IDataServiceInvokable> インスタンスが作成されますが、アクションの呼び出しは行われません。  WCF Data Services のアクションは副作用を伴うため、更新プロバイダーと連携して、その変更をディスクに保存する必要があります。  <xref:System.Data.Services.Providers.IDataServiceInvokable.Invoke%2A> メソッドは、更新プロバイダーの SaveChanges\(\) メソッドが呼び出された後に呼び出されます。  
  
#### GetServiceActions  
 このメソッドは、WCF Data Services が公開するすべてのアクションを表す <xref:System.Data.Services.Providers.ServiceAction> インスタンスのコレクションを返します。  <xref:System.Data.Services.Providers.ServiceAction> は、アクションのメタデータ表現であり、アクションの名前、パラメーター、戻り値の型などの情報を含んでいます。  
  
#### GetServiceActionsByBindingParameterType  
 このメソッドは、指定されたバインディング パラメーターの種類にバインドできるすべての <xref:System.Data.Services.Providers.ServiceAction> インスタンスのコレクションを返します。  つまり、指定されたリソースの種類 \(バインディング パラメーターの種類\) を操作できるすべての <xref:System.Data.Services.Providers.ServiceAction> を表します。サービスがリソースを返すときに、そのリソースに対して呼び出すことのできるアクションの情報を含めるために使用します。  このメソッドが返すアクションは、\(派生型ではなく\) 指定どおりのバインディング パラメーターの種類にバインドできるアクションのみです。  このメソッドは、要求ごと、検出された種類ごとに 1 回呼び出され、結果は WCF Data Services によってキャッシュされます。  
  
#### TryResolveServiceAction  
 このメソッドは、指定された <xref:System.Data.Services.Providers.ServiceAction> を検索し、<xref:System.Data.Services.Providers.ServiceAction> が見つかった場合は `true` を返します。  見つかった場合、`out` パラメーター `serviceAction` で <xref:System.Data.Services.Providers.ServiceAction> が返されます。  
  
### IDataServiceInvokable  
 このインターフェイスは、WCF Data Services アクションの実行方法を提供します。  IDataServiceInvokable を実装する場合は、次の 3 つを行う必要があります。  
  
1.  パラメーターをキャプチャし、場合によってはマーシャリングを行う。  
  
2.  Invoke\(\) の呼び出し時に、アクションを実際に実装するコードにパラメーターをディスパッチする。  
  
3.  GetResult\(\) を使用して取得できるように、Invoke\(\) の結果を保存する。  
  
 パラメーターは、トークンとして渡すことができます。  これは、リソースを表すトークンを扱うデータ サービス プロバイダーを作成することができるためです。ただしその場合は、実際のアクションにディスパッチする前に、トークンを実際のリソースに変換 \(マーシャリング\) する必要があります。  アクションが呼び出されたときに発生したリソースへの変更を保存してディスクに書き込むことができるよう、マーシャリングを行ったパラメーターは編集可能な状態にしておく必要があります。  
  
 このインターフェイスには、Invoke および GetResult という 2 つのメソッドが必要です。  Invoke はアクションの動作を実装するデリゲートを呼び出し、GetResult はアクションの結果を返します。  
  
## WCF Data Services アクションの呼び出し  
 アクションは HTTP POST 要求を使用して呼び出します。  リソースの後にアクション名を続けて URL を指定します。  パラメーターは、要求の本文を使用して渡します。  たとえば、MovieService というサービスがあり、Rate というアクションが公開されているとします。  この場合、特定のムービーに対して Rate アクションを呼び出すには、次のような URL 使用することができます。  
  
 http:\/\/MovieServer\/MovieService.svc\/Movies\(1\)\/Rate  
  
 Movies\(1\) は評価対象のムービーを示し、Rate は Rate アクションを指定しています。  次の例に示すように、評価の実際の値は HTTP 要求の本文に含まれます。  
  
```  
POST http://MovieServer/MoviesService.svc/Movies(1)/Rate HTTP/1.1   
Content-Type: application/json   
Content-Length: 20   
Host: localhost:15238  
{   
   "rating": 4   
}  
  
```  
  
> [!WARNING]
>  上のサンプル コードが動作するのは、JSON Light をサポートする WCF Data Services 5.2 以降を使用している場合のみです。  それより前のバージョンの WCF Data Services を使用している場合は、Verbose JSON の Content\-Type を「`application/json;odata=verbose`」のように指定する必要があります。  
  
 また、次のコード スニペットのように、WCF Data Services クライアントを使用してアクションを呼び出すこともできます。  
  
```  
MoviesModel context = new MoviesModel (new Uri("http://MyServer/MoviesService.svc/"));  
            //...  
            context.Execute(new Uri("http://MyServer/MoviesService.svc/Movies(1)/Rate"), "POST", new BodyOperationParameter("rating",4) );           
```  
  
 上のコード スニペットの `MoviesModel` クラスは、Visual Studio の \[サービス参照の追加\] で WCF Data Services への参照を追加することでが生成されたものです。  
  
## 参照  
 [WCF Data Services 4.5](../../../../docs/framework/data/wcf/index.md)   
 [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)   
 [WCF Data Services の開発と配置](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)   
 [カスタム データ サービス プロバイダー](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)
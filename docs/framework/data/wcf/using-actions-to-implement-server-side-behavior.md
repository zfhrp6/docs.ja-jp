---
title: アクションを使用してサーバー側の動作を実装する
ms.date: 03/30/2017
ms.assetid: 11a372db-7168-498b-80d2-9419ff557ba5
ms.openlocfilehash: d4be2aa42c667460232f6aa3cd8dc707805750e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365242"
---
# <a name="using-actions-to-implement-server-side-behavior"></a>アクションを使用してサーバー側の動作を実装する
OData アクションを使用すると、OData サービスから取得したリソースに対する動作を実装できます。  たとえば、リソースとしてデジタル ムービーについて考えてみましょう。デジタル ムービーについては、チェックアウト、評価やコメント、チェックインなど、多様な操作が考えられます。 これらはすべて、デジタル ムービーを管理するために WCF Data Services で実装できるアクションの例です。 アクションは、そのアクションを呼び出すことのできる対象のリソースが含まれている OData 応答に記述します。 ユーザーが、デジタル ムービーを表すリソースを要求した場合、WCF Data Services から返される応答には、そのリソースに使用できるアクションに関する情報が含まれています。 アクションを使用できるかどうかは、データ サービスまたはリソースの状態によって変わる場合があります。 たとえば、デジタル ムービーがチェックアウトされている場合、それを別のユーザーがチェックアウトすることはできません。 クライアントは、URL を指定するだけでアクションを呼び出すことができます。 たとえばhttp://MyServer/MovieService.svc/Movies(6)特定のデジタル ムービーとhttp://MyServer/MovieService.svc/Movies(6)/Checkout特定のムービーに対するアクションを呼び出します。 アクションを使用すると、データ モデルを公開することなくサービス モデルを公開することができます。 先ほどのムービー サービスを例とすると、評価データをリソースとして直接公開せずにムービーをユーザーが評価できるようにするというケースが考えられます。 そこで、たとえば Rate (評価) アクションを実装することにより、リソースとして評価データに直接アクセスせずに、ムービーをユーザーが評価できるようにすることができます。  
  
## <a name="implementing-an-action"></a>アクションの実装  
 実装する必要がありますサービス アクションを実装する、 <xref:System.IServiceProvider>、 [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx)、および[IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx)インターフェイスです。 <xref:System.IServiceProvider> により、WCF データ サービスの実装を取得する[IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx)です。 [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) WCF データ サービスを作成するが検索、について説明し、サービスのアクションを起動します。 [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx)存在する場合に使用すると、サービス操作の動作を実装するコードを呼び出すし、結果を取得します。 WCF Data Services は呼び出しごとの WCF サービスであり、サービスの新しいインスタンスは、サービスが呼び出されるごとに作成されます。  サービスの作成時に、不要な作業が行われないよう注意してください。  
  
### <a name="iserviceprovider"></a>IServiceProvider  
 <xref:System.IServiceProvider> には、<xref:System.IServiceProvider.GetService%2A> というメソッドが含まれています。 このメソッドは、メタデータ サービス プロバイダーやデータ サービス アクション プロバイダーなど、いくつかのサービス プロバイダーを取得するために、WCF Data Services によって呼び出されます。 データ サービス アクション プロバイダーを求められたら、返す、 [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx)実装します。  
  
### <a name="idataserviceactionprovider"></a>IDataServiceActionProvider  
 [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx)使用可能なアクションに関する情報を取得できるようにするメソッドが含まれています。 実装に[IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx)のサービスの実装によって定義されているサービスのメタデータを増強する[IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx)アクションがあると必要に応じてアクションへのディスパッチを処理しています。  
  
#### <a name="advertiseserviceaction"></a>AdvertiseServiceAction  
 [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider.advertiseserviceaction(v=vs.113).aspx)はどのような操作は、指定されたリソースの利用を決定する呼び出されます。 このメソッドは、常時使用可能ではないアクションについてのみ呼び出されます。 このメソッドの用途は、要求されているリソースの状態またはサービスの状態に基づいて、アクションを OData 応答に含めるかどうかを確認することです。 この確認をどのように行うかは、開発者が指定する必要があります。 使用可能かどうかを計算する処理の負荷が高く、現在のリソースがフィード内にある場合は、確認をスキップしてアクションの情報提供を行うこともできます。 返される現在のリソースがフィードの一部である場合は、`inFeed` パラメーターが `true` に設定されます。  
  
#### <a name="createinvokable"></a>CreateInvokable  
 [CreateInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider.createinvokable(v=vs.113).aspx)作成するために呼び出される、 [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx)アクションの動作を実装するコードをカプセル化するデリゲートを格納しています。 これを作成、 [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx)のインスタンスが動作を引き起こすことはありません。 WCF Data Services のアクションは副作用を伴うため、更新プロバイダーと連携して、その変更をディスクに保存する必要があります。 [IDataServiceInvokable.Invoke](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable.invoke(v=vs.113).aspx)から、更新プロバイダーの SaveChanges() メソッドが呼び出されたメソッドが呼び出されます。  
  
#### <a name="getserviceactions"></a>GetServiceActions  
 このメソッドのコレクションを返します[ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx)のすべての WCF データ サービスは、公開操作を表すインスタンス。 [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx)アクション名、パラメーター、戻り値の型などの情報を含むアクションのメタデータ表現です。  
  
#### <a name="getserviceactionsbybindingparametertype"></a>GetServiceActionsByBindingParameterType  
 このメソッドは、すべてのコレクションを返します[ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx)インスタンスを指定したバインディング パラメーターの型にバインドできます。 つまり、すべて[ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx)s (バインディング パラメーターの種類とも呼ばれます) 指定されたリソースの種類に対応できます。これは、サービスでは、そのリソースに対して呼び出すことのできるアクションに関する情報を含めるために、リソースが返されるときに使用されます。 このメソッドが返すアクションは、(派生型ではなく) 指定どおりのバインディング パラメーターの種類にバインドできるアクションのみです。 このメソッドは、要求ごと、検出された種類ごとに 1 回呼び出され、結果は WCF Data Services によってキャッシュされます。  
  
#### <a name="tryresolveserviceaction"></a>TryResolveServiceAction  
 このメソッドは、指定した検索[ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx)し、返します`true`場合、 [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx)が見つかった。 場合、 [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx)で返される、`serviceAction``out`パラメーター。  
  
### <a name="idataserviceinvokable"></a>IDataServiceInvokable  
 このインターフェイスは、WCF Data Services アクションの実行方法を提供します。 IDataServiceInvokable を実装する場合は、次の 3 つを行う必要があります。  
  
1.  パラメーターをキャプチャし、場合によってはマーシャリングを行う。  
  
2.  Invoke() の呼び出し時に、アクションを実際に実装するコードにパラメーターをディスパッチする。  
  
3.  GetResult() を使用して取得できるように、Invoke() の結果を保存する。  
  
 パラメーターは、トークンとして渡すことができます。 これは、リソースを表すトークンを扱うデータ サービス プロバイダーを作成することができるためです。ただしその場合は、実際のアクションにディスパッチする前に、トークンを実際のリソースに変換 (マーシャリング) する必要があります。 アクションが呼び出されたときに発生したリソースへの変更を保存してディスクに書き込むことができるよう、マーシャリングを行ったパラメーターは編集可能な状態にしておく必要があります。  
  
 このインターフェイスには、Invoke および GetResult という 2 つのメソッドが必要です。 Invoke はアクションの動作を実装するデリゲートを呼び出し、GetResult はアクションの結果を返します。  
  
## <a name="invoking-a-wcf-data-service-action"></a>WCF Data Services アクションの呼び出し  
 アクションは HTTP POST 要求を使用して呼び出します。 リソースの後にアクション名を続けて URL を指定します。 パラメーターは、要求の本文を使用して渡します。 たとえば、MovieService というサービスがあり、Rate というアクションが公開されているとします。 この場合、特定のムービーに対して Rate アクションを呼び出すには、次のような URL 使用することができます。  
  
 http://MovieServer/MovieService.svc/Movies(1)/Rate  
  
 Movies(1) は評価対象のムービーを示し、Rate は Rate アクションを指定しています。 次の例に示すように、評価の実際の値は HTTP 要求の本文に含まれます。  
  
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
>  上のサンプル コードが動作するのは、JSON Light をサポートする WCF Data Services 5.2 以降を使用している場合のみです。 それより前のバージョンの WCF Data Services を使用している場合は、Verbose JSON の Content-Type を「`application/json;odata=verbose`」のように指定する必要があります。  
  
 また、次のコード スニペットのように、WCF Data Services クライアントを使用してアクションを呼び出すこともできます。  
  
```  
MoviesModel context = new MoviesModel (new Uri("http://MyServer/MoviesService.svc/"));  
            //...  
            context.Execute(new Uri("http://MyServer/MoviesService.svc/Movies(1)/Rate"), "POST", new BodyOperationParameter("rating",4) );           
```  
  
 上のコード スニペットの `MoviesModel` クラスは、Visual Studio の [サービス参照の追加] で WCF Data Services への参照を追加することでが生成されたものです。  
  
## <a name="see-also"></a>関連項目  
 [WCF Data Services 4.5](../../../../docs/framework/data/wcf/index.md)  
 [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [WCF Data Services の開発と配置](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)  
 [カスタム データ サービス プロバイダー](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)

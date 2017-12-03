---
title: "カスタム有効期間"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2538a9c483b949dfef1c60bd2225f5daf4e01117
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="custom-lifetime"></a>カスタム有効期間
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] の共有サービス インスタンスにカスタムの有効期間サービスを提供する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 拡張機能の作成方法を示します。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
## <a name="shared-instancing"></a>共有インスタンス化  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、サービス インスタンス用にいくつかのインスタンス化モードが用意されています。 このトピックで説明する共有インスタンス化モードでは、サービス インスタンスを複数のチャネルで共有できます。 クライアントは、インスタンスのエンドポイント アドレスをローカルで解決するか、サービスのファクトリ メソッドと通信して実行中のインスタンスのエンドポイント アドレスを取得することができます。 エンドポイント アドレスを取得したら、新しいチャネルを作成して通信を開始することができます。 次のコード例は、クライアント アプリケーションが既存のサービス インスタンスへの新しいチャネルを作成する方法を示しています。  
  
```  
// Create the first channel.  
IEchoService proxy = channelFactory.CreateChannel();  
  
// Resolve the instance.  
EndpointAddress epa = ((IClientChannel)proxy).ResolveInstance();  
  
// Create new channel factory with the endpoint address resolved by   
// previous statement.  
ChannelFactory<IEchoService> channelFactory2 =  
                new ChannelFactory<IEchoService>("echoservice",  
                epa);  
  
// Create the second channel to the same instance.  
IEchoService proxy2 = channelFactory2.CreateChannel();  
```  
  
 他のインスタンス化モードとは異なり、共有インスタンス化モードでは、独特の方法でサービス インスタンスを解放します。 インスタンスのすべてのチャネルが閉じると、サービスの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ランタイムによってタイマーが開始されます。 タイムアウトになるまでに誰も接続しなかった場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] はインスタンスを解放してリソースを要求します。 切り離し手順の一環として、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、インスタンスを解放する前にすべての <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 実装の <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> メソッドを呼び出します。 そのすべてが `true` を返す場合は、インスタンスが解放されます。 それ以外の場合、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 実装は、コールバック メソッドを使用してアイドル状態であることを`Dispatcher`に通知します。  
  
 既定では、<xref:System.ServiceModel.InstanceContext> のアイドル タイムアウト値は 1 分です。 ただし、このサンプルでは、カスタム拡張機能を使用してこれを延長する方法を示します。  
  
## <a name="extending-the-instancecontext"></a>InstanceContext の拡張  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の <xref:System.ServiceModel.InstanceContext> は、サービス インスタンスと`Dispatcher`の間のリンクです。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、拡張可能オブジェクト パターンを使用して新しい状態または動作を追加することで、このランタイム コンポーネントを拡張できます。 拡張可能オブジェクト パターンは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、既存のランタイム クラスに新しい機能を付け加えて拡張するため、またはオブジェクトに新しい状態の機能を追加するために使用されます。 拡張可能オブジェクト パターンには、`IExtensibleObject<T>`、`IExtension<T>`、および `IExtensionCollection<T>` の 3 つのインターフェイスがあります。  
  
 `IExtensibleObject<T>` インターフェイスは、機能をカスタマイズするための拡張が可能なオブジェクトによって実装されます。  
  
 `IExtension<T>` インターフェイスは、`T` 型のクラスの拡張が可能なオブジェクトによって実装されます。  
  
 最後に、`IExtensionCollection<T>` インターフェイスは `IExtensions` のコレクションで、型ごとに `IExtensions` を取得できます。  
  
 したがって、<xref:System.ServiceModel.InstanceContext> を拡張するには、`IExtension` インターフェイスを実装する必要があります。 このサンプル プロジェクトでは、`CustomLeaseExtension` クラスにこの実装が含まれています。  
  
```  
class CustomLeaseExtension : IExtension<InstanceContext>  
{  
}  
```  
  
 `IExtension` インターフェイスには、`Attach` と `Detach` の 2 つのメソッドが含まれています。 名前が示すように、これらの 2 つのメソッドは、ランタイムが <xref:System.ServiceModel.InstanceContext> クラスのインスタンスに拡張機能を関連付けるときと関連付けを解除するときに呼び出されます。 このサンプルでは、`Attach` メソッドを使用して、拡張機能の現在のインスタンスに属する <xref:System.ServiceModel.InstanceContext> オブジェクトを追跡します。  
  
```  
InstanceContext owner;  
  
public void Attach(InstanceContext owner)  
{  
  this.owner = owner;   
}  
```  
  
 また、有効期間の延長をサポートするには、必要な実装を拡張機能に追加する必要があります。 したがって、`ICustomLease` インターフェイスを目的のメソッドで宣言し、`CustomLeaseExtension` クラスに実装します。  
  
```  
interface ICustomLease  
{  
    bool IsIdle { get; }          
    InstanceContextIdleCallback Callback { get; set; }  
}  
  
class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease  
{  
}  
```  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 実装で <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> メソッドを呼び出すと、この呼び出しは <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> の `CustomLeaseExtension` メソッドにルーティングされます。 次に、`CustomLeaseExtension` はそのプライベート状態をチェックし、<xref:System.ServiceModel.InstanceContext> がアイドル状態かどうかを確認します。 アイドル状態の場合は、`true` を返します。 それ以外の場合は、延長された指定の有効期間のタイマーが開始されます。  
  
```  
public bool IsIdle  
{  
  get  
  {  
    lock (thisLock)  
    {  
      if (isIdle)  
      {  
        return true;  
      }  
      else  
      {  
        StartTimer();  
        return false;  
      }  
    }  
  }  
}  
```  
  
 タイマーの `Elapsed` イベントで、別のクリーンアップ サイクルを開始するためにディスパッチャーのコールバック関数が呼び出されます。  
  
```  
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)  
{  
    idleTimer.Stop();  
    isIdle = true;    
    callback(owner);  
}  
```  
  
 アイドル状態に移行中のインスタンスに新しいメッセージが届いたときに、実行中のタイマーを更新する方法はありません。  
  
 このサンプルでは、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> メソッドの呼び出しを受け取って <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> にルーティングするために `CustomLeaseExtension` を実装します。 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 実装は、`CustomLifetimeLease` クラスに含まれています。 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> メソッドは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] がサービス インスタンスを解放するときに呼び出されます。 ただし、ServiceBehavior の `ISharedSessionInstance` コレクションに存在する特定の <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 実装のインスタンスは 1 つだけです。 つまり、<xref:System.ServiceModel.InstanceContext> が [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] メソッドをチェックする時点で閉じられている <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> を知る方法はありません。 したがって、このサンプルでは、スレッド ロックを使用して <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> メソッドへの要求をシリアル化します。  
  
> [!IMPORTANT]
>  シリアル化はアプリケーションのパフォーマンスに大きな影響を及ぼす可能性があるので、スレッド ロックは使用しないことをお勧めします。  
  
 `CustomLeaseExtension` クラスでプライベート メンバー変数を使用して、`IsIdle` の値を追跡します。 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> の値が取得されるたびに、`IsIdle` プライベート メンバーが返されて `false` にリセットされます。 ディスパッチャーが `false` メソッドを呼び出すようにするには、この値を <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> に設定する必要があります。  
  
```  
public bool IsIdle  
{  
    get   
    {  
       lock (thisLock)  
       {  
           bool idleCopy = isIdle;  
           isIdle = false;  
           return idleCopy;  
       }  
    }  
}  
```  
  
 `ISharedSessionLifetime.IsIdle` プロパティが `false` を返す場合、ディスパッチャーは `NotifyIdle` メソッドを使用してコールバック関数を登録します。 このメソッドは、解放される <xref:System.ServiceModel.InstanceContext> への参照を受け取ります。 したがって、このサンプル コードでは、`ICustomLease` 型拡張に対してクエリを実行し、拡張状態の `ICustomLease.IsIdle` プロパティをチェックすることができます。  
  
```  
public void NotifyIdle(InstanceContextIdleCallback callback,   
            InstanceContext instanceContext)  
{  
    lock (thisLock)  
    {  
       ICustomLease customLease =  
           instanceContext.Extensions.Find<ICustomLease>();  
       customLease.Callback = callback;   
       isIdle = customLease.IsIdle;  
       if (isIdle)  
       {  
             callback(instanceContext);  
       }  
    }   
}  
```  
  
 `ICustomLease.IsIdle` プロパティをチェックする前に、Callback プロパティを設定する必要があります。これは、アイドル状態になったときに `CustomLeaseExtension` がディスパッチャーに通知するために不可欠です。 `ICustomLease.IsIdle` が `true` を返す場合は、`isIdle` プライベート メンバーが `CustomLifetimeLease` で単に `true` に設定され、コールバック メソッドが呼び出されます。 このコードではロックが使用されているので、他のスレッドではこのプライベート メンバーの値を変更できません。 次にディスパッチャーが `ISharedSessionLifetime.IsIdle` をチェックするときに `true` が返されて、ディスパッチャーがインスタンスを解放できるようになります。  
  
 これでカスタム拡張機能の基礎が完成したので、この拡張機能をサービス モデルにフックする必要があります。 `CustomLeaseExtension` 実装を <xref:System.ServiceModel.InstanceContext> にフックするために、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、<xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> のブートストラップを実行する <xref:System.ServiceModel.InstanceContext> インターフェイスが用意されています。 このサンプルでは、`CustomLeaseInitializer` クラスでこのインターフェイスを実装し、`CustomLeaseExtension` のインスタンスを唯一のメソッドの初期化から得られる <xref:System.ServiceModel.InstanceContext.Extensions%2A> コレクションに追加します。 このメソッドは、<xref:System.ServiceModel.InstanceContext> の初期化中にディスパッチャーによって呼び出されます。  
  
```  
public void Initialize(InstanceContext instanceContext, Message message)  
{  
  IExtension<InstanceContext> customLeaseExtension =  
    new CustomLeaseExtension(timeout);  
  instanceContext.Extensions.Add(customLeaseExtension);  
}  
```  
  
 最後に、`System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime`と<xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer>は実装が、サービス モデルを使用して最大フック、<xref:System.ServiceModel.Description.IServiceBehavior>実装します。 この実装は、`CustomLeaseTimeAttribute` クラスに配置されています。また、`Attribute` 基本クラスから派生してこの動作を属性として公開します。 `IServiceBehavior.ApplyBehavior` メソッドで、<xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> 実装と `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` 実装のインスタンスがそれぞれ `System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextLifetimes` の <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> コレクションと <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> コレクションに追加されます。  
  
```  
public void ApplyBehavior(ServiceDescription description,   
           ServiceHostBase serviceHostBase,   
           Collection<DispatchBehavior> behaviors,  
           Collection<BindingParameterCollection> parameters)  
{  
    CustomLifetimeLease customLease = new CustomLifetimeLease();  
    CustomLeaseInitializer initializer =   
                new CustomLeaseInitializer(timeout);  
  
    foreach (DispatchBehavior dispatchBehavior in behaviors)  
    {  
        dispatchBehavior.InstanceContextLifetimes.Add(customLease);  
        dispatchBehavior.InstanceContextInitializers.Add(initializer);  
    }  
}  
```  
  
 この動作は、`CustomLeaseTime` 属性を使用して注釈を付けることにより、サンプル サービス クラスに追加できます。  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Shareable)]  
[CustomLeaseTime(Timeout = 20000)]  
public class EchoService : IEchoService  
{  
  //…  
}  
```  
  
 このサンプルを実行すると、操作要求と応答がサービスとクライアントの両方のコンソール ウィンドウに表示されます。 どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
2.  ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`  
  
## <a name="see-also"></a>関連項目

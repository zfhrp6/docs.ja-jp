---
title: カスタム有効期間
ms.date: 03/30/2017
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: e41c970739b8036730fa601433ce7157e01d7e19
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="custom-lifetime"></a>カスタム有効期間
このサンプルでは、WCF サービスの共有インスタンス用のカスタムの有効期間サービスを提供する Windows Communication Foundation (WCF) 拡張機能を記述する方法を示します。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
## <a name="shared-instancing"></a>共有インスタンス化  
 WCF には、サービス インスタンス用の複数のインスタンス化モードが用意されています。 このトピックで説明する共有インスタンス化モードでは、サービス インスタンスを複数のチャネルで共有できます。 クライアントは、インスタンスのエンドポイント アドレスをローカルで解決するか、サービスのファクトリ メソッドと通信して実行中のインスタンスのエンドポイント アドレスを取得することができます。 エンドポイント アドレスを取得したら、新しいチャネルを作成して通信を開始することができます。 次のコード例は、クライアント アプリケーションが既存のサービス インスタンスへの新しいチャネルを作成する方法を示しています。  
  
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
  
 他のインスタンス化モードとは異なり、共有インスタンス化モードでは、独特の方法でサービス インスタンスを解放します。 インスタンスは、すべてのチャネルが閉じられると、サービスの WCF ランタイムはタイマーを開始します。 誰も接続タイムアウトの有効期限が切れる前に場合、WCF は、インスタンスを解放し、リソースを要求します。 WCF を呼び出す切り離し手順の一部として、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>すべてのメソッド<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>インスタンスを解放する前に実装します。 そのすべてが `true` を返す場合は、インスタンスが解放されます。 それ以外の場合、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 実装は、コールバック メソッドを使用してアイドル状態であることを`Dispatcher`に通知します。  
  
 既定では、<xref:System.ServiceModel.InstanceContext> のアイドル タイムアウト値は 1 分です。 ただし、このサンプルでは、カスタム拡張機能を使用してこれを延長する方法を示します。  
  
## <a name="extending-the-instancecontext"></a>InstanceContext の拡張  
 WCF では、<xref:System.ServiceModel.InstanceContext>サービス インスタンスの間のリンクは、および`Dispatcher`です。 WCF では、その拡張可能オブジェクト パターンを使用して新しい状態または動作を追加することによってこのランタイム コンポーネントを拡張することができます。 拡張可能オブジェクト パターンは WCF で使用されるか、新しい機能を持つ既存のランタイム クラスを拡張するか、オブジェクトに新しい状態の機能を追加します。 拡張可能オブジェクト パターンには、`IExtensibleObject<T>`、`IExtension<T>`、および `IExtensionCollection<T>` の 3 つのインターフェイスがあります。  
  
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
  
 WCF が呼び出す場合、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>メソッドで、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>にこの呼び出しをルーティングの実装、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>のメソッド、`CustomLeaseExtension`です。 次に、`CustomLeaseExtension` はそのプライベート状態をチェックし、<xref:System.ServiceModel.InstanceContext> がアイドル状態かどうかを確認します。 アイドル状態の場合は、`true` を返します。 それ以外の場合は、延長された指定の有効期間のタイマーが開始されます。  
  
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
  
 このサンプルでは、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> メソッドの呼び出しを受け取って <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> にルーティングするために `CustomLeaseExtension` を実装します。 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 実装は、`CustomLifetimeLease` クラスに含まれています。 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> WCF がサービス インスタンスを解放しようとしてがの場合、メソッドが呼び出されます。 ただし、ServiceBehavior の `ISharedSessionInstance` コレクションに存在する特定の <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 実装のインスタンスは 1 つだけです。 つまり、知る方法はありません、 <xref:System.ServiceModel.InstanceContext> WCF チェック時に閉じられる、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>メソッドです。 したがって、このサンプルでは、スレッド ロックを使用して <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> メソッドへの要求をシリアル化します。  
  
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
  
 これでカスタム拡張機能の基礎が完成したので、この拡張機能をサービス モデルにフックする必要があります。 フックするために、`CustomLeaseExtension`を実装、 <xref:System.ServiceModel.InstanceContext>、WCF の提供、<xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer>のブートス トラップを実行するインターフェイス<xref:System.ServiceModel.InstanceContext>です。 このサンプルでは、`CustomLeaseInitializer` クラスでこのインターフェイスを実装し、`CustomLeaseExtension` のインスタンスを唯一のメソッドの初期化から得られる <xref:System.ServiceModel.InstanceContext.Extensions%2A> コレクションに追加します。 このメソッドは、<xref:System.ServiceModel.InstanceContext> の初期化中にディスパッチャーによって呼び出されます。  
  
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
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`  
  
## <a name="see-also"></a>関連項目

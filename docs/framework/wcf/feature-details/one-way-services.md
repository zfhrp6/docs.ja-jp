---
title: "一方向サービス | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "サービス コントラクト [WCF], 一方向の定義"
  - "WCF [WCF], 一方向のサービス コントラクト"
  - "Windows Communication Foundation [WCF], 一方向のサービス コントラクト"
ms.assetid: 19053a36-4492-45a3-bfe6-0365ee0205a3
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# 一方向サービス
サービス操作の既定の動作は、要求\/応答パターンです。要求\/応答パターンでは、サービス操作がコードで `void` 型のメソッドとして表される場合であっても、クライアントは応答メッセージを待機します。一方向操作では、メッセージが 1 つ送信されるだけです。受信者は応答メッセージを送信せず、送信者もこれを待機しません。  
  
 一方向デザイン パターンは次の場合に使用します。  
  
-   クライアントが操作を呼び出す必要があり、操作レベルで操作の結果に影響を受けない場合。  
  
-   <xref:System.ServiceModel.NetMsmqBinding> クラスまたは <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> クラスを使用している場合 \(このシナリオ[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[WCF のキュー](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)」を参照してください\)。  
  
 操作が一方向の場合、エラー情報をクライアントに伝達する応答メッセージはありません。エラー状態を検出するには、信頼できるセッションのような基になるバインディングの機能を使用できます。また、2 つの一方向操作 \(1 つは、サービス操作を呼び出すための、クライアントからサービスへの一方向コントラクト、もう 1 つは、クライアントが実装するコールバックを使用してサービスがエラーを返せるようにする、サービスとクライアントの間の一方向コントラクト\) を使用する双方向サービス コントラクトをデザインすることもできます。  
  
 一方向サービス コントラクトを作成するには、サービス コントラクトを定義し、<xref:System.ServiceModel.OperationContractAttribute> クラスを各操作に適用し、<xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> プロパティを `true` に設定します。次のコードを参照してください。  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 完全な例については、「[一方向](../../../../docs/framework/wcf/samples/one-way.md)」のサンプルを参照してください。  
  
## 一方向操作でのクライアントのブロック  
 一方向アプリケーションの中には、送信データをネットワーク接続に書き込むとすぐに処理を終了するものがある一方で、バインディングまたはサービスの実装により [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントが一方向操作を使用できなくなるというシナリオもあることを理解することが重要です。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント アプリケーションでは、送信データがネットワーク接続に書き込まれるまで [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント オブジェクトは処理を終了しません。これは一方向操作を含め、すべてのメッセージ交換パターンについて当てはまることで、トランスポートへのデータの書き込みに何らかの問題があると、クライアントが処理を終了できなくなることを意味します。問題の種類によっては、例外が発生したりサービスへのメッセージの送信に遅延が発生したりする結果となることがあります。  
  
 たとえば、トランスポートがエンドポイントを見つけられない場合、大きな遅延なしに <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=fullName> 例外がスローされます。ただし、サービスが何らかの理由によりデータをネットワークから読み込めないために、クライアントのトランスポート送信操作が終了しない可能性もあります。このような場合、クライアントのトランスポート バインディングで <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A?displayProperty=fullName> 期間が経過すると、<xref:System.TimeoutException?displayProperty=fullName> がスローされますが、タイムアウト時間が経過するまで例外はスローされません。またサービスに多数のメッセージが集中しているために、一定の期間が経過するまでサービスがメッセージを処理できないことがあります。この場合も、サービスがメッセージを処理できるまで、または例外がスローされるまで、一方向クライアントはブロックします。  
  
 さらに別の状況として、サービスの <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=fullName> プロパティが <xref:System.ServiceModel.ConcurrencyMode> に設定されているのに、バインディングが複数のセッションを使用する場合があります。この場合、ディスパッチャーにより受信メッセージの並び替え \(セッションの要件\) が強制され、サービスがそのセッションの以前のメッセージの処理を終えるまで、後続のメッセージはネットワークから読み込まれません。この場合も、クライアントはブロックしますが、例外が発生するかどうかは、サービスがこのクライアントで設定されているタイムアウト期間が経過する前に、待機中のデータを処理できるかどうかによって異なります。  
  
 この問題を軽減するには、クライアント オブジェクトとクライアントのトランスポート送信操作との間にバッファーを挿入します。たとえば、非同期呼び出しまたはメモリ内メッセージ キューを使用すると、クライアント オブジェクトの処理を短時間で終了できます。どちらのアプローチでも機能性は向上しますが、スレッド プールとメッセージ キューのサイズによる制限は残ります。  
  
 代わりに、クライアントおよびサービスの各種コントロールを調べてアプリケーション シナリオをテストし、最適な構成がどちら側にあるのかを判断することをお勧めします。たとえば、セッションの使用によりサービスでのメッセージの処理がブロックされている場合、<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=fullName> プロパティを <xref:System.ServiceModel.InstanceContextMode> に設定することによって、異なるサービス インスタンスによって各メッセージが処理されるようにし、また <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> を <xref:System.ServiceModel.ConcurrencyMode> に設定することによって、複数のスレッドで同時にメッセージをディスパッチできるようにします。また、別のアプローチとして、サービスとクライアント バインディングの読み取りクォータを増やすという方法もあります。  
  
## 参照  
 [一方向](../../../../docs/framework/wcf/samples/one-way.md)
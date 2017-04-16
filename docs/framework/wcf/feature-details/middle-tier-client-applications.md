---
title: "中間層クライアント アプリケーション | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f9714a64-d0ae-4a98-bca0-5d370fdbd631
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# 中間層クライアント アプリケーション
ここでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用する中間層クライアント アプリケーション固有のさまざまな問題について説明します。  
  
## 中間層クライアントのパフォーマンス向上  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] を使用する Web サービスなど従来の通信技術と比べ、豊富な機能セットを備えた [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント インスタンスの作成が複雑になる場合があります。  たとえば、<xref:System.ServiceModel.ChannelFactory%601> オブジェクトを開いている場合、サービスとの間にセキュリティで保護されたセッションを確立できますが、そのぶんクライアント インスタンスの起動時間が長くなります。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントはいくつかの呼び出しを実行してから閉じるため、通常、このような追加機能がクライアント アプリケーションに大きな影響を与えることはありません。  
  
 ただし、中間層クライアント アプリケーションは、多くの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント オブジェクトをすばやく作成できるので、その結果、初期化要件が増加します。  サービスを呼び出すときに中間層アプリケーションのパフォーマンスを向上させる方法は主に 2 つあります。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント オブジェクトをキャッシュし、以降の呼び出しで可能であればそれを再利用します。  
  
-   <xref:System.ServiceModel.ChannelFactory%601> オブジェクトを作成し、そのオブジェクトを使用して呼び出しごとに新しい [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント チャネルを作成します。  
  
 これらの方法を使用するときに検討すべきいくつかの問題があります。  
  
-   サービスがセッションを使用してクライアント固有の状態を維持する場合、サービスの状態が中間層クライアントの状態に関連付けられているため、クライアント層の複数の要求を持つ中間層の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントを再利用することはできません。  
  
-   サービスがクライアントごとに認証を実行する必要がある場合、中間層のクライアント資格情報を [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント \(または <xref:System.ServiceModel.ChannelFactory%601>\) の作成後に変更できないため、中間層の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント \(または [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント チャネル オブジェクト\) を再利用するのではなく、受信要求ごとに新しいクライアントを中間層に作成する必要があります。  
  
-   チャネルにより作成されたチャネルとクライアントは、スレッド セーフですが複数のメッセージをネットワークに同時に書き込むことをサポートしていない場合があります。  大容量メッセージ \(特にストリーミング\) を送信すると、送信操作はブロックされ別の送信が完了するまで待機する場合があります。  チャネルを再利用するサービスに制御フローが戻った場合、これにより、同時性の欠如とデッドロックの可能性という 2 種類の問題が発生します \(つまり、共有クライアントがサービスを呼び出すと、そのコード パスは結果的に共有クライアントにコールバックします\)。  これは、再利用する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントの型には左右されません。  
  
-   チャネルを共有しているかどうかに関係なく、エラーの発生したチャネルを処理する必要があります。  ただし、チャネルを再利用するときに、エラーの発生しているチャネルは複数の保留中の要求を削除するか送信することができます。  
  
 複数の要求に対してクライアントを再利用するためのベスト プラクティスが示された例については、「[ASP.NET クライアントでのデータ バインディング](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)」を参照してください。  
  
 さらに、<xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化できるデータ型を使用するクライアントの起動時のパフォーマンスを向上したり、実行時にこのようなデータ型のシリアル化コードを生成およびコンパイルしたりできます \(この場合、起動時のパフォーマンスが低下することがあります\)。  [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を使用すると、必要なシリアル化コードをアプリケーションのコンパイル済みアセンブリから生成することで、このようなアプリケーションの起動時のパフォーマンスを改善できます。  詳細については、「[方法 : XmlSerializer を使用する WCF クライアント アプリケーションの起動時間を短縮する](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)」を参照してください。  
  
## 参照  
 [WCF クライアントを使用したサービスへのアクセス](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)
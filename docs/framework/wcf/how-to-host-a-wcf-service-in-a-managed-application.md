---
title: "方法 : マネージ アプリケーションで WCF サービスをホストする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
caps.latest.revision: 42
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 42
---
# 方法 : マネージ アプリケーションで WCF サービスをホストする
マネージ アプリケーションでサービスをホストするには、マネージ アプリケーション コード内にサービスのコードを埋め込み、サービスのエンドポイントをコードで強制的に定義するか、構成を使用して宣言により定義してから、または既定のエンドポイントを使用して、<xref:System.ServiceModel.ServiceHost> のインスタンスを作成します。  
  
 メッセージの受信を開始するには、<xref:System.ServiceModel.ServiceHost> で <xref:System.ServiceModel.ICommunicationObject.Open%2A> を呼び出します。これにより、サービスのリスナーが作成されて開きます。この方法によるサービスのホストは、マネージ アプリケーション自体がホスト作業を行うため、"自己ホスト" と呼ばれることがあります。サービスを閉じるには、<xref:System.ServiceModel.ServiceHost> で <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=fullName> を呼び出します。  
  
 サービスは、マネージ Windows サービス、インターネット インフォメーション サービス \(IIS\)、または Windows プロセス アクティブ化サービス \(WAS\) でホストすることもできます。サービスのホスティング[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[ホスティング サービス](../../../docs/framework/wcf/hosting-services.md)」を参照してください。  
  
 マネージ アプリケーションでのサービスのホストは、展開するインフラストラクチャが最小限で済むため、最も柔軟性があります。マネージ アプリケーションでのホスティング サービス[!INCLUDE[crabout](../../../includes/crabout-md.md)]、[マネージ アプリケーションのホスト](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)」を参照してください。  
  
 次の手順では、自己ホスト型サービスをコンソール アプリケーションに実装する方法を示します。  
  
### 自己ホスト型サービスを作成するには  
  
1.  [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] を開き、**\[ファイル\]** メニューの **\[新規作成\]**、**\[プロジェクト\]** の順にクリックします。  
  
2.  **\[インストールされているテンプレート\]** ボックスで **\[Visual C\#\]**、**\[Windows\]** または **\[Visual Basic\]**、**\[Windows\]** を選択します。[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] の設定に応じて、選択した内容の 1 つまたは両方が **\[インストールされているテンプレート\]** ボックスの **\[他の言語\]** ノードに表示されます。  
  
3.  **\[Windows\]**  ボックスから **\[コンソール アプリケーション\]** を選択します。**\[名前\]** ボックスに「`SelfHost`」と入力して **\[OK\]** をクリックします。  
  
4.  **ソリューション エクスプローラー**で **\[SelfHost\]** を右クリックし、**\[参照の追加\]** をクリックします。**\[.NET\]** タブの **\[System.ServiceModel\]** をクリックし、**\[OK\]** をクリックします。  
  
    > [!TIP]
    >  **ソリューション エクスプローラー** ウィンドウが表示されない場合は、**\[表示\]** メニューの **\[ソリューション エクスプローラー\]** をクリックします。  
  
5.  まだ開いていない場合は、**ソリューション エクスプローラー**で **\[Program.cs\]** または **\[Module1.vb\]** をダブルクリックして、コード ウィンドウで開きます。ファイルの先頭に次のステートメントを追加します。  
  
     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]  
  
6.  サービス コントラクトを定義して実装します。この例では、サービスへの入力に基づいてメッセージを返す `HelloWorldService` を定義します。  
  
     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]  
  
    > [!NOTE]
    >  サービス インターフェイスを定義および実装する方法[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[方法 : サービス コントラクトを定義する](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)」および「[方法 : サービス コントラクトを実装する](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)」を参照してください。  
  
7.  `Main` メソッドの上部で、サービスのベース アドレスで <xref:System.Uri> クラスのインスタンスを作成します。  
  
     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]  
  
8.  <xref:System.ServiceModel.ServiceHost> クラスのインスタンスを作成して、サービス型を表す <xref:System.Type> とベース アドレス URI \(Uniform Resource Identifier\) を [ServiceHost\(Type, Uri\<xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29> に渡します。メタデータ公開を有効にして、<xref:System.ServiceModel.ServiceHost> で <xref:System.ServiceModel.ICommunicationObject.Open%2A> メソッドを呼び出し、サービスを初期化してメッセージを受信する準備をします。  
  
     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]  
  
    > [!NOTE]
    >  この例では、既定のエンドポイントを使用するので、このサービスには構成ファイルは必要ありません。エンドポイントが構成されていない場合、ランタイムは、サービスによって実装されたサービス コントラクトごとに 1 つのエンドポイントを各ベース アドレスに作成します。既定のエンドポイント[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[簡略化された構成](../../../docs/framework/wcf/simplified-configuration.md)」および「[WCF サービスの簡略化された構成](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)」を参照してください。  
  
9. Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
### サービスをテストするには  
  
1.  Ctrl キーを押しながら F5 キーを押してサービスを実行します。  
  
2.  **\[WCF のテスト用クライアント\]** を開きます。  
  
    > [!TIP]
    >  **\[WCF のテスト用クライアント\]** を開くには、[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] コマンド プロンプトを開いて、**WcfTestClient.exe** を実行します。  
  
3.  **\[ファイル\]** メニューの **\[サービスの追加\]** をクリックします。  
  
4.  アドレス ボックスに「`http://localhost:8080/hello`」と入力し、**\[OK\]** をクリックします。  
  
    > [!TIP]
    >  サービスが実行していることを確認してください。サービスが実行していない場合、この手順は失敗します。コードでベース アドレスを変更した場合は、この手順で、変更したアドレスを使用します。  
  
5.  **\[マイ サービス プロジェクト\]** ノードの **\[SayHello\]** をダブルクリックします。自分の名前を **\[要求\]** ボックスの **\[値\]** 列に入力して、**\[起動\]** をクリックします。応答メッセージが **\[応答\]** ボックスに表示されます。  
  
## 使用例  
 `HelloWorldService` 型のサービスをホストする <xref:System.ServiceModel.ServiceHost> オブジェクトを作成し、<xref:System.ServiceModel.ServiceHost> で <xref:System.ServiceModel.ICommunicationObject.Open%2A> メソッドを呼び出す例を、次に示します。ベース アドレスがコードで指定され、メタデータ公開が有効化されていて、既定のエンドポイントが使用されています。  
  
 [!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
 [!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]  
  
## 参照  
 <xref:System.Uri>   
 <xref:System.Configuration.ConfigurationManager.AppSettings%2A>   
 <xref:System.Configuration.ConfigurationManager>   
 [方法 : IIS で WCF サービスをホストする](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)   
 [自己ホスト](../../../docs/framework/wcf/samples/self-host.md)   
 [ホスティング サービス](../../../docs/framework/wcf/hosting-services.md)   
 [方法 : サービス コントラクトを定義する](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)   
 [方法 : サービス コントラクトを実装する](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)   
 [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)   
 [サービスとクライアントを構成するためのバインディングの使用](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)   
 [システム標準のバインディング](../../../docs/framework/wcf/system-provided-bindings.md)
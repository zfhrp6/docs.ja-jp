---
title: "方法 : Windows Communication Foundation クライアントを作成する | Microsoft Docs"
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
helpviewer_keywords: 
  - "クライアント [WCF], 実行"
  - "WCF クライアント [WCF], 実行"
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
caps.latest.revision: 64
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 64
---
# 方法 : Windows Communication Foundation クライアントを作成する
これは、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] アプリケーションの作成に必要な 6 つのタスクのうち、4 番目のタスクです。6 つのすべてのタスクの概要については、「[チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)」を参照してください。  
  
 ここでは、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスからメタデータを取得し、このメタデータを使用して、サービスにアクセスできる [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント プロキシを作成する方法について説明します。このタスクは、Visual Studio によって提供される "サービス参照の追加" 機能を使用することで完了できます。このツールは、サービスの MEX エンドポイントからメタデータを取得し、ユーザーが選択した言語 \(既定では C\#\) でクライアント プロキシのマネージ ソース コード ファイルを生成します。このツールでは、クライアント プロキシの作成だけでなく、クライアントの構成ファイルの作成または更新も行います。この構成ファイルにより、クライアント アプリケーションはエンドポイントのいずれかにあるサービスに接続できるようになります。  
  
> [!NOTE]
>  また、Visual Studio 内で "サービス参照の追加" を使用する代わりに、[ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ツールを使用して、プロキシ クラスおよび構成を生成することもできます。  
  
> [!WARNING]
>  [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] のクラス ライブラリ プロジェクトから [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスを呼び出すときは、サービス参照の追加機能を使用して、プロキシおよび関連構成ファイルを自動的に生成できます。この構成ファイルはクラス ライブラリ プロジェクトで使用されません。クラス ライブラリを呼び出す実行可能ファイルの app.config ファイルに、生成された構成ファイル内の設定を追加する必要があります。  
  
 クライアント アプリケーションは生成されたプロキシ クラスを使用して、サービスと通信します。この手順については、「[方法 : クライアントを使用する](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)」を参照してください。  
  
### Windows Communication Foundation クライアントを作成するには  
  
1.  新しいコンソール アプリケーション プロジェクトを作成します。入門ソリューションを右クリックし、**\[追加\]**、**\[新しいプロジェクト\]** の順にクリックします。**\[新しいプロジェクトの追加\]** ダイアログ ボックスの左側で、**\[C\#\]** または **\[VB\]** の **\[Windows\]** をクリックします。ダイアログ ボックスの中央のセクションで、**\[コンソール アプリケーション\]** を選択します。プロジェクトに `GettingStartedClient` という名前を付けます。  
  
2.  GettingStartedClient プロジェクトのターゲット フレームワークを .NET Framework 4.5 に設定します。ソリューション エクスプローラーで **\[GettingStartedClient\]** を右クリックし、**\[プロパティ\]** を選択します。**\[ターゲット フレームワーク\]** ボックスの一覧の **\[.NET Framework 4.5\]** をクリックします。VB プロジェクトのターゲット フレームワークを設定する方法は多少異なり、GettingStartedClient プロジェクトの \[プロパティ\] ダイアログ ボックスで、画面左側の **\[コンパイル\]** タブをクリックし、ダイアログ ボックスの左下隅にある **\[詳細コンパイル オプション\]** をクリックします。次に、**\[ターゲット フレームワーク\]** ボックスの一覧の **\[.NET Framework 4.5\]** をクリックします。  
  
     ターゲット フレームワークを設定すると、Visual Studio 2011 はソリューションを再読み込みします。ダイアログが表示されたら、**\[OK\]** をクリックします。  
  
3.  System.ServiceModel への参照を GettingStartedClient プロジェクトに追加します。ソリューション エクスプローラーで GettingStartedClient プロジェクトの **\[参照\]** フォルダーを右クリックし、**\[参照の追加\]** をクリックします。**\[参照の追加\]** ダイアログ ボックスの左側で、**\[フレームワーク\]** を選択します。\[アセンブリの検索\] ボックスに「`System.ServiceModel`」と入力します。ダイアログ ボックスの中央のセクションで、**\[System.ServiceModel\]** を選択し、**\[追加\]**、**\[閉じる\]** の順にクリックします。メイン メニューの **\[すべて保存\]** をクリックして、ソリューションを保存します。  
  
4.  次に、電卓サービスへのサービス参照を追加します。これを実行する前に、GettingStartedHost コンソール アプリケーションを起動する必要があります。ホストが実行中になったら、ソリューション エクスプローラーで GettingStartedClient プロジェクトの \[参照\] フォルダーを右クリックし、\[サービス参照の追加\] をクリックします。\[サービス参照の追加\] ダイアログ ボックスの \[アドレス\] ボックスに URL \(http:\/\/localhost:8000\/ServiceModelSamples\/Service\) を入力し、**\[移動\]** をクリックします。\[CalculatorService\] が \[サービス\] ボックスに表示されたら、\[CalculatorService\] をダブルクリックして、そのサービスによって実装されているサービス コントラクトを展開して表示します。既定の名前空間を変更せずに、**\[OK\]** をクリックします。  
  
     Visual Studio を使用してサービスへの参照を追加すると、新しい項目がソリューション エクスプローラーの GettingStartedClient プロジェクトの \[サービス参照\] フォルダーの下に表示されます。[ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ツールを使用した場合、ソース コード ファイルおよび app.config ファイルが生成されます。  
  
     コマンド ライン ツールである [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を適切なスイッチと共に使用して、クライアント コードを作成することもできます。次の例では、サービスのコード ファイルと構成ファイルを生成しています。最初の例は VB でプロキシを生成する方法を示し、2 番目の例は C\# でプロキシを生成する方法を示しています。  
  
    ```  
    svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/ServiceModelSamples/service  
  
    ```  
  
    ```csharp  
    svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/ServiceModelSamples/service  
  
    ```  
  
 ここでは、クライアント アプリケーションが電卓サービスを呼び出すために使用するプロキシを作成しました。シリーズの次のトピックに進んでください: [方法 : クライアントを構成する](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)  
  
## 参照  
 [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)   
 [概要](../../../docs/framework/wcf/samples/getting-started-sample.md)   
 [自己ホスト](../../../docs/framework/wcf/samples/self-host.md)   
 [方法 : 構成ファイルを使用してサービスのメタデータを公開する](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)   
 [方法 : Svcutil.exe を使用してメタデータ ドキュメントをダウンロードする](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
---
title: "サービス操作エラーの監視 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59472ba3-8ebf-4479-bd7b-f440d5e636cb
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# サービス操作エラーの監視
アプリケーションに対して分析トレースが有効になっている場合、サービス エラーはイベント ビューアーで簡単に監視できます。ここでは、サービス操作が失敗したことを確認する方法、およびエラーの原因を特定する方法を示します。  
  
### サービス操作エラーに関する情報の確認  
  
1.  **\[スタート\]** ボタン、**\[ファイル名を指定して実行\]** の順にクリックし、「`eventvwr.exe`」と入力してイベント ビューアーを開きます。  
  
2.  分析トレースを有効にしていない場合は、**\[アプリケーションとサービス ログ\]**、**\[Microsoft\]**、**\[Windows\]**、**\[アプリケーション サーバー \- アプリケーション\]** の順に展開します。**\[表示\]**、**\[分析およびデバッグ ログの表示\]** の順にクリックします。**\[分析\]** を右クリックし、**\[ログを有効にする\]** を選択します。サービス操作が失敗した後にトレースを表示できるように、イベント ビューアーを開いたままにしておきます。  
  
3.  次に、[!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] の「[チュートリアル入門](../../../../../docs/framework/wcf/getting-started-tutorial.md)」で作成したサンプルを開きます。サービスを作成できるように、管理者として [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] を実行する必要があることに注意してください。[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サンプルがインストールされている場合、このチュートリアルで作成する完成済みのプロジェクトが含まれている[概要](../../../../../docs/framework/wcf/samples/getting-started-sample.md)を開くことができます。  
  
4.  Server プロジェクトの Program.cs ファイルで、`CalculatorService` クラスの `Divide` メソッドの先頭に次のコード行を追加します。  
  
    ```  
    if (n2 == 0) throw new DivideByZeroException();  
  
    ```  
  
5.  クライアント プロジェクトの Program.cs ファイルで、value2 に割り当てる値をゼロに変更します。  
  
    ```  
    //Call the Divide service operation  
    value1 = 22.00D;  
    value2 = 0.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0}, {1}) = {2}", value1, value2, result);  
  
    ```  
  
6.  **Ctrl** キーを押しながら F5 キーを押して、サーバー アプリケーションをデバッグなしで実行します。  
  
7.  Visual Studio コマンド プロンプトを開きます。クライアント ディレクトリに移動し、コマンド ラインからクライアントを実行します。  
  
8.  イベント ビューアーで、分析ログを無効化および更新し、イベント ID でイベントを並べ替えます。サービス エラーを示すイベント ID [219 \- ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md) のイベントを検索します。  
  
    ```Output  
    メッセージの処理中に種類 'System.DivideByZeroException' のハンドルされない例外がスローされました。完全な例外の ToString: System.DivideByZeroException: 0 で除算しようとしました。  
    ```  
  
    > [!NOTE]
    >  イベントは、イベント ビューアーへの送信時にバッファーされます。そのため、エラー イベントはすぐに表示されない場合があります。
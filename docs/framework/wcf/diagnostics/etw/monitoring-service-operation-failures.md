---
title: サービス操作エラーの監視
ms.date: 03/30/2017
ms.assetid: 59472ba3-8ebf-4479-bd7b-f440d5e636cb
ms.openlocfilehash: 16ed779f77836fb68cf1edf1e01dbb3c0df01d45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="monitoring-service-operation-failures"></a>サービス操作エラーの監視
アプリケーションに対して分析トレースが有効になっている場合、サービス エラーはイベント ビューアーで簡単に監視できます。  ここでは、サービス操作が失敗したことを確認する方法、およびエラーの原因を特定する方法を示します。  
  
### <a name="determining-service-operation-failure-information"></a>サービス操作エラーに関する情報の確認  
  
1.  クリックしてイベント ビューアーを開いて**開始**、**実行**、」と入力して`eventvwr.exe`です。  
  
2.  分析トレースを有効にしていない場合は展開**Applications and Services Logs**、 **Microsoft**、 **Windows**、**アプリケーション サーバー-アプリケーション**. 選択**ビュー**、 **分析およびデバッグ ログ**です。 右クリック**分析**選択**ログの有効化**です。 サービス操作が失敗した後にトレースを表示できるように、イベント ビューアーを開いたままにしておきます。  
  
3.  作成したサンプルを次に、開く、[チュートリアル入門](../../../../../docs/framework/wcf/getting-started-tutorial.md)で[!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)]実行する必要があります[!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)]を管理者として、サービスを作成できるようにします。 ある場合、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]サンプルのインストール、開くことができます、[作業の開始](../../../../../docs/framework/wcf/samples/getting-started-sample.md)チュートリアルに完成したプロジェクトが含まれています。  
  
4.  Server プロジェクトの Program.cs ファイルで、`Divide` クラスの `CalculatorService` メソッドの先頭に次のコード行を追加します。  
  
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
  
6.  キーを押してデバッグを行わない場合、サーバー アプリケーションを実行**ctrl キーを押しながら f5 キーを押して**です。  
  
7.  Visual Studio コマンド プロンプトを開きます。  クライアント ディレクトリに移動し、コマンド ラインからクライアントを実行します。  
  
8.  イベント ビューアーで、分析ログを無効化および更新し、イベント ID でイベントを並べ替えます。  イベント ID を持つイベントを探して[219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md)サービスのエラーを記述します。  
  
    ```Output  
    There was an unhandled exception of type 'System.DivideByZeroException' during message processing.  Full Exception ToString: System.DivideByZeroException: Attempted to divide by zero.  
    ```  
  
    > [!NOTE]
    >  イベントは、イベント ビューアーへの送信時にバッファーされます。そのため、エラー イベントはすぐに表示されない場合があります。

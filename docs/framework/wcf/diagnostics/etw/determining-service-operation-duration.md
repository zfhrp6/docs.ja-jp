---
title: "サービス操作の実行時間の確認 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# サービス操作の実行時間の確認
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] アプリケーションで分析トレースを有効にしている場合、イベント ログを調べるだけでサービス操作の実行時間を簡単に確認できます。  ここでは、サービス操作の実行にかかる時間を確認する方法を示します。  
  
### サービス操作の実行時間の確認  
  
1.  **\[スタート\]** ボタン、**\[ファイル名を指定して実行\]** の順にクリックし、「`eventvwr.exe`」と入力してイベント ビューアーを開きます。  
  
2.  分析トレースを有効にしていない場合は、**\[アプリケーションとサービス ログ\]**、**\[Microsoft\]**、**\[Windows\]**、**\[アプリケーション サーバー \- アプリケーション\]** の順に展開します。  **\[表示\]**、**\[分析およびデバッグ ログの表示\]** の順にクリックします。  **\[分析\]** を右クリックし、**\[ログを有効にする\]** をクリックします。  サービス操作が実行された後にトレースを表示できるように、イベント ビューアーを開いたままにしておきます。  
  
3.  次に、サービス プロジェクトおよびそのサービスと対話するクライアント プロジェクトが含まれている [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] アプリケーションを開きます。  このようなアプリケーションの作成方法については、「[チュートリアル入門](../../../../../docs/framework/wcf/getting-started-tutorial.md)」を参照してください。  [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サンプルがインストールされている場合、このチュートリアルで作成する完成済みのプロジェクトが含まれている[概要](../../../../../docs/framework/wcf/samples/getting-started-sample.md)を開くことができます。  
  
4.  **F5** キーを押してサーバー アプリケーションを実行します。  **Client** プロジェクトを右クリックし、**\[デバッグ\]**、**\[新しいインスタンスを開始\]** の順にクリックして、クライアント アプリケーションを実行します。  
  
5.  イベント ビューアーで、分析ログを更新し、イベント ID でイベントを並べ替えます。  イベント ID が [214 \- OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md) のイベントを探します。  これらのイベントは、完了した操作、およびその操作にかかった時間を示します。  次のイベントは、追加操作の時間を示しています。  
  
    ```Output  
  
    OperationInvoker がメソッド 'Add' への呼び出しを完了しました。  メソッド呼び出し時間は '3' ミリ秒でした。    
    ```
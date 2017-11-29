---
title: "サービス操作の実行時間の確認"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 63a8c92713ee452da2439475ac526229d1e5741c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="determining-service-operation-duration"></a>サービス操作の実行時間の確認
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] アプリケーションで分析トレースを有効にしている場合、イベント ログを調べるだけでサービス操作の実行時間を簡単に確認できます。  ここでは、サービス操作の実行にかかる時間を確認する方法を示します。  
  
### <a name="determining-service-operation-execution-duration"></a>サービス操作の実行時間の確認  
  
1.  クリックしてイベント ビューアーを開いて**開始**、**実行**、」と入力して`eventvwr.exe`です。  
  
2.  分析トレースを有効にしていない場合は展開**Applications and Services Logs**、 **Microsoft**、 **Windows**、**アプリケーション サーバー-アプリケーション**. 選択**ビュー**、 **分析およびデバッグ ログ**です。 右クリック**分析**選択**ログの有効化**です。 サービス操作が実行された後にトレースを表示できるように、イベント ビューアーを開いたままにしておきます。  
  
3.  次に、サービス プロジェクトおよびそのサービスと対話するクライアント プロジェクトが含まれている [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] アプリケーションを開きます。  このようなアプリケーションを作成するには、次の[チュートリアル入門](../../../../../docs/framework/wcf/getting-started-tutorial.md)です。  ある場合、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]サンプルのインストール、開くことができます、[作業の開始](../../../../../docs/framework/wcf/samples/getting-started-sample.md)チュートリアルに完成したプロジェクトが含まれています。  
  
4.  キーを押してサーバー アプリケーションを実行**f5 キーを押して**です。 右クリックして、クライアント アプリケーションを実行、**クライアント**プロジェクトを選択して**デバッグ**、**新しいインスタンスを開始**です。  
  
5.  イベント ビューアーで、分析ログを更新し、イベント ID でイベントを並べ替えます。  イベント ID を持つイベントを探します[214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md)です。  これらのイベントは、完了した操作、およびその操作にかかった時間を示します。  次のイベントは、追加操作の時間を示しています。  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```

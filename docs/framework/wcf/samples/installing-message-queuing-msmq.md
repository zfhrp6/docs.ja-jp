---
title: "メッセージ キュー (MSMQ) のインストール | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# メッセージ キュー (MSMQ) のインストール
メッセージ キュー 4.0 およびメッセージ キュー 3.0 をインストールする方法を次の手順に示します。  
  
> [!NOTE]
>  メッセージ キュー 4.0 は、[!INCLUDE[wxp](../../../../includes/wxp-md.md)] および [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] では使用できません。  
  
#### Windows Server 2008 または Windows Server 2008 R2 にメッセージ キュー 4.0 をインストールするには  
  
1.  サーバー マネージャーで **\[機能\]** をクリックします。  
  
2.  **\[機能の概要\]** の右側のペインで、**\[機能の追加\]** をクリックします。  
  
3.  表示されたウィンドウで **\[メッセージ キュー\]** を展開します。  
  
4.  **\[メッセージ キュー サービス\]** を展開します。  
  
5.  **\[ディレクトリ サービス統合\]** を \(ドメインに参加するコンピューターの場合\) クリックし、**\[HTTP サポート\]** をクリックします。  
  
6.  **\[次へ\]** をクリックし、**\[インストール\]** をクリックします。  
  
#### Windows 7 または Windows Vista にメッセージ キュー 4.0 をインストールするには  
  
1.  **コントロール パネル**を開きます。  
  
2.  **\[プログラム\]** をクリックし、**\[プログラムと機能\]** の **\[Windows の機能の有効化または無効化\]** をクリックします。  
  
3.  \[Microsoft Message Queue \(MSMQ\) Server\]、\[Microsoft Message Queue \(MSMQ\) Server Core\] の順に展開して、インストールする次のメッセージ キュー機能のチェック ボックスをオンにします。  
  
    -   \[MSMQ Active Directory Domain Services Integration\] \(ドメインに参加するコンピューターの場合\)  
  
    -   \[MSMQ HTTP サポート\]  
  
4.  **\[OK\]** をクリックします。  
  
5.  コンピューターを再起動するかどうかを確認するメッセージが表示されたら、**\[OK\]** をクリックしてインストールを完了します。  
  
#### Windows XP および Windows Server 2003 にメッセージ キュー 3.0 をインストールするには  
  
1.  **コントロール パネル**を開きます。  
  
2.  **\[プログラムの追加と削除\]**、**\[Windows コンポーネントの追加と削除\]** の順にクリックします。  
  
3.  メッセージ キューを選択し、**\[詳細\]** をクリックします。  
  
    > [!NOTE]
    >  [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] を実行している場合は、メッセージ キューにアクセスするアプリケーション サーバーを選択します。  
  
4.  詳細ページで、\[MSMQ HTTP サポート\] オプションが選択されていることを確認します。  
  
5.  **\[OK\]** をクリックして詳細ページを閉じ、**\[次へ\]** をクリックします。インストールを完了します。  
  
6.  コンピューターを再起動するかどうかを確認するメッセージが表示されたら、**\[OK\]** をクリックしてインストールを完了します。  
  
## 参照  
 [セットアップ手順](../../../../docs/framework/wcf/samples/set-up-instructions.md)
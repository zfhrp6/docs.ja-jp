---
title: メッセージ キュー (MSMQ) のインストール
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: b54fab13d644cafda8a070280d672c60cf71b675
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="installing-message-queuing-msmq"></a>メッセージ キュー (MSMQ) のインストール
メッセージ キュー 4.0 およびメッセージ キュー 3.0 をインストールする方法を次の手順に示します。  
  
> [!NOTE]
>  メッセージ キュー 4.0 は、[!INCLUDE[wxp](../../../../includes/wxp-md.md)] および [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] では使用できません。  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a>Windows Server 2008 または Windows Server 2008 R2 にメッセージ キュー 4.0 をインストールするには  
  
1.  サーバー マネージャーで、をクリックして**機能**します。  
  
2.  右側のペインで**機能の概要**をクリックして**機能の追加**です。  
  
3.  結果ウィンドウで、展開**メッセージ キュー**です。  
  
4.  展開**メッセージ キュー サービス**です。  
  
5.  をクリックして**ディレクトリ サービス統合**(コンピューターの場合、ドメインに参加している)、し、クリックして**HTTP サポート**です。  
  
6.  をクリックして**次**、をクリックして**インストール**です。  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a>Windows 7 または Windows Vista にメッセージ キュー 4.0 をインストールするには  
  
1.  **[コントロール パネル]** を開きます。  
  
2.  をクリックして**プログラム**し、**プログラムと機能**をクリックして**Windows の機能のオンとオフを**です。  
  
3.  [Microsoft Message Queue (MSMQ) Server]、[Microsoft Message Queue (MSMQ) Server Core] の順に展開して、インストールする次のメッセージ キュー機能のチェック ボックスをオンにします。  
  
    -   [MSMQ Active Directory Domain Services Integration] \(ドメインに参加するコンピューターの場合)  
  
    -   [MSMQ HTTP サポート]  
  
4.  **[OK]** をクリックします。  
  
5.  コンピューターを再起動するメッセージが表示されたら、クリックして**OK**インストールを完了します。  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a>Windows XP および Windows Server 2003 にメッセージ キュー 3.0 をインストールするには  
  
1.  **[コントロール パネル]** を開きます。  
  
2.  をクリックして**プログラムの追加と削除** をクリックし、 **Windows コンポーネントの追加**です。  
  
3.  メッセージ キューを選択し、クリックして**詳細**です。  
  
    > [!NOTE]
    >  [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] を実行している場合は、メッセージ キューにアクセスするアプリケーション サーバーを選択します。  
  
4.  詳細ページで、[MSMQ HTTP サポート] オプションが選択されていることを確認します。  
  
5.  をクリックして**OK**の詳細 ページを終了し、をクリックして**次へ**です。 インストールを完了します。  
  
6.  コンピューターを再起動するメッセージが表示されたら、クリックして**OK**インストールを完了します。  
  
## <a name="see-also"></a>関連項目  
 [セットアップ手順](../../../../docs/framework/wcf/samples/set-up-instructions.md)

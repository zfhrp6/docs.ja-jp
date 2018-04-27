---
title: '方法 : サービスを開始する'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 47e27f579c0ed7d1be0b061bc6e79bba0c060abb
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-start-services"></a>方法 : サービスを開始する
サービスをインストールした後で、サービスを起動します。 起動することで、サービス クラスの <xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドが呼び出されます。 通常、<xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドにはサービスが本来行う処理を定義します。 サービスの起動後は、手動で一時停止または停止するまで、アクティブの状態を維持します。  
  
 サービスを自動で起動するか手動で起動するかを設定できます。 自動的に起動するサービスは、そのサービスがインストールされているコンピューターを再起動したとき、または初めて電源を入れたときに起動します。 手動で起動するサービスは、ユーザーが起動する必要があります。  
  
> [!NOTE]
>  既定では、Visual Studio で作成されたサービスは、手動で起動に設定されます。  
  
 さまざまな方法でサービスを手動で開始できます — から**サーバー エクスプ ローラー**から、**サービス コントロール マネージャー**、またはコードからコンポーネントを使用して呼び出される、<xref:System.ServiceProcess.ServiceController>です。  
  
 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> クラスの <xref:System.ServiceProcess.ServiceInstaller> プロパティを設定し、サービスを手動で起動するか自動で起動するかを指定します。  
  
### <a name="to-specify-how-a-service-should-start"></a>サービスの起動方法を指定するには  
  
1.  サービスの作成後、必要なインストーラーを追加します。 詳細については、次を参照してください。[する方法: サービス アプリケーションへのインストーラーの追加](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)です。  
  
2.  デザイナーで、対象となるサービスのインストーラーをクリックします。  
  
3.  **プロパティ**ウィンドウで、設定、<xref:System.ServiceProcess.ServiceInstaller.StartType%2A>プロパティに、次のいずれか。  
  
    |サービスを起動するタイミング|設定値|  
    |----------------------------------|--------------------|  
    |コンピューターを再起動したとき。|**自動**|  
    |明示的なユーザー アクションによってサービスを開始するとき。|**手動**|  
  
    > [!TIP]
    >  サービスが開始されているすべてのことを防ぐために設定することができます、<xref:System.ServiceProcess.ServiceInstaller.StartType%2A>プロパティを**無効になっている**です。 サーバーを数回再起動することが見込まれる場合は、サービスを自動的に起動しないように設定することで、再起動の時間を短縮できます。  
  
    > [!NOTE]
    >  以上のプロパティやその他のプロパティの設定は、サービスのインストール後に変更できます。  
  
     持つサービスを開始できるいくつかの方法があるその<xref:System.ServiceProcess.ServiceInstaller.StartType%2A>プロセス**手動**— から**サーバー エクスプ ローラー**から、 **Windows サービス コントロール マネージャー**、コードとの間です。 コンテキストでは実際には、サービスを開始すべてこれらのメソッドのことに注意する必要がある、**サービス コントロール マネージャー**です。**サーバー エクスプ ローラー**し、プログラム、サービスの開始の方法が実際には、コント ローラーを操作します。  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a>サーバー エクスプローラーでサービスを手動起動するには  
  
1.  **サーバー エクスプ ローラー**、表示されていない場合、サーバーを追加します。 詳細については、次を参照してください。 方法: アクセスおよびサーバー エクスプ ローラー データベース エクスプ ローラーを初期化します。  
  
2.  展開、 **Services**  ノードを見つけて、サービスを開始します。  
  
3.  サービスの名前を右クリックし、をクリックして**開始**です。  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a>サービス制御マネージャーでサービスを手動起動するには  
  
1.  開く、**サービス コントロール マネージャー**次のいずれかを行います。  
  
    -   Windows XP および 2000 Professional を右クリックして**マイ コンピューター**をクリックして、デスクトップ**管理**です。 ダイアログ ボックスが表示されますが、展開、**サービスとアプリケーション**ノード。  
  
         \- または -  
  
    -   Windows Server 2003 および Windows 2000 Server をクリックして**開始**、 をポイント**プログラム**、 をクリックして**管理ツール**、順にクリック**Services**.  
  
        > [!NOTE]
        >  Windows NT version 4.0 からこのダイアログ ボックスを開くことができます**コントロール パネルの **です。  
  
     サービスが一覧表示されます、 **Services**ウィンドウのセクションです。  
  
2.  一覧で、サービスを選択して、右クリックし、をクリックして**開始**です。  
  
### <a name="to-manually-start-a-service-from-code"></a>コードでサービスを手動起動するには  
  
1.  <xref:System.ServiceProcess.ServiceController> クラスのインスタンスを作成し、管理対象となるサービスと対話するように設定します。  
  
2.  <xref:System.ServiceProcess.ServiceController.Start%2A> メソッドを呼び出してサービスを起動します。  
  
## <a name="see-also"></a>関連項目  
 [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [方法 : Windows サービスを作成する](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [方法 : サービス アプリケーションにインストーラーを追加する](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)

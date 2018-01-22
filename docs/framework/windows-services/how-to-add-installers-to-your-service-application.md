---
title: "方法 : サービス アプリケーションにインストーラーを追加する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, deploying
- installation components, adding to services
- installers, adding to services
- Windows Service applications, adding installers
- services, adding installers
- ServiceInstaller class, adding installers to services
- ServiceProcessInstaller class, adding installers to services
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
caps.latest.revision: "14"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 15487d4311f896aa09c1c7712292058086a49b50
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-installers-to-your-service-application"></a>方法 : サービス アプリケーションにインストーラーを追加する
Visual Studio では、サービス アプリケーションに関連付けられているリソースをインストールするインストール コンポーネントが同梱されています。 インストール コンポーネントにインストールされていると、サービス コントロール マネージャー知らせます、サービスが存在するシステム上の個々 のサービスを登録します。 サービス アプリケーションを操作するときに自動的に適切なインストーラーをプロジェクトに追加する [プロパティ] ウィンドウでリンクを選択することができます。  
  
> [!NOTE]
>  サービスのプロパティの値は、インストーラー クラスに、サービス クラスからコピーされます。 サービス クラスのプロパティの値を更新する場合は自動的に更新されません installer で。  
  
 インストーラーをプロジェクトに新しいクラスに追加するとき (これは、既定では、名前は`ProjectInstaller`) プロジェクト、およびコンポーネントが内に作成した適切なインストールのインスタンスで作成されました。 このクラスは、すべてのインストール コンポーネントの中心点として機能しています。 プロジェクトの必要があります。 など、2 番目のサービスをアプリケーションに追加するインストーラーの追加 をクリックすると、2 番目のインストーラー クラスは作成されません。代わりに、2 番目のサービスのために必要な追加のインストール コンポーネントは、既存のクラスに追加されます。  
  
 サービスを正しくインストールするインストーラー内に特殊なコーディングを行う必要はありません。 ただし、インストール プロセスに特別な機能を追加する必要がある場合、インストーラーの内容を変更する必要がある場合があります。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-add-installers-to-your-service-application"></a>サービス アプリケーションにインストーラーを追加するには  
  
1.  **ソリューション エクスプ ローラー**、アクセス**デザイン**インストール コンポーネントを追加するサービスを表示します。  
  
2.  なく、それ自体の内容は、サービスを選択するデザイナーの背景をクリックします。  
  
3.  デザイナーにフォーカスを右クリックし、クリック**インストーラーの追加**です。  
  
     新しいクラスを`ProjectInstaller`、および 2 つのインストール コンポーネント<xref:System.ServiceProcess.ServiceProcessInstaller>と<xref:System.ServiceProcess.ServiceInstaller>サービスが、コンポーネントにコピーされるは、プロジェクト、およびプロパティの値に追加します。  
  
4.  クリックして、<xref:System.ServiceProcess.ServiceInstaller>コンポーネントことを確認の値、<xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A>プロパティが同じ値に設定、<xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A>サービス自体のプロパティです。  
  
5.  調べるには、サービスの開始方法をクリックして、<xref:System.ServiceProcess.ServiceInstaller>コンポーネントで、設定、<xref:System.ServiceProcess.ServiceInstaller.StartType%2A>プロパティを適切な値にします。  
  
    |[値]|結果|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|サービスは、インストール後に手動で開始する必要があります。 詳細については、次を参照してください。[する方法: サービスを開始](../../../docs/framework/windows-services/how-to-start-services.md)です。|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|サービスは、コンピューターが再起動されるたびに、それ自体で起動されます。|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|サービスを開始することはできません。|  
  
6.  サービスを実行するセキュリティ コンテキストを決定するには、をクリックして、<xref:System.ServiceProcess.ServiceProcessInstaller>コンポーネントし、適切なプロパティの値を設定します。 詳細については、次を参照してください。[する方法: サービスのセキュリティ コンテキストを指定](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)です。  
  
7.  対象のカスタム処理を実行する必要があります。 すべてのメソッドをオーバーライドします。  
  
8.  プロジェクトのサービスごとに手順 1. ~ 7. を実行します。  
  
    > [!NOTE]
    >  プロジェクト内の追加サービスごとに追加する必要があります<xref:System.ServiceProcess.ServiceInstaller>コンポーネントをプロジェクトの`ProjectInstaller`クラスです。 <xref:System.ServiceProcess.ServiceProcessInstaller>手順 3 で追加したコンポーネントがすべて、プロジェクト内の個々 のサービスのインストーラーの動作です。  
  
## <a name="see-also"></a>参照  
 [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [方法 : サービスをインストールおよびアンインストールする](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [方法 : サービスを開始する](../../../docs/framework/windows-services/how-to-start-services.md)  
 [方法 : サービスのセキュリティ コンテキストを指定する](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)

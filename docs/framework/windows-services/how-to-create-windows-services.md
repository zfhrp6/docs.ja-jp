---
title: '方法 : Windows サービスを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
author: ghogen
manager: douge
ms.openlocfilehash: 7719af9393bee816665040d6e4ced191419d0855
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-windows-services"></a>方法 : Windows サービスを作成する
サービスを作成するときに、という名前の Visual Studio プロジェクト テンプレートを使用することができます**Windows サービス**です。 このテンプレートを使用すると、作業の多くを自動化できます。この自動化は、適切なクラスと名前空間を参照し、サービスの基底クラスからの継承を設定し、メソッドのいくつかをオーバーライドすることで実現されます。  
  
> [!WARNING]
>  Windows サービスのプロジェクト テンプレートは、Visual Studio の Express Edition では使用できません。  
  
 実用的なサービスを作成するには、少なくとも以下の作業を行う必要があります。  
  
-   <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> プロパティを設定します。  
  
-   サービス アプリケーションに必要なインストーラーを作成します。  
  
-   <xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドと <xref:System.ServiceProcess.ServiceBase.OnStop%2A> メソッドのオーバーライドとコーディングを行い、サービスの動作をカスタマイズします。  
  
### <a name="to-create-a-windows-service-application"></a>Windows サービス アプリケーションを作成するには  
  
1.  作成、 **Windows サービス**プロジェクト。  
  
    > [!NOTE]
    >  テンプレートを使用せずにサービスを記述する方法については、次を参照してください。[する方法: プログラムによってサービスを書き込む](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)です。  
  
2.  **プロパティ**ウィンドウで、設定、<xref:System.ServiceProcess.ServiceBase.ServiceName%2A>サービスのプロパティです。  
  
     ![ServiceName プロパティを設定します。] (../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")  
  
    > [!NOTE]
    >  <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> プロパティの値は、各インストーラー クラスに記録されている名前と一致する必要があります。 このプロパティを変更した場合は、インストーラー クラスの <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> プロパティも変更する必要があります。  
  
3.  次のいずれかのプロパティを設定して、サービスの動作を決定します。  
  
    |プロパティ|設定|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|サービスが実行停止要求を受け付ける場合は `True` を設定します。サービスの実行を停止しない場合は `false` を設定します。|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|サービスがコンピューターのシャットダウン時に通知を受けて `True` プロシージャを呼び出す場合は、<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> を設定します。|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|サービスが一時停止要求または再開要求を受け付ける場合は `True` を設定します。サービスを一時停止または再開しない場合は `false` を設定します。|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|`True` サービスがコンピューターの電源状態の変更の通知を処理できることを示すために`false`をサービスがしてこれらの変更通知を送信するを防ぐためにします。|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|サービスがアクションを実行したときにアプリケーション イベント ログに情報を入力する場合は `True` を設定します。この機能を無効にする場合は `false` を設定します。 詳細については、次を参照してください。[する方法: サービスに関する情報のログ](../../../docs/framework/windows-services/how-to-log-information-about-services.md)です。 **注:** 既定では、<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>に設定されている`true`です。|  
  
    > [!NOTE]
    >  ときに<xref:System.ServiceProcess.ServiceBase.CanStop%2A>または<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>に設定されている`false`、**サービス コントロール マネージャー**停止、一時停止、またはサービスを続行する、対応するメニュー オプションが無効になります。  
  
4.  コード エディターを起動し、<xref:System.ServiceProcess.ServiceBase.OnStart%2A> プロシージャと <xref:System.ServiceProcess.ServiceBase.OnStop%2A> プロシージャの処理を記述します。  
  
5.  ほかに動作を定義するメソッドがある場合は、それをオーバーライドします。  
  
6.  サービス アプリケーションの必要なインストーラーを追加します。 詳細については、次を参照してください。[する方法: サービス アプリケーションへのインストーラーの追加](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)です。  
  
7.  選択して、プロジェクトをビルド**ソリューションのビルド**から、**ビルド**メニュー。  
  
    > [!NOTE]
    >  F5 キーを押してプロジェクトを実行しないでください。この方法ではサービス プロジェクトを実行できません。  
  
8.  サービスをインストールします。 詳細については、「 [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [方法 : プログラムでサービスを作成する](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)  
 [方法 : サービス アプリケーションにインストーラーを追加する](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [方法 : サービスに関する情報のログを記録する](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [方法 : サービスを開始する](../../../docs/framework/windows-services/how-to-start-services.md)  
 [方法 : サービスのセキュリティ コンテキストを指定する](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)  
 [方法 : サービスをインストールおよびアンインストールする](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [チュートリアル: コンポーネント デザイナーによる Windows サービス アプリケーションの作成](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

---
title: "方法 : Windows サービス アプリケーションをデバッグする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- Windows NT services, debugging
- Windows Service applications, debugging
- services, debugging
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
caps.latest.revision: "16"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 86d90e4129f089a77e51e6e58233a1087fe5d0f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-windows-service-applications"></a>方法 : Windows サービス アプリケーションをデバッグする
サービスは、Visual Studio 内からではなく、サービス コントロール マネージャーのコンテキスト内から実行する必要があります。 そのため、サービスのデバッグは、その他の種類の Visual Studio アプリケーションをデバッグするように単純ではありません。 サービスのデバッグを行うには、サービスを起動してから、サービスを実行しているプロセスにデバッガーをアタッチします。 これにより、Visual Studio のすべての標準デバッグ機能を使用して、アプリケーションをデバッグできるようになります。  
  
> [!CAUTION]
>  プロセスが強制終了される可能性もあるため、アタッチするプロセスの特性や、アタッチによる影響をよく理解している場合に限って、プロセスにデバッガーをアタッチしてください。 たとえば、システムは WinLogon プロセスがないと動作しないため、WinLogon プロセスにデバッガーをアタッチした後でデバッグを中止すると、システムは停止します。  
  
 デバッガーをアタッチできるのは、実行中のサービスだけです。 アタッチのプロセスは、サービスが現在実行している処理に割り込みます。実際にサービスの処理の停止や一時停止を行うのではありません。 つまり、実行中のサービスに対してデバッグを開始すると、デバッグの間、サービスは技術的には起動状態のままですが、処理は中断されます。  
  
 プロセスにデバッガーをアタッチした後で、ブレークポイントを設定し、設定したブレークポイントを使用してコードをデバッグできます。 プロセスへのアタッチに使用するダイアログ ボックスを閉じると、デバッグ モードが有効になります。 サービス コントロール マネージャーを使用して、サービスの開始、停止、一時停止、および再開を行うことができます。これによって、設定したブレークポイントにヒットします。 デバッグが正常に完了したら、このダミー サービスを削除できます。  
  
 この記事ではローカル コンピューターで実行されているサービスのデバッグについて説明しますが、リモート コンピューターで実行されている Windows サービスをデバッグすることもできます。 参照してください[リモート デバッグ](/visualstudio/debugger/debug-installed-app-package)です。  
  
> [!NOTE]
>  サービス コントロール マネージャーではすべてのサービスの開始試行に対して 30 秒の制限が適用されるため、<xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドのデバッグが困難になる場合があります。 詳細については、次を参照してください。[トラブルシューティング: Windows サービスのデバッグ](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md)です。  
  
> [!WARNING]
>  デバッグに有用な情報を取得するためには、Visual Studio デバッガーは、デバッグ対象のバイナリのシンボル ファイルを検索する必要があります。 Visual Studio に組み込まれているサービスをデバッグしている場合は、シンボル ファイル (.pdb ファイル) は実行可能ファイルまたはライブラリと同じフォルダーにあり、デバッガーはそれらを自動的に読み込みます。 構築していないサービスをデバッグしている場合は、最初にサービスのシンボルを検索し、デバッガーでこれらを検出できるようにする必要があります。 参照してください[シンボル (.pdb) を指定して、ソース ファイル](http://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b)です。 システム プロセスをデバッグしているか、サービスにシステム呼び出しのシンボルを含めたい場合は、Microsoft シンボル サーバーを追加する必要があります。 参照してください[デバッグ シンボル](http://msdn.microsoft.com/windows/desktop/ee416588.aspx)です。  
  
### <a name="to-debug-a-service"></a>サービスをデバッグするには  
  
1.  サービスをデバッグ構成で構築します。  
  
2.  サービスをインストールします。 詳細については、「 [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)」を参照してください。  
  
3.  いずれかから、サービスを起動**サービス コントロール マネージャー**、**サーバー エクスプ ローラー**コードとの間です。 詳細については、次を参照してください。[する方法: サービスを開始](../../../docs/framework/windows-services/how-to-start-services.md)です。  
  
4.  システム プロセスにアタッチすることができるように、管理者資格情報を使用して Visual Studio を起動します。  
  
5.  (省略可能)Visual Studio メニュー バーで、**ツール**、**オプション**です。 **オプション** ダイアログ ボックスで、選択**デバッグ**、**シンボル**、select、 **Microsoft シンボル サーバー**チェック ボックスをオンにして、**OK**ボタンをクリックします。  
  
6.  メニュー バーで、次のように選択します。**プロセスにアタッチする**から、**デバッグ**または**ツール**メニュー。 (キーボード: Ctrl + Alt + P)  
  
     **プロセス** ダイアログ ボックスが表示されます。  
  
7.  選択、**プロセスのすべてのユーザーを表示する**チェック ボックスをオンします。  
  
8.  **選択可能なプロセス**セクションで、サービスのプロセスを選択し、**アタッチ**です。  
  
    > [!TIP]
    >  プロセスの名前は、サービスの実行可能ファイルの名前と同じになります。  
  
     **[プロセスにアタッチ]** ダイアログ ボックスが表示されます。  
  
9. 適切なオプションを選択し、**[OK]** ダイアログ ボックスを閉じます。  
  
    > [!NOTE]
    >  デバッグ モードになります。  
  
10. コード内で使用する任意のブレークポイントを設定します。  
  
11. サービス コントロール マネージャーを起動し、停止、一時停止、再開の各コマンドを送信してサービスを操作して、ブレークポイントをヒットします。 詳細については、サービス コントロール マネージャーを実行して、次を参照してください。[する方法: サービスを開始](../../../docs/framework/windows-services/how-to-start-services.md)です。 またを参照してください[トラブルシューティング: Windows サービスのデバッグ](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md)です。  
  
## <a name="debugging-tips-for-windows-services"></a>Windows サービスのデバッグのヒント  
 サービスのプロセスにアタッチすると、そのサービスのコードのほとんど (すべてではない) をデバッグすることができます。 たとえば、サービスが既に開始されているため、そのサービスの <xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッド内のコード、またはサービスをこの方法で読み込むために使用されている `Main` メソッド内のコードは、デバッグすることができません。 この制限に対処する方法の 1 つは、デバッグ専用の一時的な "ダミー" サービスを作成し、サービス アプリケーションに追加することです。 サービスを両方ともインストールし、ダミー サービスを開始してサービス プロセスを読み込むことができます。 使用することができます、一時的なサービスのプロセスが開始されたら、**デバッグ**サービス プロセスにアタッチする Visual Studio のメニュー。  
  
 <xref:System.Threading.Thread.Sleep%2A> メソッドに呼び出しを追加して、プロセスにアタッチできるようになるまで動作を遅延します。  
  
 プログラムを通常のコンソール アプリケーションに変更します。 このためには、起動方法に応じて Windows サービスとコンソール アプリケーションの両方として実行することができるように、`Main` メソッドを次のように書き換えます。  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a>方法: Windows サービスをコンソール アプリケーションとして実行する  
  
1.  <xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドと <xref:System.ServiceProcess.ServiceBase.OnStop%2A> メソッドを実行するサービスにメソッドを追加します。  
  
    ```  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2.  `Main` メソッドを次のように書き換えます。  
  
    ```  
    static void Main(string[] args)  
            {  
                if (Environment.UserInteractive)  
                {  
                    MyNewService service1 = new MyNewService(args);  
                    service1.TestStartupAndStop(args);  
                }  
                else  
                {  
                    // Put the body of your old Main method here.  
                }  
    ```  
  
3.  **アプリケーション**タブ、プロジェクトのプロパティの設定、**出力の種類**に**コンソール アプリケーション**です。  
  
4.  選択**デバッグを開始**(F5) します。  
  
5.  プログラムを再度 Windows サービスとして実行するには、プログラムをインストールして、Windows サービスとして通常どおり起動します。 これらの変更を反対にする必要はありません。  
  
 システムの起動時にのみ発生する問題をデバッグするときなどのいくつかのケースでは、Windows デバッガーを使用する必要があります。 インストール[Debugging Tools for Windows](http://msdn.microsoft.com/windows/hardware/hh852365)して[Windows サービスをデバッグする方法について](http://support.microsoft.com/kb/824344)です。  
  
## <a name="see-also"></a>参照  
 [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [方法 : サービスをインストールおよびアンインストールする](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [方法 : サービスを開始する](../../../docs/framework/windows-services/how-to-start-services.md)  
 [サービスのデバッグ](http://msdn.microsoft.com/library/windows/desktop/ms682546.aspx)

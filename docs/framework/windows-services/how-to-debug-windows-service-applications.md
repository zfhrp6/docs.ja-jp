---
title: "方法 : Windows サービス アプリケーションをデバッグする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "デバッグ [Visual Studio], Windows サービス"
  - "デバッグ (Windows サービス アプリケーションの)"
  - "サービス, デバッグ"
  - "Windows NT サービス, デバッグ"
  - "Windows サービス アプリケーション, デバッグ"
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
caps.latest.revision: 16
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 16
---
# 方法 : Windows サービス アプリケーションをデバッグする
サービスは、Visual Studio 内からではなく、サービス コントロール マネージャーのコンテキスト内から実行する必要があります。  そのため、サービスのデバッグは、その他の種類の Visual Studio アプリケーションをデバッグするように単純ではありません。  サービスのデバッグを行うには、サービスを起動してから、サービスを実行しているプロセスにデバッガーをアタッチします。  これにより、Visual Studio のすべての標準デバッグ機能を使用して、アプリケーションをデバッグできるようになります。  
  
> [!CAUTION]
>  プロセスが強制終了される可能性もあるため、アタッチするプロセスの特性や、アタッチによる影響をよく理解している場合に限って、プロセスにデバッガーをアタッチしてください。  たとえば、システムは WinLogon プロセスがないと動作しないため、WinLogon プロセスにデバッガーをアタッチした後でデバッグを中止すると、システムは停止します。  
  
 デバッガーをアタッチできるのは、実行中のサービスだけです。  アタッチのプロセスは、サービスが現在実行している処理に割り込みます。実際にサービスの処理の停止や一時停止を行うのではありません。  つまり、実行中のサービスに対してデバッグを開始すると、デバッグの間、サービスは技術的には起動状態のままですが、処理は中断されます。  
  
 プロセスにデバッガーをアタッチした後で、ブレークポイントを設定し、設定したブレークポイントを使用してコードをデバッグできます。  プロセスへのアタッチに使用するダイアログ ボックスを閉じると、デバッグ モードが有効になります。  サービス コントロール マネージャーを使用して、サービスの開始、停止、一時停止、および再開を行うことができます。これによって、設定したブレークポイントにヒットします。  デバッグが正常に完了したら、このダミー サービスを削除できます。  
  
 この記事ではローカル コンピューターで実行されているサービスのデバッグについて説明しますが、リモート コンピューターで実行されている Windows サービスをデバッグすることもできます。  「[リモート デバッグ](../Topic/Remote%20Debugging.md)」を参照してください。  
  
> [!NOTE]
>  サービス コントロール マネージャーではすべてのサービスの開始試行に対して 30 秒の制限が適用されるため、<xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドのデバッグが困難になる場合があります。  詳細については、「[Windows サービスをデバッグする場合](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md)」を参照してください。  
  
> [!WARNING]
>  デバッグに有用な情報を取得するためには、Visual Studio デバッガーは、デバッグ対象のバイナリのシンボル ファイルを検索する必要があります。  Visual Studio に組み込まれているサービスをデバッグしている場合は、シンボル ファイル \(.pdb ファイル\) は実行可能ファイルまたはライブラリと同じフォルダーにあり、デバッガーはそれらを自動的に読み込みます。  構築していないサービスをデバッグしている場合は、最初にサービスのシンボルを検索し、デバッガーでこれらを検出できるようにする必要があります。  「[シンボルとソース コードの管理](../Topic/Specify%20Symbol%20\(.pdb\)%20and%20Source%20Files%20in%20the%20Visual%20Studio%20Debugger.md)」を参照してください。  システム プロセスをデバッグしているか、サービスにシステム呼び出しのシンボルを含めたい場合は、Microsoft シンボル サーバーを追加する必要があります。  「[シンボルを使用したデバッグ](http://msdn.microsoft.com/windows/desktop/ee416588.aspx)」を参照してください。  
  
### サービスをデバッグするには  
  
1.  サービスをデバッグ構成で構築します。  
  
2.  サービスをインストールします。  詳細については、「[方法: サービスをインストールおよびアンインストールする](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)」を参照してください。  
  
3.  **サービス コントロール マネージャー**、**サーバー エクスプローラー**、またはコードで、サービスを起動します。  詳細については、「[方法 : サービスを開始する](../../../docs/framework/windows-services/how-to-start-services.md)」を参照してください。  
  
4.  システム プロセスにアタッチすることができるように、管理者資格情報を使用して Visual Studio を起動します。  
  
5.  \(省略可能\) Visual Studio のメニュー バーで **\[ツール\]**、**\[オプション\]** の順に選択します。  **\[オプション\]** ダイアログ ボックスで、**\[デバッグ\]**、**\[シンボル\]** の順に選択し、**\[Microsoft シンボル サーバー\]** チェック ボックスをオンにし、**\[OK\]** を選択します。  
  
6.  メニュー バーの **\[デバッグ\]** または **\[ツール\]** メニューで、**\[プロセスにアタッチ\]** を選択します。  \(キーボード: Ctrl \+ Alt \+ P\)  
  
     **\[プロセス\]** ダイアログ ボックスが表示されます。  
  
7.  **\[Show processes from all users\]** チェック ボックスをオンにします。  
  
8.  **\[選択可能なプロセス\]** セクションでサービスのプロセスを選択し、**\[アタッチ\]** を選択します。  
  
    > [!TIP]
    >  プロセスの名前は、サービスの実行可能ファイルの名前と同じになります。  
  
     **\[プロセスにアタッチ\]** ダイアログ ボックスが表示されます。  
  
9. 適切なオプションを選択し、**\[OK\]** を選択してダイアログ ボックスを閉じます。  
  
    > [!NOTE]
    >  デバッグ モードになります。  
  
10. コード内で使用する任意のブレークポイントを設定します。  
  
11. サービス コントロール マネージャーを起動し、停止、一時停止、再開の各コマンドを送信してサービスを操作して、ブレークポイントをヒットします。  サービス コントロール マネージャーの実行方法の詳細については、「[方法 : サービスを開始する](../../../docs/framework/windows-services/how-to-start-services.md)」を参照してください。  さらに、「[Windows サービスをデバッグする場合](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md)」を参照してください。  
  
## Windows サービスのデバッグのヒント  
 サービスのプロセスにアタッチすると、そのサービスのコードのほとんど \(すべてではない\) をデバッグすることができます。  たとえば、サービスが既に開始されているため、そのサービスの <xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッド内のコード、またはサービスをこの方法で読み込むために使用されている `Main` メソッド内のコードは、デバッグすることができません。  この制限に対処する方法の 1 つは、デバッグ専用の一時的な "ダミー" サービスを作成し、サービス アプリケーションに追加することです。  サービスを両方ともインストールし、ダミー サービスを開始してサービス プロセスを読み込むことができます。  "ダミー" サービスがプロセスを起動した後は、Visual Studio の **\[デバッグ\]** メニューで、サービス プロセスへのアタッチを行うことができます。  
  
 <xref:System.Threading.Thread.Sleep%2A> メソッドに呼び出しを追加して、プロセスにアタッチできるようになるまで動作を遅延します。  
  
 プログラムを通常のコンソール アプリケーションに変更します。  このためには、起動方法に応じて Windows サービスとコンソール アプリケーションの両方として実行することができるように、`Main` メソッドを次のように書き換えます。  
  
#### 方法: Windows サービスをコンソール アプリケーションとして実行する  
  
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
  
3.  プロジェクトのプロパティの **\[アプリケーション\]** タブで、**\[出力の種類\]** を **\[コンソール アプリケーション\]** に設定します。  
  
4.  **\[デバッグの開始\]** を選択します \(F5\)。  
  
5.  プログラムを再度 Windows サービスとして実行するには、プログラムをインストールして、Windows サービスとして通常どおり起動します。  これらの変更を反対にする必要はありません。  
  
 システムの起動時にのみ発生する問題をデバッグするときなどのいくつかのケースでは、Windows デバッガーを使用する必要があります。  [Windows 用のデバッグ ツール](http://msdn.microsoft.com/windows/hardware/hh852365)をインストールし、「[Windows サービスをデバッグする方法](http://support.microsoft.com/kb/824344)」を参照してください。  
  
## 参照  
 [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)   
 [方法: サービスをインストールおよびアンインストールする](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)   
 [方法 : サービスを開始する](../../../docs/framework/windows-services/how-to-start-services.md)   
 [サービスのデバッグ](http://msdn.microsoft.com/library/windows/desktop/ms682546.aspx)
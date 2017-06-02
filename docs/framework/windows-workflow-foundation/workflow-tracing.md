---
title: "ワークフロー トレース | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# ワークフロー トレース
ワークフロー トレースでは、.NET Framework のトレース リスナーを使用して診断情報を取得できます。トレースは、アプリケーションで問題が検出された場合に有効にし、その問題が解決されたら、再度無効にすることが可能です。ワークフローのデバッグ トレースを有効にする方法は 2 つあります。また、イベント トレース ビューアーを使用してトレースを構成したり、<xref:System.Diagnostics> を使用してトレース イベントをファイルに送信したりすることができます。  
  
## ETW でのデバッグ トレースの有効化  
 ETW を使用してトレースを有効化するには、次の手順に従ってイベント ビューアーでデバッグ チャネルを有効化します。  
  
1.  イベント ビューアーで分析ログおよびデバッグ ログのノードに移動します。  
  
2.  イベント ビューアーのツリー ビューで、**\[イベント ビューアー\]**、**\[アプリケーションとサービス ログ\]**、**\[Microsoft\]**、**\[Windows\]** の順に選択して **\[アプリケーション サーバー \- アプリケーション\]** に移動します。**\[アプリケーション サーバー \- アプリケーション\]** を右クリックし、**\[表示\]**、**\[分析およびデバッグ ログの表示\]** の順にクリックします。**\[デバッグ\]** を右クリックし、**\[ログを有効にする\]** を選択します。  
  
3.  ワークフローがデバッグを実行し、トレースが ETW デバッグ チャネルに出力されると、トレースをイベント ビューアーで参照できます。**\[イベント ビューアー\]**、**\[アプリケーションとサービス ログ\]**、**\[Microsoft\]**、**\[Windows\]** の順に選択して **\[アプリケーション サーバー \- アプリケーション\]** に移動します。**\[デバッグ\]** を右クリックし、**\[更新\]** を選択します。  
  
4.  既定の分析トレースのバッファー サイズは 4 KB ですが、このサイズを 32 KB に増やすことをお勧めします。これを行うには、次の手順を実行します。  
  
    1.  現在のフレームワークのディレクトリ \(C:\\Windows\\Microsoft.NET\\Framework\\v4.0.21203 など\) で、次のコマンドを実行します。`wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`  
  
    2.  Windows.ApplicationServer.Applications.man ファイルの \<bufferSize\> の値を 32 に変更します。  
  
        ```  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
  
        ```  
  
    3.  現在のフレームワークのディレクトリ \(C:\\Windows\\Microsoft.NET\\Framework\\v4.0.21203 など\) で、次のコマンドを実行します。`wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`  
  
> [!NOTE]
>  .NET Framework 4 Client Profile を使用している場合は、.NET Framework 4 ディレクトリから次のコマンドを実行することによって、最初に ETW マニフェストを登録する必要があります。`ServiceModelReg.exe –i –c:etw`  
  
## System.Diagnostics を使用したデバッグ トレースの有効化  
 これらのリスナーは、ワークフロー アプリケーションの App.config ファイルまたはワークフロー サービスの Web.config ファイルで構成します。この例では、現在のディレクトリにある MyTraceLog.txt ファイルにトレース情報を保存するように [TextWriterTraceListener](http://go.microsoft.com/fwlink/?LinkId=165424) が構成されています。  
  
```  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="System.Activities" switchValue="Information">  
        <listeners>  
          <add name="textListener" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"  
           type="System.Diagnostics.TextWriterTraceListener"  
           initializeData="MyTraceLog.txt"  
           traceOutputOptions="ProcessId, DateTime" />  
    </sharedListeners>  
    <trace autoflush="true" indentsize="4">  
      <listeners>  
        <add name="textListener" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## 参照  
 [Windows Server App Fabric の監視](http://go.microsoft.com/fwlink/?LinkId=201273)   
 [App Fabric を使用したアプリケーションの監視](http://go.microsoft.com/fwlink/?LinkId=201275)
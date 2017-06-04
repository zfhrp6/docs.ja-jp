---
title: "サービス アプリケーションのプログラミング アーキテクチャ | Microsoft Docs"
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
  - "ServiceBase クラス, サービスの状態"
  - "ServiceController クラス"
  - "ServiceController コンポーネント, プログラミング アーキテクチャ"
  - "ServiceProcessInstaller クラス, サービス アプリケーションのコード モデル"
  - "サービス, プログラミング アーキテクチャ"
  - "サービス, 状態"
  - "Windows サービス アプリケーション, コード モデル"
  - "Windows サービス アプリケーション, 状態"
ms.assetid: 83230026-d068-4174-97ff-e264c896eb2f
caps.latest.revision: 15
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 15
---
# サービス アプリケーションのプログラミング アーキテクチャ
Windows サービス アプリケーションは、<xref:System.ServiceProcess.ServiceBase?displayProperty=fullName> クラスから継承するクラスに基づいています。  このクラスからメソッドをオーバーライドし、機能を定義してサービスの動作を決定します。  
  
 サービスの作成には、主に次のクラスを使用します。  
  
-   <xref:System.ServiceProcess.ServiceBase?displayProperty=fullName> クラス。サービス作成時に <xref:System.ServiceProcess.ServiceBase> クラスのメソッドをオーバーライドし、サービスの機能をこの継承クラスに定義します。  
  
-   <xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=fullName> クラスおよび <xref:System.ServiceProcess.ServiceInstaller?displayProperty=fullName> クラス。サービスのインストールとアンインストールを行うときに使用します。  
  
 また、<xref:System.ServiceProcess.ServiceController> クラスを使用してサービス自体を操作することもできます。  このクラスはサービスの作成には使用しませんが、サービスの起動や停止を行うとき、サービスにコマンドを渡すとき、およびサービス一覧の取得を行うときに使用できます。  
  
## サービスの動作定義  
 サービス制御マネージャーでサービスの状態が変更されたときの動作は、基本クラスの関数によって定義されていますが、サービス クラスでは基本クラスの関数をオーバーライドして使用します。  <xref:System.ServiceProcess.ServiceBase> クラスには次のメソッドがあり、このメソッドをオーバーライドして独自の動作を追加できます。  
  
|メソッド|オーバーライドの目的|  
|----------|----------------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|サービスの実行を開始したときのアクションを示します。  サービス本来の処理は、このプロシージャに記述する必要があります。|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|サービスを一時停止したときの動作を示します。|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|サービスの実行を停止したときの動作を示します。|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|一時停止したサービスを再開したときの動作を示します。|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|実行中のサービスの、システムがシャットダウンする直前の動作を示します。|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|サービスがカスタム コマンドを受信したときの動作を示します。  カスタム コマンドの詳細については、MSDN オンラインを参照してください。|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|低電力モードやサスペンド モードなど、電源管理イベントを受信したときのサービスの応答を示します。|  
  
> [!NOTE]
>  上記のメソッドは、有効期間内に順次に移り変わるサービスの状態を表しています。  たとえば、<xref:System.ServiceProcess.ServiceBase.OnStart%2A> が呼び出されていない状態では、サービスは <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> コマンドに応答できません。  
  
 上記以外にも関連するプロパティおよびメソッドがあります。  以下に例を示します。  
  
-   <xref:System.ServiceProcess.ServiceBase> クラスの <xref:System.ServiceProcess.ServiceBase.Run%2A> メソッド。  サービスのメイン エントリ ポイントです。  Windows サービスのテンプレートを使用してサービスを作成した場合は、アプリケーションの `Main` メソッドにサービスを実行するコードを挿入します。  コード例を次に示します。  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    >  上記の例では、<xref:System.ServiceProcess.ServiceBase> 型の配列を使用しています。アプリケーションに含まれる各サービスをこの配列に追加して、すべてのサービスを同時に実行できます。  ただし、サービスを 1 つだけ作成する場合は、配列を使用せず、<xref:System.ServiceProcess.ServiceBase> から継承する新しいオブジェクトを宣言して実行することもできます。  例については、「[方法 : プログラムでサービスを作成する](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)」を参照してください。  
  
-   <xref:System.ServiceProcess.ServiceBase> クラスの各プロパティ。  サービスに対して呼び出すことができるメソッドを決定します。  たとえば、<xref:System.ServiceProcess.ServiceBase.CanStop%2A> プロパティに `true` が設定されている場合は、サービスの <xref:System.ServiceProcess.ServiceBase.OnStop%2A> メソッドを呼び出すことができます。  <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> プロパティに `true` が設定されている場合は、<xref:System.ServiceProcess.ServiceBase.OnPause%2A> メソッドと <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> メソッドを呼び出すことができます。  これらのいずれかのプロパティに `true` を設定する場合は、該当するメソッドの処理のオーバーライドと定義を行う必要があります。  
  
    > [!NOTE]
    >  サービスが有用であるためには、少なくとも <xref:System.ServiceProcess.ServiceBase.OnStart%2A> と <xref:System.ServiceProcess.ServiceBase.OnStop%2A> をオーバーライドする必要があります。  
  
 <xref:System.ServiceProcess.ServiceController> コンポーネントを使用して、既存のサービスと通信したり、既存のサービスの動作を制御したりできます。  
  
## 参照  
 [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)   
 [方法 : Windows サービスを作成する](../../../docs/framework/windows-services/how-to-create-windows-services.md)
---
title: "方法 : サービス アプリケーションにインストーラーを追加する | Microsoft Docs"
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
  - "インストール コンポーネント, 追加 (サービスに)"
  - "インストーラー, 追加 (サービスに)"
  - "ServiceInstaller クラス, 追加 (インストーラーをサービスに)"
  - "ServiceProcessInstaller クラス, 追加 (インストーラーをサービスに)"
  - "サービス, 追加 (インストーラーを)"
  - "Windows サービス アプリケーション, 追加 (インストーラーを)"
  - "Windows サービス アプリケーション, 配置"
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
caps.latest.revision: 14
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 14
---
# 方法 : サービス アプリケーションにインストーラーを追加する
Visual Studio には、サービス アプリケーションに関連付けられたリソースをインストールできるインストール コンポーネントが組み込まれています。  インストール コンポーネントは、サービスをインストール先システムに登録し、サービス コントロール マネージャーにサービスの存在を知らせます。  サービス アプリケーションを作成するときに、\[プロパティ\] ウィンドウでリンクを選択して、適切なインストーラーをプロジェクトに自動的に追加できます。  
  
> [!NOTE]
>  サービスのプロパティ値は、サービス クラスからインストーラー クラスにコピーされます。  サービス クラスのプロパティ値を更新しても、インストーラーのプロパティ値は更新されません。  
  
 インストーラーをプロジェクトに追加すると、新しいクラス \(既定の名前は `ProjectInstaller`\) がプロジェクトに作成され、そのクラス内にインストール コンポーネントのインスタンスが作成されます。  このクラスは、プロジェクトで必要なすべてのインストール コンポーネントの核になります。  たとえば、2 番目のサービスをアプリケーションに追加し、\[インストーラーの追加\] リンクをクリックしても、2 番目のインストーラー クラスは作成されません。代わりに、2 番目のサービスに必要な追加のインストール コンポーネントが、既存のクラスに追加されます。  
  
 サービスを正しくインストールするために、特別なコードをインストーラーに追加する必要はありません。  ただし、インストール プロセスに特殊な機能を追加する場合は、インストーラーの変更が必要になることもあります。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### サービス アプリケーションにインストーラーを追加するには  
  
1.  **ソリューション エクスプローラー**で、インストール コンポーネントを追加するサービスを**デザイン** ビューに表示します。  
  
2.  デザイナーの背景をクリックして、サービスの内容ではなくサービス自体を選択します。  
  
3.  デザイナーにフォーカスを置いた状態で右クリックし、**\[インストーラーの追加\]** をクリックします。  
  
     新しいクラスの `ProjectInstaller`、および <xref:System.ServiceProcess.ServiceProcessInstaller> と <xref:System.ServiceProcess.ServiceInstaller> の 2 つのインストール コンポーネントが、プロジェクトに追加されます。また、サービスのプロパティ値がこれらのコンポーネントにコピーされます。  
  
4.  \[<xref:System.ServiceProcess.ServiceInstaller>\] コンポーネントをクリックし、<xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> プロパティがサービス自体の <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> プロパティと同じ値に設定されているかどうかを確認します。  
  
5.  サービスの起動方法を決定するには、\[<xref:System.ServiceProcess.ServiceInstaller>\] コンポーネントをクリックし、<xref:System.ServiceProcess.ServiceInstaller.StartType%2A> プロパティに適切な値を設定します。  
  
    |値|結果|  
    |-------|--------|  
    |<xref:System.ServiceProcess.ServiceStartMode>|インストール後に手動でサービスを起動する必要があります。  詳細については、「[方法 : サービスを開始する](../../../docs/framework/windows-services/how-to-start-services.md)」を参照してください。|  
    |<xref:System.ServiceProcess.ServiceStartMode>|コンピューターを再起動すると、サービスが自動的に起動します。|  
    |<xref:System.ServiceProcess.ServiceStartMode>|サービスは起動できません。|  
  
6.  サービスが実行されるセキュリティ コンテキストを決定するには、\[<xref:System.ServiceProcess.ServiceProcessInstaller>\] コンポーネントをクリックし、適切なプロパティ値を設定します。  詳細については、「[方法 : サービスのセキュリティ コンテキストを指定する](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)」を参照してください。  
  
7.  カスタム処理の実行が必要なメソッドをオーバーライドします。  
  
8.  プロジェクトに作成するサービスごとに、手順 1 ～ 7 を実行します。  
  
    > [!NOTE]
    >  プロジェクトに作成するすべてのサービスについて、<xref:System.ServiceProcess.ServiceInstaller> コンポーネントをプロジェクトの `ProjectInstaller` クラスに追加する必要があります。  手順 3 で追加した <xref:System.ServiceProcess.ServiceProcessInstaller> コンポーネントは、プロジェクトのすべてのサービス インストーラーに適用されます。  
  
## 参照  
 [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)   
 [方法: サービスをインストールおよびアンインストールする](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)   
 [方法 : サービスを開始する](../../../docs/framework/windows-services/how-to-start-services.md)   
 [方法 : サービスのセキュリティ コンテキストを指定する](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)
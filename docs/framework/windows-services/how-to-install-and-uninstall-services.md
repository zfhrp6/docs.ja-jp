---
title: "方法: サービスをインストールおよびアンインストールする | Microsoft Docs"
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
  - "インストール, Windows サービス"
  - "インストール (Windows サービスを)"
  - "installutil.exe ツール"
  - "サービス, インストール"
  - "サービス, アンインストール"
  - "アンインストール (アプリケーションを), Windows サービス"
  - "アンインストール (Windows サービスを)"
  - "Windows サービス アプリケーション, 配置"
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
caps.latest.revision: 19
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 17
---
# 方法: サービスをインストールおよびアンインストールする
.NET Framework を使用して Windows サービスを開発している場合は、InstallUtil.exe というコマンド ライン ユーティリティを使用してサービス アプリケーションをすばやくインストールできます。  開発者は、ユーザーがインストールおよびアンインストールできる Windows サービスをリリースする場合、InstallShield を使用する必要があります。  「[Windows インストーラーの配置](http://msdn.microsoft.com/ja-jp/121be21b-b916-43e2-8f10-8b080516d2a0)」を参照してください。  
  
> [!WARNING]
>  サービスをコンピューターからアンインストールする場合は、この記事の手順には従わないでください。  代わりに、サービスをインストールしたプログラムまたはソフトウェア パッケージを確認し、\[コントロール パネル\] の **\[プログラムの追加と削除\]** を選択してそのプログラムをアンインストールします。  多くのサービスが Windows の不可欠な構成要素であることに注意してください。それらを削除すると、システムが不安定になることがあります。  
  
 この記事の手順を使用するためには、まず、Windows サービスにサービス インストーラーを追加する必要があります。  「[チュートリアル: コンポーネント デザイナーによる Windows サービス アプリケーションの作成](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)」を参照してください。  
  
 Windows サービス プロジェクトは、F5 キーを押して Visual Studio 開発環境から直接実行することができません。  これは、プロジェクトを実行する前に、プロジェクトのサービスをインストールする必要があるためです。  
  
> [!TIP]
>  **サーバー エクスプローラー**を起動して、サービスがインストールまたはアンインストールされているかどうかを確認できます。  詳細については、「[方法 : サーバー エクスプローラー\/データベース エクスプローラーにアクセスして初期化する](../Topic/How%20to:%20Access%20and%20Initialize%20Server%20Explorer-Database%20Explorer.md)」を参照してください。  
  
### サービスを手動でインストールするには  
  
1.  Windows の **\[スタート\]** メニューまたは **\[スタート\]** 画面で、**\[Visual Studio\]**、**\[Visual Studio ツール\]**、**\[開発者コマンド プロンプト\]** の順に選択します。  
  
     Visual Studio コマンド プロンプトが表示されます。  
  
2.  プロジェクトのコンパイル済み実行可能ファイルが格納されているディレクトリに移動します。  
  
3.  プロジェクトの実行可能ファイルをパラメーターとして指定し、コマンド プロンプトから InstallUtil.exe を実行します。  
  
    ```  
    installutil <yourproject>.exe  
    ```  
  
     Visual Studio コマンド プロンプトを使用している場合は、InstallUtil.exe がシステム パス上にある必要があります。  該当しない場合は、パスに追加するか、完全修飾パスを使用して起動します。  このツールは .NET Framework と共にインストールされ、パスは `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>` です。  たとえば、32 ビット版の .NET Framework 4 または 4.5\* では、Windows のインストール ディレクトリが C:\\Windows である場合、パスは `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe` になります。  64 ビット版の .NET Framework 4 または 4.5\* では、既定のパスは `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe` になります。  
  
### サービスを手動でアンインストールするには  
  
1.  Windows の **\[スタート\]** メニューまたは **\[スタート\]** 画面で、**\[Visual Studio\]**、**\[Visual Studio ツール\]**、**\[開発者コマンド プロンプト\]** の順に選択します。  
  
     Visual Studio コマンド プロンプトが表示されます。  
  
2.  プロジェクトの出力先ファイルをパラメーターとして指定し、コマンド プロンプトから InstallUtil.exe を実行します。  
  
    ```  
    installutil /u <yourproject>.exe  
    ```  
  
3.  場合によっては、サービスの実行可能ファイルを削除した後も、レジストリ内にサービスが存在したままになることがあります。  このような場合は、コマンド [sc delete](http://technet.microsoft.com/library/cc742045.aspx) を使用して、レジストリからサービスのエントリを削除します。  
  
## 参照  
 [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)   
 [方法 : Windows サービスを作成する](../../../docs/framework/windows-services/how-to-create-windows-services.md)   
 [方法 : サービス アプリケーションにインストーラーを追加する](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)   
 [Installutil.exe \(インストーラー ツール\)](../../../docs/framework/tools/installutil-exe-installer-tool.md)
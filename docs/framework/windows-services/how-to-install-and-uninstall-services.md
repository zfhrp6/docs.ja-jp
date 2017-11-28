---
title: "方法: サービスをインストールおよびアンインストールする"
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
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, Windows Services
- installation, Windows Services
- uninstalling Windows Services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
caps.latest.revision: "19"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: d52512ef98596e1e3d5f0acb3b1bbc0eebffe867
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-install-and-uninstall-services"></a>方法: サービスをインストールおよびアンインストールする
.NET Framework を使用して Windows サービスを開発している場合は、InstallUtil.exe というコマンド ライン ユーティリティを使用してサービス アプリケーションをすばやくインストールできます。 開発者は、ユーザーがインストールおよびアンインストールできる Windows サービスをリリースする場合、InstallShield を使用する必要があります。 参照してください[Windows インストーラーの配置](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)です。  
  
> [!WARNING]
>  サービスをコンピューターからアンインストールする場合は、この記事の手順には従わないでください。 代わりに、サービスをインストールしたプログラムまたはソフトウェア パッケージを検索し、**プログラムの追加/削除**そのプログラムをアンインストールするコントロール パネルの します。 多くのサービスが Windows の不可欠な構成要素であることに注意してください。それらを削除すると、システムが不安定になることがあります。  
  
 この記事の手順を使用するためには、まず、Windows サービスにサービス インストーラーを追加する必要があります。 参照してください[チュートリアル: Windows を作成するサービス アプリケーション コンポーネント デザイナーを](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)です。  
  
 Windows サービス プロジェクトは、F5 キーを押して Visual Studio 開発環境から直接実行することができません。 これは、プロジェクトを実行する前に、プロジェクトのサービスをインストールする必要があるためです。  
  
> [!TIP]
>  起動する**サーバー エクスプ ローラー**サービスがインストールまたはアンインストールされたことを確認してください。 詳細については、次を参照してください。 方法: アクセスおよびサーバー エクスプ ローラー データベース エクスプ ローラーを初期化します。  
  
### <a name="to-install-your-service-manually"></a>サービスを手動でインストールするには  
  
1.  Windows の**開始**メニューまたは**開始**画面で、選択**Visual Studio** 、 **Visual Studio Tools**、**開発者コマンド プロンプト**です。  
  
     Visual Studio コマンド プロンプトが表示されます。  
  
2.  プロジェクトのコンパイル済み実行可能ファイルが格納されているディレクトリに移動します。  
  
3.  プロジェクトの実行可能ファイルをパラメーターとして指定し、コマンド プロンプトから InstallUtil.exe を実行します。  
  
    ```  
    installutil <yourproject>.exe  
    ```  
  
     Visual Studio コマンド プロンプトを使用している場合は、InstallUtil.exe がシステム パス上にある必要があります。 該当しない場合は、パスに追加するか、完全修飾パスを使用して起動します。 このツールは .NET Framework と共にインストールされ、パスは `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>` です。 たとえば、32 ビット版の .NET Framework 4 または 4.5* では、Windows のインストール ディレクトリが C:\Windows である場合、パスは `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe` になります。 64 ビット バージョンの .NET Framework 4 または 4.5。\*、既定のパスは`C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`します。  
  
### <a name="to-uninstall-your-service-manually"></a>サービスを手動でアンインストールするには  
  
1.  Windows の**開始**メニューまたは**開始**画面で、選択**Visual Studio**、 **Visual Studio Tools**、**開発者コマンド プロンプト**です。  
  
     Visual Studio コマンド プロンプトが表示されます。  
  
2.  プロジェクトの出力先ファイルをパラメーターとして指定し、コマンド プロンプトから InstallUtil.exe を実行します。  
  
    ```  
    installutil /u <yourproject>.exe  
    ```  
  
3.  場合によっては、サービスの実行可能ファイルを削除した後も、レジストリ内にサービスが存在したままになることがあります。 その場合は、コマンドを使用して[sc delete](http://technet.microsoft.com/library/cc742045.aspx)をレジストリからサービスのエントリを削除します。  
  
## <a name="see-also"></a>関連項目  
 [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [方法: Windows サービスの作成](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [方法: サービス アプリケーションへのインストーラーの追加](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Installutil.exe (インストーラー ツール)](../../../docs/framework/tools/installutil-exe-installer-tool.md)

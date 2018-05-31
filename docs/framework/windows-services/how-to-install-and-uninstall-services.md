---
title: '方法: サービスをインストールおよびアンインストールする'
ms.date: 03/30/2017
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
author: ghogen
manager: douge
ms.openlocfilehash: 0d42a37b2e84c310569666771ded38e5feca3608
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513140"
---
# <a name="how-to-install-and-uninstall-services"></a>方法: サービスをインストールおよびアンインストールする
.NET Framework を使用して Windows サービスを開発している場合は、InstallUtil.exe というコマンド ライン ユーティリティを使用してサービス アプリケーションをすばやくインストールできます。 開発者は、ユーザーがインストールおよびアンインストールできる Windows サービスをリリースする場合、InstallShield を使用する必要があります。 「[Windows インストーラー配置](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)」をご覧ください。  
  
> [!WARNING]
>  サービスをコンピューターからアンインストールする場合は、この記事の手順には従わないでください。 代わりに、サービスをインストールしたプログラムまたはソフトウェア パッケージを確認し、[コントロール パネル] の **[プログラムの追加と削除]** を選択してそのプログラムをアンインストールします。 多くのサービスが Windows の不可欠な構成要素であることに注意してください。それらを削除すると、システムが不安定になることがあります。  
  
 この記事の手順を使用するためには、まず、Windows サービスにサービス インストーラーを追加する必要があります。 「[チュートリアル: コンポーネント デザイナーによる Windows サービス アプリケーションの作成](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)」をご覧ください。  
  
 Windows サービス プロジェクトは、F5 キーを押して Visual Studio 開発環境から直接実行することができません。 これは、プロジェクトを実行する前に、プロジェクトのサービスをインストールする必要があるためです。  
  
> [!TIP]
>  **サーバー エクスプローラー**を起動して、サービスがインストールまたはアンインストールされているかどうかを確認できます。 詳しくは、「方法: サーバー エクスプローラー/データベース エクスプローラーにアクセスして初期化する」をご覧ください。  
  
### <a name="to-install-your-service-manually"></a>サービスを手動でインストールするには  
  
1.  Windows の **[スタート]** メニューまたは **[スタート]** 画面で、**[Visual Studio]**、**[Visual Studio Tools]**、**[開発者コマンド プロンプト]** の順に選択します。  
  
     Visual Studio コマンド プロンプトが表示されます。  
  
2.  プロジェクトのコンパイル済み実行可能ファイルが格納されているディレクトリに移動します。  
  
3.  プロジェクトの実行可能ファイルをパラメーターとして指定し、コマンド プロンプトから InstallUtil.exe を実行します。  
  
    ```  
    installutil <yourproject>.exe  
    ```  
  
     Visual Studio コマンド プロンプトを使用している場合は、InstallUtil.exe がシステム パス上にある必要があります。 該当しない場合は、パスに追加するか、完全修飾パスを使用して起動します。 このツールは .NET Framework と共にインストールされ、パスは `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>` です。 たとえば、32 ビット版の .NET Framework 4 または 4.5* では、Windows のインストール ディレクトリが C:\Windows である場合、パスは `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe` になります。 64 ビット版の .NET Framework 4 または 4.5.\* では、既定のパスは `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe` になります。  
  
### <a name="to-uninstall-your-service-manually"></a>サービスを手動でアンインストールするには  
  
1.  Windows の **[スタート]** メニューまたは **[スタート]** 画面で、**[Visual Studio]**、**[Visual Studio Tools]**、**[開発者コマンド プロンプト]** の順に選択します。  
  
     Visual Studio コマンド プロンプトが表示されます。  
  
2.  プロジェクトの出力先ファイルをパラメーターとして指定し、コマンド プロンプトから InstallUtil.exe を実行します。  
  
    ```  
    installutil /u <yourproject>.exe  
    ```  
  
3.  場合によっては、サービスの実行可能ファイルを削除した後も、レジストリ内にサービスが存在したままになることがあります。 このような場合は、コマンド [sc delete](http://technet.microsoft.com/library/cc742045.aspx) を使って、レジストリからサービスのエントリを削除します。  
  
## <a name="see-also"></a>参照  
 [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [方法 : Windows サービスを作成する](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [方法 : サービス アプリケーションにインストーラーを追加する](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Installutil.exe (インストーラー ツール)](../../../docs/framework/tools/installutil-exe-installer-tool.md)

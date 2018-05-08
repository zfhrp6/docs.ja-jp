---
title: '方法 : Visual Studio を構成して Web サービスを呼び出す XAML ブラウザー アプリケーションをデバッグする'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
ms.openlocfilehash: 948a730185650cb3449202503a049e9caff7c4bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>方法 : Visual Studio を構成して Web サービスを呼び出す XAML ブラウザー アプリケーションをデバッグする
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] インターネット ゾーン アクセス許可セットに制限されている部分的に信頼されたセキュリティ サンド ボックス内で実行します。 このアクセス許可セットは、Web で配置されているサービスのみを Web サービス呼び出しを制限、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]元のアプリケーションのサイトです。 ときに、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]からデバッグ[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)]も、Web サービスに参照としては、元の同じサイトがないと見なされます。 この原因セキュリティ例外を発生させると、 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Web サービスを呼び出すしようとしています。 ただし、 [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)]プロジェクトは、デバッグ中に呼び出し、Web サービスと同じサイトに元のシミュレートするように構成できます。 これにより、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]を安全にセキュリティ例外を発生させることがなく、Web サービスを呼び出します。  
  
## <a name="configuring-visual-studio"></a>Visual Studio の構成  
 構成する[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)]をデバッグする、 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Web サービスを呼び出します。  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **プロジェクト デザイナー**をクリックして、**デバッグ**タブです。  
  
3.  **開始動作**セクションで、**外部プログラムの開始**」と入力します。  
  
     `C:\WINDOWS\System32\PresentationHost.exe`  
  
4.  **開始オプション**セクションで、次の点を入力してください、**コマンドライン引数**テキスト ボックス。  
  
     `-debug`  *ファイル名*  
  
     *ファイル名*値を **-デバッグ**パラメーターは、.xbap ファイル名。 例。  
  
     `-debug c:\example.xbap`  
  
> [!NOTE]
>  これは、既定の構成で作成したソリューションは、 [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)]プロジェクト テンプレート。  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **プロジェクト デザイナー**をクリックして、**デバッグ**タブです。  
  
3.  **開始オプション**セクションで、次のコマンド ライン パラメーターを追加、**コマンドライン引数**テキスト ボックス。  
  
     `-debugSecurityZoneURL`  *URL*  
  
     *URL*値を **- debugSecurityZoneURL**パラメーターは、[!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)]として、アプリケーションの元のサイトをシミュレートする場所です。  
  
 たとえば、次のように検討します、[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]に次の Web サービスを使用する[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:。  
  
 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`  
  
 元のサイト[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]この Web サービスは。  
  
 `http://services.msdn.microsoft.com`  
  
 その結果、完全な **- debugSecurityZoneURL**コマンド ライン パラメーターと値は。  
  
 `-debugSecurityZoneURL http://services.msdn.microsoft.com`  
  
## <a name="see-also"></a>関連項目  
 [WPF ホスト (PresentationHost.exe)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)
